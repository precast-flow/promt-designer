# Manual Piece & Template Studio-okan

**Modül kodu:** `MPTS-okan`  
**Kapsam:** Mühendislik altında manuel parça özellikleri, malzeme kataloğu, assembly, piece mark şablonları ve üretim parçası düzenleme — yalnızca **frontend bilgi mimarisi, ekran kurgusu ve prompt-designer çıktısı** (kod, API, backend yok).

---

## 1. Önerilen modül adı

**Manual Piece & Template Studio-okan** (kısa: **Parça & Şablon Stüdyosu-okan**)

**Neden:** “Studio”, hem şablon yazımını (authoring) hem üretim parçası örneğini (instance) kapsayan kurumsal bir çağrışım sunar; “Manual Piece” ürün cümlesindeki odağı (manuel parça tanımı) doğrudan taşır; **-okan** soneki bu çalışmanın sahibini ve sürümünü ayırt eder. Alternatiflerden *Piece Authoring Studio* çok genel kalır; *Engineering Piece Definition* yalnızca tanımı vurgular, template→instance zincirini zayıf bırakır.

---

## 2. Modül özeti

**Bu modül ne yapar?**

- **Master data:** Material Items ve Material Assemblies kataloglarını listeler, ekler/düzenler/siler (mock).
- **Şablon:** Piece Mark Templates ile parça işaret şablonunun başlık bilgisini, malzeme satırlarını, assembly satırlarını ve maliyet kırılımını tek şablonda toplar.
- **Örnek üretimi:** Şablondan işe (job) bağlı üretim parçası oluşturur (Add from Template modal).
- **Örnek düzenleme:** Üretim parçası için Piece Mark bilgisi, standart malzeme (ve isteğe bağlı job-specific) sekmelerini sunar; şablondan gelen ile sahada değişen alanları ayırt etmeye uygun UI önerir.

**Ne yapmaz?**

- Backend, kalıcı veri, kimlik doğrulama, gerçek maliyet motoru, CAD/BIM içe aktarım, MES/ERP API çağrıları, rapor PDF üretimi (sadece aksiyon yerleşimi ve mock).

**Sınırlar:** Tüm hesaplar ve “Calc” alanları **görüntüleme ve etkileşim mock’u**; iş kuralları yazılmaz, sadece hangi alanın ne zaman dolu/boş/hataya düşeceği tarif edilir.

---

## 3. Kullanıcı akışı (master → template → instance)

1. Kullanıcı **Material Items** ve **Material Assemblies** ile sözlüğü doldurur (veya mevcut mock ile çalışır).
2. **Piece Mark Template** oluşturur: önce Header/Piece Mark Information, sonra Material Items / Material Assemblies / Costs sekmeleri.
3. **Production Pieces** altında iş seçer; **Add From Template** ile şablondan parça üretir.
4. **Edit Production Piece** ile instance düzeltir: Piece Mark Information + Standard Material (Items / Assemblies alt sekmeleri); gerekirse Job Specific Material.

Bu zincir ekranda **breadcrumb + modül içi sol nav** ile sürekli görünür tutulur.

---

## 4. Bilgi mimarisi (IA)

**Öneri:** Tek üst modül **Engineering**, altında üç ana bölüm; yoğun master data için **Catalog** altında iki liste birleşik giriş noktası.

```
Engineering
└── Manual Piece & Template Studio-okan
    ├── Catalog
    │   ├── Material Items          (liste → add/edit)
    │   └── Material Assemblies     (liste → add/edit)
    ├── Templates
    │   └── Piece Mark Templates    (liste → template detay [sekmeli])
    └── Production Pieces
        ├── Piece Marks (liste)     (job bağlamında)
        └── Edit Production Piece   (detay [sekmeli])
```

- **Breadcrumb örneği:** `Engineering / Manual Piece & Template Studio-okan / Templates / PM-TPL-001 / Material Items`
- **Üst sekme yoksa:** Sol tarafta dar ikonlu nav (Catalog | Templates | Production Pieces); mobilde üst dropdown’a çökertilir.
- **Template detay ve Production piece detay:** İçeride **yatay sekme**: Header | Material Items | Material Assemblies | Costs (template); Piece Mark Information | Standard Material | (opsiyonel) Job Specific Material (production).

