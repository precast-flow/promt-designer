# MVP detaylı analiz raporu — Precast Flow

## 🔍 Konu Tanımı

Bu doküman, beton prefabrik süreç yönetimi ürününün **ilk canlıya çıkabilecek minimum uygulanabilir sürüm (MVP)** kapsamını genişleterek analiz eder. Amaç: hangi işlerin MVP’de yapılması mantıklı olduğunu; hangi modül ve yapıların **tamamlanmış** sayılması gerektiğini; kullanıcı tarafından **kesin** istenen **dinamik rol / yetki** ve **kullanıcı yönetimi** ekranlarının MVP içinde nasıl konumlandığını netleştirmek.

**Referans:** `mvp-scope.md`, `release-phases.md`, `01-business-process/overview.md`, `modules-landscape.md`, `roles-and-responsibilities.md`.

---

## 🎯 Amaç

- MVP ile **iş değeri** üreten uçtan uca veya yarı-uçtan uca bir akışı mümkün kılmak.
- **Çok kiracılı (multi-tenant) olmasa bile**, en azından **kurum içi rol ve yetki** ile güvenli pilot çalıştırmak.
- Pilot sonrası genişlemeye izin verecek **platform iskeletini** (kimlik, kullanıcı, rol, izin) MVP’de kurmak.

---

## 🧠 MVP felsefesi ve önceliklendirme

### Öncelik etiketleri

| Etiket | Anlamı |
|--------|--------|
| **P0** | MVP **olmazsa olmaz**; pilot bunlar olmadan güvenli veya anlamlı değil |
| **P1** | MVP’de **olması çok istenen**; süre kısıtında P0 sonrası ilk doldurulacak işler |
| **P2** | **İdeal MVP+** veya **Faz 1.5**; varlığı değer katar ama ilk haftalar atlanabilir |

### Temel ilke

- İlk MVP’de **her modülün “tam ürün” olması** gerekmez; ancak seçilen akışta **veri ve durum tutarlılığı** olmalıdır.
- **Kimlik, kullanıcı, rol ve yetki** (aşağıda zorunlu) pilot için **risk azaltıcı** ve satış/demo için **güven** sağlayıcıdır.

---

## ✅ Kesin MVP kapsamı (kullanıcı talebi — zorunlu)

Aşağıdakiler **MVP tanımına dahil edilmelidir** (P0).

### 1) Dinamik rol, sorumluluk ve yetki yapılandırması (RBAC / yetki matrisi)

**Ne olmalı?**

- Yönetici (veya “Güvenlik yöneticisi”) tarafından kullanılabilen bir **Yönetim** bölümü:
  - **Rol tanımları:** rol adı, açıklama, aktif/pasif.
  - **İzinler (permissions):** modül veya ekran / aksiyon bazlı atomik izinler (ör. `teklif.onayla`, `uretim.emri.olustur`, `sevkiyat.cikis.kaydet`).
  - **Rol ↔ izin ataması:** matris veya gruplu checkbox; kaydet öncesi özet.
  - **İsteğe bağlı MVP içi sadeleştirme:** “sorumluluk” alanı rol kartında serbest metin veya etiket listesi (iş tanımı); ileride iş akışı ile bağlanabilir.

**Neden MVP’de zorunlu?**

- Prefabrik operasyonda aynı kişi birden fazla şapka giyer; **statik hard-coded roller** pilotu kilitler.
- Teklif onayı, üretim emri, sevkiyat çıkışı gibi adımlar **yetkisiz kullanıcıya açılmamalı**.

**Tasarım / sayfa beklentisi (ürün, kod değil)**

- Sol: rol listesi (neumorphic liste kartı uyumlu).
- Sağ: seçili rol detayı; sekmeler: **Genel**, **İzinler**, **Kullanıcılar (bu role atanmış)**.
- İzinler sekmesi: modül gruplarına göre açılır bölümler (CRM, Teklif, Proje, …); her izin için kısa açıklama tooltip.
- **Sistem rolleri** (ör. Süper yönetici) koruması: silinemez / kilitli ikon + açıklama metni.

