## 🔍 Konu Tanımı

`Estimating & Quoting → Project Management = D4 (Süreç bağımlılığı)`

## 🎯 MVP Uygunluğu

**Beklenen MVP’de VAR / YÜKSEK OLASILIK.**

Çünkü MVP akışında “Teklif oluşturma ve onay” sonrasında “projenin açılması” var.

## 🧠 Tartışma Alanı (Sadeleştirme Kararları)

- `Proje açılışı` için gate tam olarak hangisi olacak?
  - Teklif onayı mı?
  - Teklifteki revizyon “kilidi” mi?
- Proje açıldıktan sonra teklif revizyonu gelirse:
  - proje içi güncelleme mi,
  - yoksa yeni proje fazı mı?

## ⚖️ Alternatifler

- **MVP Gate (önerilen):** Teklif onaylandı statüsü olmadan proje açma yok.
- **MVP Gate (alternatif):** Proje erken açılır; teklif revizyonu geldikçe proje planı güncellenir (daha az gate, daha çok operasyon riski).

## 🧱 Yapısal Analiz (Minimum Gereken Çıktı)

Bu bağımlılık için MVP’de “zaten” oluşması gereken zorunlu veri:

- Proje kimliği / proje referansı
- Teklif referansı ile eşleşme (izlenebilirlik)
- Tahmini kapsam parametreleri (en azından üretim planını tetikleyecek minimum set)

## 🔄 MVP’de nasıl çalıştırılır? (Plan)

1. `Estimating` tarafında teklif oluşturulur ve “hazır”a alınır.
2. Onay süreci işletilir ve `Teklif Onaylandı` statüsü oluşur.
3. Bu statü tetiklenince `Project Management` içinde proje açma aksiyonu yapılır.
4. Proje açılırken, tekliften sadece MVP için gerekli minimum parametreler proje kaydına taşınır.
5. Teklif revizyonu sonraki bir tarihte gelirse:
   - MVP’de “proje planını kilitleme” politikası sade tutulur (ör. revizyon otomatik değil, proje güncelleme isteği olarak gelir).

## 🔄 Sistem İçindeki Yeri

- MVP’de tekliften üretime giden ilk kritik geçiş noktasıdır.

## ❗ Riskler

- Teklif onay statüsü belirsiz kalırsa proje yanlış varsayımlarla başlar.
- Teklif revizyonunun proje planını otomatik bozması (MVP’de bunu minimize etmek gerekir).

## ❓ Açık Sorular

1. MVP’de “proje açılışı” gate’i kesin olarak hangisi olsun: `Teklif Onaylandı` mı, `Sözleşme İmzası` mı?
2. Teklif revizyonu gelince MVP’de tercih hangisi olsun:
   - A) proje içi güncelleme (otomatik değil, kontrollü onayla)
   - B) yeni proje fazı / revizyon fazı
3. MVP’de kaç adet teklif revizyonu “geri dönülebilir” sınırda tutulacak?