**Alternatif kararların özeti**

| # | Karar | Sonuç | Gerekçe |
|---|--------|--------|---------|
| 1 | Items vs Assemblies ayrı mı, tek katalog mu? | **Tek “Catalog” altında iki alt sayfa** | Aynı kullanıcı görevi (master tanım); menü şişmesin; ortak filtre dilini paylaşır. |
| 2 | Templates ayrı bölüm mü, step wizard mı? | **Ayrı “Templates” bölümü**; içeride sekmeli detay | Paralel düzenleme (malzeme + maliyet) wizard’a sığmaz; stepper sadece “yeni şablon sihirbazı” opsiyonel P1’de kalabilir. |
| 3 | Production editing template’ten ne kadar ayrı? | **Görsel tema: template = nötr/mavi çizim ikonu, instance = turuncu/amber “Job” şeridi** | Aynı alan düzeni korunur ama bağlam karışmaz. |
| 4 | Template içi Items/Assemblies/Costs | **Klasik sekme + üstte sticky özet şeridi** | Step navigator uzun formlarda kaybolur; sekmeler ERP alışkanlığına uygun. |
| 5 | Tablo vs kart | **Yoğun grid + üstte özet kart şeridi + boş durumda kart** | Endüstriyel veri yoğunluğu + modern özet alanı. |

---

## 5. Kullanıcı rolleri

| Rol | Kullanım |
|-----|----------|
| Precast design engineer | Şablon başlığı, ölçüler, brace, Add Work |
| Technical office specialist | Material/assemblies grid, maliyet satırları |
| Engineering clerk / design entry operator | Master item girişi, liste düzenleme |
| Production preparation engineer | Production piece, qty, BOM copy, saha öncesi düzeltme |
| Plant-specific engineering admin | Location/plant filtreleri, aktif/pasif, şablon çoğaltma |

---

## 6. UI prensipleri

- **Gri / beyaz / mavi aksan**; durum için amber (job), yeşil (aktif), kırmızı (hata) — mor yok (mevcut MVP diline uyum).
- **Sticky üst aksiyon çubuğu:** Save, Save & Close, Close birlikte; primary solda veya sağda tutarlı.
- **Dense mode:** Tablolarda satır yüksekliği compact; font tablo için `text-sm`.
- **Breadcrumb + sayfa başlığı** her listede; detayda şablon/parça kodu başlıkta.
- **Tab persistence:** URL query `?tab=material-items` (prompt seviyesinde öneri; implementasyon mock).
- **Özet şeridi:** Template ve production detayında üstte 1 satırlık özet (Description, Location/Job, Rev).

---

## 7. Sayfa bazlı ekran tasarımları (ekran başına şablon)

Her ekranda ortak olarak şunlar düşünülür (varsa ilgili satıra işlenir): **sağ özet paneli** (liste ekranlarında seçili satır özeti veya filtre özeti), **validation** (inline + özet), **helper text**, **boş / başarı / hata** durumları.

---

### A. Material Items — Liste

| Başlık | İçerik |
|--------|--------|
| Amaç | Tekil malzeme master satırlarını aramak, düzenlemek, silmek. |
| Senaryo | “Rebar” kategorisinde #4 Epoxy satırını bulup düzenleme. |
| Üst aksiyonlar | Report, Export, **Add New**, Close (shell). |
| Filtreler | Category (multi), Bend Type (multi), Active (All/Yes/No), Prod/CIP/Erect (üçlü toggle), global search (Material Num, Description, Embed Label). |
| Tablo kolonları | Category, Material Num, Embed Label, Description, GL Code, Bend Type, Material Cost, Dim Length, Order By, Active (pill), Prod, CIP, Erect. |
| Satır aksiyonları | Edit, Delete (onay modalı: “Bu kalem N assembly’de kullanılıyor olabilir”). |
| Sağ panel (opsiyonel) | Son seçilen satırın kısa özeti + “Son düzenleyen” mock. |
| Validation | — (liste). |
| Boş durum | İllüstrasyon + “Henüz material item yok” + Add New + Import CSV (disabled). |
| Başarı | Toast: “Kayıt silindi” / “Dışa aktarma kuyruğa alındı” (mock). |
| Hata | Kırmızı banner + “Silme başarısız — bağımlılık var” (mock). |
| Yoğun veri UX | Sticky header, yatay scroll, column chooser, ilk 2 kolon freeze. |
| Mock veri | Kategoriler: Rebar, Strand, Insert, Lifting Loop, Miscellaneous Items. Örnek satır: `Rebar \| M-440C \| EMB-01 \| #4 Epoxy \| 5.2001 \| Std \| 1.25 \| 20 \| 10 \| ✓ \| ✓ \| ✓ \| ✓` |