**Kabul kriterleri (MVP)**

- [ ] Yeni rol oluşturulup izin atanabiliyor.
- [ ] En az bir test kullanıcısı bu rolle giriş yaptığında yetkisiz menü/aksiyon görünmüyor veya API reddediliyor (ürün kararı: UI hide + server enforce ikisi de hedeflenmeli).
- [ ] Varsayılan roller şablonu (ör. Satış, Planlama, Üretim, Sevkiyat, Yönetici) tek tıkla yüklenebiliyor veya ilk kurulumda seed ediliyor.

---

### 2) Kullanıcı yönetimi

**Ne olmalı?**

- **Kullanıcı listesi:** ad, e-posta, durum (aktif/pasif), son giriş (placeholder kabul), atanmış roller.
- **Kullanıcı oluşturma / düzenleme:** ad, e-posta, geçici şifre veya davet akışı (MVP’de e-posta daveti P1 olabilir; manuel şifre P0 olabilir).
- **Rol atama:** çoklu rol seçimi; birincil rol (isteğe bağlı) veya tüm roller eşit (ürün kararı).
- **Hesap kilitleme / pasifleştirme:** anında erişimi kesmek için.

**Neden MVP’de zorunlu?**

- Pilot kullanıcı sayısı az olsa bile **kim kimin yerine** giriyor, **kim onaylıyor** izlenebilir olmalı.
- Denetim ve güvenlik için temel gereklilik.

**Tasarım / sayfa beklentisi**

- Liste + sağ detay veya tam sayfa form; üstte filtre (rol, durum, arama).
- Detayda sekmeler: **Profil**, **Roller**, **Oturum / güvenlik** (MVP’de sadece şifre sıfırlama tetikleyicisi placeholder).
- Tehlikeli aksiyon: kullanıcıyı pasifleştir → onay modalı.

**Kabul kriterleri (MVP)**

- [ ] Kullanıcı CRUD (en az create + update + list + deactivate).
- [ ] Kullanıcıya bir veya birden fazla rol atanabiliyor.
- [ ] Pasif kullanıcı giriş yapamıyor.

---

## 🧱 MVP iş paketleri (özet tablo)

| Paket | İçerik | Öncelik |
|-------|--------|---------|
| **Platform & güvenlik** | Giriş, oturum, kullanıcı, rol, izin, denetim izi (minimal) | **P0** |
| **CRM** | Müşteri/kontak, proje ile ilişkilendirme (basit) | P0–P1 |
| **Teklif** | Taslak, onay akışı (en az tek seviye onay) | P0–P1 |
| **Proje** | Proje kartı, temel bilgiler, teklif bağlantısı | P0 |
| **Mühendislik** | Basit paket / revizyon / “üretime hazır” bayrağı (CAD entegrasyonu derinliği P2) | P1 |
| **MES** | Üretim emri, günlük durum, basit plan görünümü | P0–P1 |
| **Kalite** | MVP’de **sadeleştirilmiş**: onay checkbox + not veya “üretim tamamlandı = kalite bekliyor” kuyruğu | P1 veya P2 |
| **Yard** | Lokasyon + envanter satırı + sevkiyata hazır işareti | P0–P1 |
| **Sevkiyat** | Plan veya direkt çıkış kaydı + araç/yükleme placeholder | P0–P1 |
| **Şantiye (Field)** | **İnce MVP:** sevkiyat çıkışına bağlı “teslim alındı” kaydı veya sadece sevkiyat içinde not | P2 |
| **Raporlama** | 2–3 sabit rapor veya dashboard KPI (gerçek veri) | P1 |
| **Audit** | Kritik aksiyonların kim/ne zaman kaydı (minimal) | P1 |

---

## 📦 Modül bazında MVP önerisi (detay)

### Platform (yeni “modül” olarak düşünülmeli)

- **P0:** Kimlik doğrulama, kullanıcı, rol, izin, yönetim menüsü.
- **P1:** Basit denetim günlüğü (teklif onayı, üretim tamamlama, sevkiyat çıkışı, rol değişikliği).
- **P2:** SSO, 2FA, parola politikası.

