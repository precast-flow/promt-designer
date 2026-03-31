## 🔍 Konu Tanımı

`Estimating & Quoting` (Teklif) modülünün `Project Management` (Proje) modülüne bağımlılığı:
`Estimating & Quoting → Project Management = D4 (Süreç bağımlılığı)`.

## 🎯 Amaç

- Teklif onayı gerçekleşmeden “proje”yi resmi çalışma birimi olarak açmamak.
- Onaylanan tekliften doğan proje planı/termini için zorunlu çıktıları garanti altına almak.

## 🧠 Tartışma Alanı

- “Proje açılışı” şirket içi süreçte hangi statüde olmalı: teklif onayı mı, sözleşme imzası mı, avans ödemesi mi?
- Teklifteki revizyonlar proje içinde yeni proje mi yaratır, yoksa aynı proje içinde versiyon mu yönetilir?

## ⚖️ Alternatifler

- **Alternatif 1 (D3 ile event tabanlı):** Teklif onaylandı → proje adayına dönüşür, proje açma onayı ayrı bir gate olur.
- **Alternatif 2 (D2):** Teklifler proje içinde sadece “referans” olarak durur; süreç gate’i olmayacak şekilde proje daha erken açılır.
- **Alternatif 3 (tam senkron):** Proje açma işlemi teklif modülünde zorunlu bir senkron doğrulama gerektirir (genelde operasyonel yük getirir).

Bu dokümanda öncelik: “D4” ile süreç gate’i yaklaşımı.

## 🧱 Yapısal Analiz

### Bağımlılık neden D4?

`D4` burada şu anlama gelir:

- Proje akışının bir adımı (ör. “proje açıldı”, “mühendislik başlatıldı”, “üretim/planlama için kayıt üretildi”) **Teklif onayı/çıktısı olmadan ilerleyemez**.
- Yani bu bir “bilgiyi okuyorum” bağımlılığı değil, “iş adımı şartı” bağımlılığıdır.

### Bağımlılığı doğuran zorunlu “çıktı”

Teklif onayından proje tarafına aktarılması gereken zorunlu bilgi türleri:

- Proje bazlı kimlik/etiket (teklif referansı ile eşleşme)
- Proje kapsamı ana parametreleri (eleman tipleri / yaklaşık metraj grupları)
- Termin hedefleri (ya da termin hedefini taşıyan varsayımlar)
- Ödeme/şart koşullarının üretim planlamasını etkileyen kısımları (varsa)

### Tipik Senaryo (Akış)

1. Teklif ekibi bir teklif kaydı oluşturur ve teklif kalemlerini tanımlar.
2. Teklif “tamamlandı” durumuna alınır (revizyon takibi hazır).
3. Teklif onay süreci işletilir.
4. Teklif onaylandığında “Teklif Onaylandı” gibi bir iş olayı doğar.
5. Proje yönetimi bu olayı bir gate olarak kabul eder.
6. Proje açılır; proje içinde mühendislik & üretim planlaması için temel parametre seti oluşur.
7. Proje ilerledikçe teklif kaynaklı parametreler “sınır set” olur (sonradan revizyon gelirse proje içi revizyon akışı tetiklenir).

### Senkron vs Asenkron strateji

- **Event (asenkron) ile tetiklenir**, fakat proje açma gate’i nedeniyle proje açılışı “yanlış zamanda” olmamalıdır.
- Bu yüzden event tüketimi “kontrol edici” olmalı: proje açma işlemi event payload’unu doğrulayıp gate’i geçemiyorsa reddetmelidir.

## 🔄 Sistem İçindeki Yeri

- Bu ilişki, uçtan uca haritada “Teklif ve maliyetlendirme → Sözleşme ve proje açılışı” geçişinin omurgasıdır.
- Diğer bağımlılıklar (Engineering → MES gibi) proje açıldıktan sonra daha güvenle kurulabilir.

## ❗ Riskler

- Teklif onayı statüsü ile “sözleşme imzası” arasındaki fark yönetilmezse sahada yanlış üretim planı çıkar.
- Teklif revizyonları proje açıldıktan sonra gelir ve aynı proje içinde düzgün versiyonlanmazsa veri tutarsızlığı olur.

## ❓ Açık Sorular

- “Proje açılış gate”i: `teklif onayı` mı `sözleşme` mi `avans` mı?
- Teklif onayından sonra kapsam değişirse (kalem değişimi) proje nasıl revize edilir?

