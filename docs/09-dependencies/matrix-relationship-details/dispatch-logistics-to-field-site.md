## 🔍 Konu Tanımı

`Dispatch / Logistics` modülünün `Field / Site` modülüne bağımlılığı:
`Dispatch/Logistics → Field/Site = D3 (Event bağımlılığı)`.

## 🎯 Amaç

- Sevkiyatın ilerlemesini (araç çıkışı, teslimat bilgisi) saha uygulamasına “otomatik bildirim” şeklinde taşımak.
- Saha tarafında montaj/teslimat ilerlemesinin doğru sevkiyat kimliği ile ilişkilendirilmesini sağlamak.

## 🧠 Tartışma Alanı

- Field modülü sevkiyat bilgisini sadece “izleme” mi yapacak (D3), yoksa saha onaylarıyla sevkiyatın akışını mı etkileyecek (muhtemel D3/D4 kombinasyonu ileride)?
- Teslimat başarısız olursa saha bilgisini hangi event’lerle geri dönecek?

## ⚖️ Alternatifler

- **Alternatif 1 (D3):** Dispatch event yayımlar; Field bunu tüketir ve kendi saha görevlerini günceller. (Bu dokümanda hedef)
- **Alternatif 2 (D2):** Field dispatch’ten veri okumak için sürekli sorgu yapar (okuma bağımlılığı).
- **Alternatif 3 (D4):** Saha, teslimatı onaylamadan dispatch başka adım atamaz (saha gate’i daha sıkı olur).

## 🧱 Yapısal Analiz

### Bağımlılık neden D3?

`D3` burada şunu temsil eder:

- Dispatch modülü “sevk/saha teslimat durumu” ile ilgili bir event yayımlar.
- Field modülü bu event’leri tüketir.
- Saha ilerleme kayıtları, sevkiyat event’lerinin geldiği bağlamla eşleştirilir.

### Zorunlu event / veri

Saha tarafında doğru iş yapmak için sevk event payload’ında bulunması gereken minimum:

- Proje / şantiye referansı
- Sevkiyat/araç/yükleme kimliği (sevkiyatın bağlamı)
- Eleman kimlikleri veya parti kimlikleri (montaj planıyla eşleşme)
- Teslimat zaman penceresi veya gerçek teslimat zamanı
- Durum (ör. yola çıktı, ulaştı, teslim edildi)

### Tipik Senaryo (Akış)

1. Dispatch yükleme ve araç çıkışı işlemini tamamlar.
2. `Araç Tesisten Çıktı` veya `Teslimat Planlandı` gibi bir event yayımlar.
3. Field bu event’i alır ve saha kabul ekranlarını “o yük” için hazır hale getirir.
4. Araç sahaya geldiğinde saha `teslim alındı` gibi bir kayıtla durumu günceller.
5. Montaj ilerleme bu sevkiyat/eleman setiyle ilişkilendirilir.
6. Saha varsa sapmaları (hasar, gecikme, eksik parça) ayrı bir geri besleme akışı olarak başlatır.

### Senkron vs Asenkron strateji

- D3 event temelli asenkron akış idealdir.
- Field’ın sahada “sevkiyat kaydı olmadan” montaja başlaması engelleniyorsa bu D3’ün yanında gate mantığı da gerekebilir; bu sonraki turda netleştirilir.

## 🔄 Sistem İçindeki Yeri

- Sevkiyat, saha görevlerinin planlamasını belirler. D3, doğru zamanda doğru bilgiyi sahaya taşıma ihtiyacından doğar.

## ❗ Riskler

- Event’ler gecikirse saha yanlış “bekleme” veya yanlış montaj sırası uygulayabilir.
- Payload eksik olursa saha, sevkiyat elemanlarını montaj planıyla doğru eşleştiremez.

## ❓ Açık Sorular

- Field’de “teslim edildi” onayı hangi rol tarafından verilecek?
- Saha eksik parça/hasar durumlarını dispatch’e geri bildirmek için hangi event seti kullanılacak?