### CRM / Contact

- **P0:** Müşteri oluşturma, kontak, temel arama/filtre.
- **P1:** Müşteriye proje bağlama, teklif başlatma kısayolu.
- **P2:** Segmentasyon, etiketler, müşteri portalı.

### Estimating & Quoting

- **P0:** Teklif taslağı, kalem satırları, toplam; **en az bir onay adımı** (tek onaycı yeterli).
- **P1:** Versiyonlama, PDF dışa aktarma (veya yazdır görünümü).
- **P2:** Çok adımlı onay, maliyet motoru, ERP fiyat entegrasyonu.

### Project Management

- **P0:** Teklif onayı sonrası proje oluşturma; proje özet ekranı; durum.
- **P1:** Eleman listesi (basit tablo), revizyon alanı placeholder.
- **P2:** Gantt, risk, doküman DAM.

### Engineering Integration

- **P1 (önerilen):** “Paket” veya “dosya seti” yükleme, revizyon numarası, **üretime hazır** onayı (CAD otomasyonu olmadan).
- **P2:** CAD/BIM entegrasyonu, otomatik piece list import.

### Production / MES

- **P0:** Üretim emri oluşturma; başlat / tamamla; günlük liste görünümü.
- **P1:** Hat/vardiya filtresi, basit slot veya sıra.
- **P2:** Kapasite optimizasyonu, IoT, detaylı OEE.

### Quality

- **P1 veya P2:** MVP’de tam kalite modülü yerine **“üretim kapanışı onayı”** tek ekranı bile yeterli olabilir.
- **P1 önerisi:** Kuyruk + onay/ret + sebep kodu (kısa liste).

### Yard / Inventory

- **P0–P1:** Elemanın yard’a girişi, lokasyon kodu, stokta görünürlük.
- **P2:** Harita/grid görselleştirme, transfer kuralları.

### Dispatch

- **P0–P1:** Sevkiyat kaydı (çıkış zamanı, araç plaka placeholder, yüklü eleman listesi).
- **P2:** Rota optimizasyonu, nakliyeci portalı.

### Field / Site

- **P2 (ince):** Sevkiyat satırında “teslim alındı” onayı veya tek sayfalık saha listesi.
- **P3:** Offline mobil, fotoğraf zorunluluğu, imza.

### Reporting

- **P1:** Dashboard’da gerçek sayılar (aktif proje, bugün üretim, yard bekleyen, bugün sevkiyat).
- **P2:** Özel rapor oluşturucu.

---

## 🔗 Uçtan uca “MVP demosu” akışı (hedef)

Pilot anlatımı için hedeflenen minimal hikâye:

1. Yönetici: rolleri ve izinleri tanımlar; pilot kullanıcıları oluşturur.
2. Satış: müşteri + teklif + onay.
3. Proje: tekliften proje açılır.
4. Mühendislik (P1): üretime hazır işaretlenir **veya** MVP sadeleştirmesi: proje yöneticisi manuel bayrak.
5. Üretim: emir oluşturulur, tamamlanır.
6. Yard: giriş ve lokasyon.
7. Sevkiyat: çıkış kaydı.
8. (İsteğe bağlı P2) Saha: teslim alındı.
9. Dashboard: rakamlar güncellenir.

Bu akışta kopukluk varsa MVP kapsamı **daraltılmalı** veya **manuel adım** açıkça etiketlenmelidir.

---

## 🏗️ MVP’de “tamamlanmış” sayılması gereken yapılar

### Veri ve süreç

- **Kimlik doğrulama** ve **oturum** (en az kullanıcı adı/şifre veya sağlayıcı seçimi — ürün kararı).
- **Tenant / organizasyon** (tek firma pilotu için bile “OrganizationId” benzeri zemin ileride çok kiracı için faydalıdır; MVP’de tek kayıt yeterli olabilir).
- **Temel ana varlıklar:** Kullanıcı, Rol, İzin, Müşteri, (opsiyonel Kontak), Proje, Teklif, Üretim emri, Yard kaydı, Sevkiyat kaydı.

