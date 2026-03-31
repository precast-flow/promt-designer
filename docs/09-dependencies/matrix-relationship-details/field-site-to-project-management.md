## 🔍 Konu Tanımı

`Field / Site` (Şantiye) modülünün `Project Management` (Proje) modülüne bağımlılığı:
`Field/Site → Project Management = D3/D4`.

## 🎯 Amaç

- Şantiye ilerlemesi ve sahadan gelen durumları proje düzeyinde ilerleme, risk görünürlüğü ve (varsa) hakediş iş akışına yansıtmak.
- Sahadaki olayların proje yönetimi tarafında “bilgi” ve bazı kararlar için “gate” olarak kullanılmasını dengeli kurmak.

## 🧠 Tartışma Alanı

- Şantiye bilgisi proje ilerlemesini otomatik mi günceller, yoksa proje yöneticisi onayıyla mı kapanışa gider?
- Hakediş gibi finansal adımlar için saha event’leri ne kadar sıkı olmalı (D4)?

## ⚖️ Alternatifler

- **Alternatif 1 (D3 ağırlıklı):** Şantiye sadece ilerleme/olay event’i üretir; proje tarafı raporlar ve onaya bağlı iş akışı ayrı yürür.
- **Alternatif 2 (D4 ağırlıklı):** Sahadan gelen bazı event’ler olmadan proje ilerleme statüsü değişmez (ör. “montaj tamamlandı” hakedişi tetikler).
- **Alternatif 3 (D2):** Proje, saha verisini dönemsel olarak okur (batch); gerçek zamanlı akış yok.

Bu dokümanda D3/D4 karışımı hedeflenir: hem event akışı hem bazı gate’ler.

## 🧱 Yapısal Analiz

### D3 neyi temsil eder?

- Field, `Teslim edildi`, `Montaj tamamlandı`, `Gecikme bildirildi` gibi olayları event olarak üretir.
- Project Management bu event’leri tüketir ve proje ilerleme görünürlüğünü günceller.

### D4 neyi temsil eder?

- Bazı event’ler (özellikle ilerleme kapanışı / hakediş tetikleyenler) proje tarafında statü geçişini kilitler.
- Yani “montaj tamamlandı” gibi olaylar gelmeden proje kapanış/ilerleme adımı ilerleyemez.

### Zorunlu event seti (yüksek seviye)

- `Montaj tamamlandı` (eleman seti / tarih / saha onayı bilgisi ile)
- `Teslimat durumu` (yolda, geldi, teslim alındı)
- `Sapma bildirimi` (eksik parça, hasar, revizyon ihtiyacı, gecikme)

### Tipik Senaryo (Akış)

1. Saha ekipleri sevkiyat ve montaj ilerlemesini kaydeder.
2. Montaj/teslimat adımlarında event üretimi tetiklenir.
3. Project Management event’leri tüketir.
4. Proje ilerleme statüsü event’lere göre güncellenir (D3 etkisi).
5. Belirli kritik eşikler için (ör. “proje fazı tamam” veya hakedişe geçilecek noktalar) gate mantığı devreye girer (D4).
6. Gate geçince proje tarafında bir kapanış/sonuç çıktısı üretilir.
7. Geri besleme olarak mühendislik/üretim tarafına yeni aksiyon event’leri üretilebilir (revizyon/eksik parça).

### Senkron vs Asenkron strateji

- Saha event’leri asenkron yayımlanmalı.
- Gate’ler proje tarafında deterministik doğrulama gerektirir (doğru saha referansı, doğru proje fazı, yeterli onay bilgisi).

## 🔄 Sistem İçindeki Yeri

- Bu ilişki, “saha gerçekliğini” proje yönetiminin doğru aksiyonuna bağlar. ERP’de raporlamadan çok daha kritik bir rol oynar.

## ❗ Riskler

- Saha event’leri gecikmeli veya eksik payload’la gelirse proje tarafında yanlış ilerleme statüsü oluşur.
- Hakediş veya kapanış gibi adımlar D4 ile aşırı sıkı kurgulanırsa operasyon tıkanabilir.

## ❓ Açık Sorular

- Proje ilerleme statüsünü güncelleyen event’ler hangi rollere bağlı (saha şefi mi, saha operatörü mü)?
- Hakediş hesaplaması için gereken saha doğruluğu seviyesi nedir?

