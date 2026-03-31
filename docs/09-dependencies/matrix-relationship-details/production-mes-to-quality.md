## 🔍 Konu Tanımı

`Production Scheduling / MES` modülünün `Quality Control` modülüne bağımlılığı:
`Production/MES → Quality = D3/D4`.

## 🎯 Amaç

- Üretim tamamlandı bilgisini ve üretim çıktısının kimliklerini kalite kontrole güvenilir şekilde aktarmak.
- Kalite onayı olmadan kaliteyle ilişkili sonraki süreç adımlarının (yard’a giriş gibi) yanlış akmamasını sağlamak.

## 🧠 Tartışma Alanı

- Kalite süreci üretimden “sonra mı” yoksa üretim sırasında “paralel mi” yürür?
- Kalite retlerinde üretim tarafında hangi kayıtlar geri alınır: üretim emri mi, sadece eleman statüsü mü?

## ⚖️ Alternatifler

- **Alternatif 1 (D3 ağırlıklı):** Üretim event’leri kaliteye bildirim gönderir; kalite kontrol bir sonraki adım olarak başlar.
- **Alternatif 2 (D4 ağırlıklı):** Kalite onayı olmadan üretim “tamamlandı” kabul edilmez (daha sıkı gate).
- **Alternatif 3 (D2):** Kalite sadece raporlama için üretim verisini okur; süreç gate yok.

Bu dokümanda “D3/D4” birlikte değerlendirilir.

## 🧱 Yapısal Analiz

### D3 neyi temsil ediyor?

`D3` burada:

- MES tarafı “eleman/üretim çıktısı oluştu” event’i yayımlar.
- Quality tarafı bu event’i tüketerek ilgili kalite kayıtlarını başlatır veya tamamlanmış üretim doğrulamasını yapar.

### D4 neyi temsil ediyor?

`D4` kısmı:

- Bazı kalite kararları (örn. eleman kalite kabulü) ilgili statü geçişini kilitler.
- Böylece MES’teki “sonuç” statüsü, kalite kapanışıyla tamamlanır.

### Zorunlu çıktı / veri seti

- Eleman kimliği (parça/production unit id)
- Hangi üretim emrine bağlı olduğu
- Üretim tamamlandı zamanı / vardiya bilgisi (izlenebilirlik)
- Üretim revizyonu / kalıp bilgisi (yorumlanabilir kalite sonuç için)

### Tipik Senaryo (Akış)

1. MES günlük/hat üretimi yürütülür.
2. Eleman için “üretim tamamlandı” durumu oluşur.
3. MES kaliteye bir event yayımlar (`Eleman Üretim Tamamlandı`).
4. Quality modülü event’i tüketir ve kalite kontrol görevini başlatır.
5. Kalite testleri/ölçümleri tamamlanır; onay veya ret kararı verilir.
6. Quality tarafı sonucu geri bildiren bir kapanış event’i yayımlar (`Eleman Kalite Onaylandı/Ret`).
7. MES tarafında (veya sonraki süreçte) eleman statüsü buna göre güncellenir.

### Senkron vs Asenkron strateji

- Event temelli asenkron akış uygun.
- Ancak “kalite ret” durumunda üretim sonrası hareketin durması gerekiyor ise D4 mantığıyla gate kurmak gerekir.

## 🔄 Sistem İçindeki Yeri

- Kaliteyi “sonradan raporlama”dan çıkarıp, süreç akışını kontrol eden bir kontrol noktası haline getirir.

## ❗ Riskler

- MES event payload’ı eksik olursa kalite kaydı bağlanamaz.
- Kalite ret kararları net süreç politikası olmadan üretime geri dönmezse veri tutarsızlığı oluşur.

## ❓ Açık Sorular

- Kalite ret durumunda “tam yeniden üretim” mi, “tamir/iyileştirme” mi yönetilecek?
- Kalite kontrol görevlerinin ataması kim tarafından yapılır (otomatik mi, kalite operatörü mü)?