---

### B. Material Item — Add/Edit

**Amaç:** Tek master kayıt; tüm alanlar aşağıda eksiksiz listelenir.

**Alanlar (tam liste):**

| Alan | Not |
|------|-----|
| Category* | Select |
| Material ID / Material Num* | Text |
| Embed Label | Text |
| Description* | Textarea kısa |
| Bend Type | Select |
| Material Cost | Decimal |
| Mat. Weight | Decimal |
| GL Code | Text |
| BOM Unit | Select |
| Purchase Unit | Select |
| Unit Conversion | Decimal |
| Material Waste | % |
| Order By | Integer |
| Dim Length | Decimal |
| File upload | Mock dosya adı + sil |
| Custom Field 1 … Custom Field 10 | Text (accordion “Advanced custom fields”) |
| Advance Order | Checkbox |
| Active | Checkbox |
| Production | Checkbox |
| CIP | Checkbox |
| Erection | Checkbox |

**Zorunlu:** Category, Material Num, Description (P0); GL Code opsiyonel P0, zorunlu P1 (ürün kararı).

**Boole:** Checkbox (ERP alışkanlığı); toggle sadece “Active” için opsiyonel alternatif.

**Numeric gruplama:** Satır1: Material Cost + Mat. Weight; Satır2: Dim Length + Unit Conversion; Satır3: Material Waste + Order By.

**Üst aksiyonlar:** Save, Save & Close, Close, **Update linked assemblies** (secondary — modal onayı).

**Sağ panel:** “Kullanıldığı yerler” mock listesi (0 assembly).

**Validation:** Required alan boş → kırmızı border; sayısal alanlarda format; file upload max boyut (mesaj only).

**Helper:** BOM Unit vs Purchase Unit — info tooltip; Custom Field’lar için “Plant extension” notu.

**Boş:** Yeni kayıtta form defaults (Active=on).

**Başarı:** “Kayıt kaydedildi” + yeşil banner; Save & Close → listeye dön.

**Hata:** “Duplicate Material Num” inline.

---

### C. Material Assemblies — Liste

**Amaç:** Assembly master listesi.

**Görsel:** Satır başı **ASM** badge + stack ikonu (Material Items’tan ayırt).

**Kolonlar / filtre / aksiyonlar:** A ile aynı mantık.

**Satır aksiyonları:** Edit, **Open sub assembly details / contents** (drawer: alt kalemler tablosu özet), Delete.

**Sağ panel:** Seçili assembly için toplam qty ve kalem sayısı mock.

**Boş / başarı / hata:** A ile paralel.

**UX:** “3 items” linki → drawer; hızlı drill-down.

---

### D. Material Assembly — Add/Edit

**Üst form (tam liste):** Category, Embed Label, Bend Type, GL Code, BOM Unit, Purchase Unit, Order By, File, Material Num, Description, Material Cost, **Calc** (readonly), Mat. Weight, **Calc** (readonly), Material Waste, Unit Conversion, Advance Order, Active, Production, CIP, Erection.

**Sub Assembly Items grid:**

| Kolon | Not |
|-------|-----|
| (sil) | Çöp ikonu |
| Category | Select → Item listesini daraltır |
| Item | Material Num lookup |
| Order By | Int |
| Qty | Decimal |
| Dim Length | Decimal |
| Bend Type | Select |
| Dim A … Dim F (P0) | P1’de Dim G–Z veya “Wide dims” yan panel |

