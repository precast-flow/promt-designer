## 🔍 Konu Tanımı

`Yard / Inventory` modülünün `Dispatch / Logistics` modülüne bağımlılığı:
`Yard/Inventory → Dispatch/Logistics = D2/D4 (Veri okuma + süreç bağımlılığı)`.

## 🎯 Amaç

- Sevkiyat planlamasında kullanılacak eleman “uygunluk” ve “bulunurluk” bilgisinin yard tarafından doğrulanmasını sağlamak.
- Sevkiyat başlamadan önce elemanların fiziksel lokasyon/yard statüsünün doğru olmasını garanti altına almak.

## 🧠 Tartışma Alanı

- Dispatch, yard verisini sadece “ne var?” için mi okur (D2), yoksa “sevk edilecek eleman” olma statüsü için onay gate’i de mi ister (D4)?
- Aynı elemanın farklı lot/parti veya farklı lokasyonlarda görünmesi nasıl engellenir?

## ⚖️ Alternatifler

- **Alternatif 1 (D2 ağırlıklı):** Dispatch yard envanterini okur, sevkiyatı başlatmak tamamen süreçsel onayla yapılır (yard gate’i daha zayıf).
- **Alternatif 2 (D4 ağırlıklı):** Sevk edilecek eleman seçimi ve tahsis işlemi yard onayı gerektirir.
- **Alternatif 3 (D3 + event):** Yard, “eleman sevke hazır” gibi event yayar; dispatch bunu tüketip seçim yapar.

Bu dokümanda D2/D4 birlikte değerlendirilir.

## 🧱 Yapısal Analiz

### D2 neyi temsil ediyor?

`D2` burada şu anlama gelir:

- Dispatch, yard’ın sahip olduğu “aktif envanter” bilgisini okur:
  - eleman kimliği
  - lokasyon
  - sevkiyata uygunluk statüsü (yard politikası)

### D4 neyi temsil ediyor?

`D4` burada şu ek kararı gösterir:

- Sevkiyat planı içinde “tahsis/kilit” veya “sevk adayı” statüsü yard içinde bir işlem gerektirir.
- Yani dispatch rastgele bir elemanı seçip kilitleyemez; yard’ın onayladığı/izin verdiği elemanlar üzerinden ilerler.

### Tipik Senaryo (Akış)

1. Yard/stok alanında eleman kabulü ve lokasyon ataması yapılmıştır.
2. Dispatch modülü, ilgili proje/termin için sevkiyat planına aday elemanları bulmak ister.
3. Yard’dan uygunluk bilgisi okunur (D2).
4. Dispatch, sevk planında “şu elemanlar”ı seçer.
5. Yard tarafında sevke tahsis/kilit aksiyonu gerekir (D4): seçilen eleman artık başka sevkiyat için kullanılmamalıdır.
6. Yard’dan ilgili “tahsis onayı” veya güncel statü bilgisi dispatch tarafından kullanılır.
7. Sevkiyat hazırlığı başlar (loading gibi saha adımları ayrı context’te yürür).

### Senkron vs Asenkron strateji

- D2 okuyarak seçim yapmak event veya read model üzerinden olabilir.
- D4 gate için (tahsis/lock) ya event + doğrulama ya da kontrollü transaction benzeri bir garanti politikası gerekir.

## 🔄 Sistem İçindeki Yeri

- Bu ilişki “elleçleme/lojistikte yanlış eleman çıkmasını” engelleyen çekirdek kontrol noktasıdır.

## ❗ Riskler

- Tahsis kilidi yeterince yoksa eleman aynı anda iki sevkiyat için görünür (çakışma).
- Lokasyon/stok güncellemeleri gecikirse dispatch yanlış lokasyondan eleman almaya çalışır.

## ❓ Açık Sorular

- Yard’a uygunluk statüsü (sevke uygun) kim tarafından ve hangi kriterle set edilir?
- Dispatch’in “tahsis kilidi” hangi seviyede olur: eleman mı, parti mi, lokasyon mu?

