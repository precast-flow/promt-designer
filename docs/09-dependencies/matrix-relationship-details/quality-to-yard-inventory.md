## 🔍 Konu Tanımı

`Quality Control` modülünün `Yard / Inventory` modülüne bağımlılığı:
`Quality → Yard/Inventory = D4 (Süreç bağımlılığı)`.

## 🎯 Amaç

- Kalite kabul edilmemiş elemanların fiziksel olarak yard/stok alanına “kayıtlı” şekilde girmesini engellemek.
- Kalite retlerinde stok/yard hareketlerinin doğru şekilde geri alınmasını veya iptal edilmesini sağlamak.

## 🧠 Tartışma Alanı

- Kalite kontrol kararları yard’a girişte nasıl bir gate oluşturuyor: kabul/ret mi, kısmi kabul mü?
- Kusurlu elemanlar tekrar tamir görürken aynı fiziksel seriyle mi devam edilir, yoksa yeni kimlik mi açılır?

## ⚖️ Alternatifler

- **Alternatif 1 (D3):** Kalite yard’a giriş için “bilgilendirme” sağlar; yard yönetimi yine de süreçte insan onayıyla ilerler.
- **Alternatif 2 (D2):** Yard stok sadece kalite sonuçlarını referans okur; yard girişi kaliteye bağlı gate olmadan yapılır.
- **Alternatif 3 (D4):** Yard’a giriş, kalite onayı olmadan yapılamaz (gate).

Bu dokümanda D4 yaklaşımı esas alınır.

## 🧱 Yapısal Analiz

### Bağımlılık neden D4?

`D4` burada:

- Yard’a giriş gibi fiziksel/operasyonel bir adım, kalite kararına bağlıdır.
- Yani kalite onayı (kabul) gerçekleşmeden elemanın “stokta var” statüsüne geçişi mümkün değildir.

### Zorunlu kalite çıktısı

Quality Control’dan Yard/Inventory’ye aktarılması beklenen minimum:

- Eleman kimliği (parça id)
- Kalite kararı (kabul / ret / kısmi kabul)
- Gerekirse kalite raporu referansı (test/ölçüm dökümanı)
- Karar zamanı ve karar veren süreç kaydı (izlenebilirlik)

### Tipik Senaryo (Akış)

1. Üretim tamamlanan eleman kalite kontrol sürecine alınır.
2. Ölçümler ve testler tamamlanır.
3. `Eleman Kalite Onaylandı` event’i (veya ret) yayımlanır.
4. Yard/Inventory bu event’i tüketir.
5. Yard’a giriş kaydı sadece “kabul” kararında oluşturulur.
6. Yard lokasyonu/alanı atanır ve elemanın stok statüsü güncellenir.
7. Ret durumunda eleman “yard’a giremez” veya “tamir alanı” gibi ayrı bir akışa yönlendirilir.

### Senkron vs Asenkron strateji

- Event asenkron olabilir.
- Ama yard’a giriş aksiyonu D4 gate gerektirir: event doğrulanmadan stok statüsü set edilmemelidir.

## 🔄 Sistem İçindeki Yeri

- Stok/yard doğruluğu üretim hatalarının maliyetini belirler. Bu ilişki, yanlış stok girişlerini önleyen “kontrol kapısıdır”.

## ❗ Riskler

- Kalite kararlarının gecikmesi yard akışını tıkar (süreç sıkışması).
- “Kısmi kabul” gibi ara statüler tanımlanmazsa süreç taşar.

## ❓ Açık Sorular

- Yard’a girişte sadece “kabul” mü var, yoksa “tamir edilecek” statüsü yard içinde ayrı lokasyona mı akacak?
- Ret sonrası süreç: eleman üretime geri mi döner, yoksa sadece tamir/iyileştirme mi?