**Davranış:** Satır ekle; **expand** satırında fazla dim için alt satır veya yan split editor (P1).

**Karar:** Varsayılan **tablo**; accordion satır bazında sadece çok fazla dim varsa.

**Aksiyonlar:** Save, Save & Close, Close.

**Validation:** En az bir alt satır önerilir (uyarı, hard error değil); duplicate item uyarısı.

**Sağ panel:** Assembly toplam ağırlık / maliyet mock (Calc alanlarıyla uyumlu).

---

### E. Piece Mark Templates — Liste

**Filtre / kolon / aksiyon:** Talep edilen set (Location, Piece Mark, Description, Product Category, Product Code, Cross Section, Active).

**Üst aksiyonlar:** Add Template, Export, Report.

**Plant/location:** Filtrede çoklu plant; liste kolonunda Location görünür.

**Yeni şablon:** Add Template → boş template detayına gider veya mini modal “Piece Mark + Location” (ürün kararı).

**Boş / başarı / hata:** A ile paralel.

**Sağ panel:** Seçili şablon özeti + “Son revizyon” mock.

---

### F. Piece Mark Template — Header / Piece Mark Information

**Sticky summary strip:** Description (kısaltılmış), Piece Mark, Location, Active pill, Rev (küçük).

**Form alanları (tam):** Description, Piece Mark*, Active, File, Location*, Product Category, Product Code, Cross Section, Note, Rev, Rev Text, Rev Date, Return Legs, Length / Width / Depth (ft-in-fraction veya birim seçicili), Weight, Struct CY, Arch CY, Total CY (readonly), Release Str, Struct SF, Arch SF, Total SF (readonly), 28 Day Release, Brace Type, Brace Qty, Add Work 1..6 (checkbox).

**Ölçü UX:** Üç küçük input (ft | in | frac) hizalı; placeholder “0’-0\"-0/0”.

**Readonly:** CY/SF toplamları — gri kutu + “Hesaplanan” etiketi.

**Hiyerarşi:** Kart1 Kimlik+Rev; Kart2 Boyutlar + Weight; Kart3 Hacim/Yüzey (readonly); Kart4 Brace + Add Work.

**Sekme:** Bu içerik **Header / Piece Mark Information** sekmesinin tamamıdır.

**Validation:** Piece Mark + Location zorunlu; ölçüler pozitif sayı.

**Sağ panel:** “Şablon özeti” — Toplam ağırlık mock, sekme sayısı (3 satır grid dolu mu).

**Boş yeni şablon:** Placeholder metinler.

**Başarı:** “Şablon kaydedildi”.

---

### G. Piece Mark Template — Material Items sekmesi

**Üst özet şeridi:** Description + Location (readonly).

**Grid kolonları:** Category, Material Num, Embed Label, Description, Qty, Cost, Total, Weight, Unit, Bend Type, Dim Length.

**Etkileşim:** Category → Material Num daraltma; Description lookup veya otomatik doldurma; yeni satır **sarı sol border**; silinen satır üstü çizili önizleme (undo mock).

**Alt footer:** **Toplam Cost**, **Toplam Weight**, satır sayısı.

**Sağ panel:** Bu sekmede “Malzeme özeti” mini kartı.

**Validation:** Negatif qty uyarısı; Qty boş satırda kayıt engeli.

---

### H. Piece Mark Template — Material Assemblies sekmesi

**Üst özet:** G ile aynı.

**Grid:** G ile aynı kolonlar + satır tipi **ASM** ikonu; satır rengi hafif farklı (açık lavanta veya nötr gri).

**Drill-down:** İçerik ikonu → popover’da alt BOM listesi (category, item, qty).

**Alt özet:** Toplam Cost + Total Weight + “Assembly satırı: N”.

**Risk:** Kullanıcı item ile assembly satırını karıştırmasın diye kolon başlığında “Type” veya ikon zorunlu.

---

### I. Piece Mark Template — Costs sekmesi

**Kolonlar:** Cost (satır adı), Section, Qty, Unit, Cost, Calc, O.H., Profit, Margin, Use Tax, Sales Tax.