### Teknik / mimari (yüksek seviye, uygulama detayı değil)

- Sunucu tarafında **izin kontrolü** (UI gizlemek yetmez).
- **Audit** için minimum tablo veya log (P1 önerilir ama güvenlik satışı için değerlidir).

---

## ➕ MVP dışında eklenebilecekler (araştırma / öneri listesi)

Aşağıdakiler **MVP sonrası** veya **MVP+** için değerlendirilir; iş değeri yüksek olanlar Faz 1.5’e alınabilir.

| Özellik | Değer | Not |
|---------|--------|-----|
| **Bildirim merkezi** (in-app) | Orta–yüksek | Onay bekleyen teklif, üretim gecikmesi |
| **Görev / iş kuyruğu** | Yüksek | Rol bazlı “yapılacaklar” — operasyonel netlik |
| **Dosya ekleri** (proje, teklif, üretim) | Orta | Basit S3/blob; versiyon P2 |
| **E-posta daveti** kullanıcıya | Orta | Güvenlik ve UX |
| **Parola sıfırlama** self-servis | Orta | Destek yükünü azaltır |
| **Çoklu dil (i18n)** | Değişken | İhracat odaklı firmalarda erken |
| **Baskı / etiket** (QR ile eleman) | Yüksek | Yard–MES–Sevkiyat hattında hata azaltır |
| **Basit entegrasyon köprüsü** (CSV import/export) | Yüksek | CAD veya ERP olmadan veri girişi |
| **Takvim görünümü** sevkiyat | Orta | Lojistik planlama |
| **Mobil web** saha için | Orta | Native app öncesi |
| **API anahtarları** (3. parti) | Düşük–orta | İlk pilotlarda genelde gereksiz |

---

## ❗ Riskler

- **Kapsam şişmesi:** Kalite + saha + CAD aynı anda MVP’ye girerse teslim tarihi kaçar.
- **Yetki karmaşıklığı:** Çok granüler izin listesi yönetim ekranını zorlaştırır — MVP’de **modül düzeyi + kritik aksiyon** izinleriyle başlanıp detay açılabilir.
- **Rol–gerçek iş uyumsuzluğu:** Küçük firmada herkes “her şeyi” ister; **şablon roller** ve “kısıtlı pilot rolü” ile sınır çizilmeli.

---

## ❓ Açık sorular (ürün kararı)

1. MVP pilotu **tek fabrika / tek şirket** mi, yoksa baştan **çok kiracı** mı hedefleniyor?
2. Teklif onayı **tek kişi** mi yoksa **hiyerarşi** (tutar eşiği ile) MVP’de var mı?
3. Mühendislik modülü MVP’de **dosya yükleme** ile mi yoksa **manuel checkbox** ile mi kapanacak?
4. Kalite MVP’de **tam modül** mü, yoksa **üretim kapanış onayı** mı?
5. Şantiye için ilk sürümde **sadece web** yeterli mi?

---

## 📎 İlişkili dokümanlar

- `mvp-scope.md` — önceki kısa MVP taslağı (bu rapor onu genişletir ve RBAC/kullanıcıyı kesinler).
- `mvp-decisions-reanalysis.md` — paydaş yanıtlarına göre **yeniden analiz** ve UI prototip (Adım 11) girdisi.
- `release-phases.md` — sonraki fazlar.
- `08-use-cases/` — modül use case’leri dolduruldukça MVP kapsamı sayısal olarak doğrulanabilir.
- `../11-ui-mvp-prototype/README.md` — Adım 11: MVP mock UI prompt paketi.

---

## Özet cümle

**MVP;** güvenli pilot için **kullanıcı + dinamik rol/izin yönetimi** ile birlikte, **teklif → proje → üretim → yard → sevkiyat** çekirdeğini mümkün olan en sade haliyle çalışır hale getirmeyi hedeflemelidir; kalite, mühendislik derinliği, saha ve gelişmiş raporlama **bilinçli olarak** P1/P2’ye ötelenebilir.