**Örnek satırlar:** Concrete CY, Material Items (rollup), Material Assemblies (rollup), Labor, Overhead, SGA, Margin.

**Özellikler:** Section group header; satır ekle/sil; checkbox kolonları için geniş başlık + kısaltma.

**Footer:** Grand total, toplam margin %, mock.

**Hesap türü:** Cost satırı dropdown’da “Manual / Rollup / Formula” (mock).

**Sağ panel:** “Margin health” göstergesi (mock gauge).

**Validation:** Negatif margin uyarısı (sarı).

---

### J. View/Edit Production Piece Marks — Liste

**Job seçimi:** Üstte zorunlu global job dropdown (mock JOB-####).

**Filtreler:** Phase, Plant, Product Category, Drawing Status, Piece Mark search.

**Grid kolonları:** Piece Mark, Phase, Plant, Product Category, Product Code, Cross Section, Qty, Drawing Status, AW1..AW6 (veya dar ekranda “+AW” expand), ek üretim kolonları (kısaltılmış).

**Üst aksiyonlar:** Report, Export, Add Piece (boş instance), **Add From Template**, Close.

**Boş:** “Bu iş için henüz piece mark yok” + Add From Template (primary) + ikincil Add Piece.

**Sağ panel:** Job özeti (termin, müşteri mock).

**Başarı / hata:** Export toast; job seçilmeden liste gri overlay “Önce iş seçin”.

---

### K. Add New Piece from Template — Modal

**Alanlar:** Job (readonly iş bağlamı), Phase*, Plant*, Product*, Template* (searchable combobox), Piece Mark (auto veya override), Qty*.

**Bağımlılık sırası:** Phase → Plant → Product → Template listesi daralır; Template seçilince **önizleme kutusu** (Description, tahmini ağırlık, rev).

**Disabled/Enabled:** Template yokken Piece Mark editlenemez veya kısıtlı (ürün kararı).

**Add | Cancel**

**Modal vs drawer:** **Modal P0**; önizleme > ekranın %40’ı ise **drawer** alternatif (not).

**Validation:** Qty > 0; zorunlu alanlar.

**Başarı:** Modal kapanır, liste yenilenir, toast “Piece mark oluşturuldu”.

---

### L. Edit Production Pieces — Piece Mark Information

**Üst şerit:** Amber **JOB** bandı: Job, Location, Phase, Product Category (kısa).

**Form Alanları (instance):** Job, Location, Phase, Product Category, Product Type, Cross Section, Piece Mark, Qty, Drawing Status, Date Issued, Length / Width / Depth, Weight, Note, Rev, Rev Text, Rev Date, Return Legs, Struct CY / Arch CY / Total CY, Release Str, 28 Day Release, Struct SF / Arch SF / Total SF, Brace Type, Brace Qty, Add Work 1..6, Drawn By, Date Drawn, Checked By, Date Checked, **release badge** (ör. Not Released / Released).

**Alt grid — piece instances:**

| Kolon |
|-------|
| status |
| CTRL Num |
| Piece S/N |
| GUID |
| Yard Loc |
| Cast Date |
| Bed Name |
| Pos |
| Load Date |
| Load No |
| QC Check |
| Pre Pour |
| Post Pour |
| Shipping |
| Count CY |
| Count SF |
| AW1 … AW6 |

**Toplu düzenleme:** Çoklu seçim + “Set status” (mock).

**Sağ panel:** “Drawing status” açıklaması + QC uyarıları mock.

**Validation:** Tarih sıraları; Released iken kritik alan readonly (mock kural).

---

### M. Edit Production Pieces — Standard Material

**İki alt sekme:** Material Items | Material Assemblies.

**Kolonlar:** Category, Material Num, Embed Label, Description, Qty, Prev. Qty, Act. Qty, Prev. Act. Qty, Weight, Unit, Bend Type, Dim Length.

**Görsel ayrım:** Plan (Prev.*) sütunları **açık mavi** header; Gerçekleşen (Act.*) **açık yeşil** header.

**Üst aksiyonlar:** BOM Copy, BOM Export, Save, Save & Close, Close.

**Şerit:** “Şablondan türetilmiş BOM; değişen satırlar işaretli” + satırda küçük kalem ikonu.

**Sağ panel:** Toplam sapma özeti (mock).

---

### N. Opsiyonel: Job Specific Material

**Fark:** Sadece bu işe özel ek kalemler; şablonda yok; genelde istisna/change order.

**Ne zaman:** Saha talebi, mühendislik değişikliği.

**UI:** Üçüncü ana sekme **“Job Specific Material”** veya Standard Material altında **ayrı alt bölüm** + “Add job-specific line” (P2 öncelik).

**Kısa:** Standard ile aynı grid yapısı; satırda “JS” badge.

---

## 8. Sekmeler ve ekranlar arası ilişki matrisi

| Ekran | Catalog Items | Catalog ASM | Template Header | Tpl Items | Tpl ASM | Tpl Costs | Add Modal | Prod Header | Prod Std Mat |
|-------|---------------|-------------|-----------------|-----------|---------|---------|-----------|-------------|--------------|
| Material Item master | ✓ edit | | | satır lookup | satır lookup | | | | satır lookup |
| Assembly master | | ✓ edit | | | satır lookup | | | | |
| Template | | | ✓ | ✓ | ✓ | ✓ | kaynak | | |
| Production instance | | | şablondan kopya | şablondan kopya | şablondan kopya | (P2 tartışma) | hedef | ✓ | ✓ |

---

## 9. Riskler ve UX karşılıkları

| Risk | Çözüm |
|------|--------|
| Yoğun formlar | Accordion, section anchor, “Show advanced” |
| Master vs instance karışması | Renk şeridi, başlık etiketi “TEMPLATE” / “JOB” |
| Item vs assembly | İkon + ayrı Catalog alt menü |
| Template vs piece | Aynı layout, farklı banner ve salt okunur alan seti |
| Çok kolon | Column chooser, freeze, dense mode |
| Ölçü/maliyet/karışık hiyerarşi | Üç kart: Boyutlar, Hacim/Yüzey, Maliyet (Costs sekmesinde) |

---

## 10. Açık sorular

- Template ve production ekranları: **layout aynı**, veri kaynağı farklı etiketle mi kalsın, yoksa production’da alan alt kümesi mi?
- Custom fields: **global şema mı**, plant override mu?
- Nested assembly: **v1’de tek seviye** mi, çok seviye P2 mi?
- Costs: **şablonda only** mu, production’da **override satırı** mu?
- Add From Template: **tekli** P0; **çoklu instantiate** (liste seç → toplu oluştur) P1?

---

## 11. Sistem içindeki yer

**Zincir:** Material catalog → Assembly tanımı → Piece mark template authoring → Template’den production piece → Instance’da engineering/material düzenleme.

**Kavramsal temas (implementasyon yok):** Proje yönetimi (job), üretim planlama, MES (piece serial), kalite (QC kolonları), yard/sevkiyat (Yard Loc, Load).

---

## 12. Ek zorunlu çıktı sırası (bu dokümanın indeksi)

Aşağıdaki sıra, talep edilen “ek zorunlu çıktı formatı” ile birebir örtüşür:

1. **Modül için önerilen isim** → Bölüm 1 (`Manual Piece & Template Studio-okan`).
2. **Modül özeti** → Bölüm 2.
3. **Kullanıcı akışı** → Bölüm 3.
4. **Bilgi mimarisi** → Bölüm 4 + Alternatif kararlar tablosu.
5. **Tüm sayfaların tek tek detaylı çözümü** → Bölüm 7 (A–N).
6. **Sekmeler ve ekranlar arası ilişki matrisi** → Bölüm 8.
7. **UI prensipleri** → Bölüm 6 + Bölüm 7 içi UX notları.
8. **Riskler** → Bölüm 9.
9. **Açık sorular** → Bölüm 10.

---

*Bu doküman prompt-designer standardında UI/IA çıktısıdır; uygulama kodu üretmez.*

**Yazar:** Okan · **Modül:** Manual Piece & Template Studio-okan
