## 🔍 Konu Tanımı

Tekil bir prefabrik elemanın (parça) yaşam döngüsü: fikir ve tasarım aşamasından başlayarak üretim, kalite kontrol, yard/stok, sevkiyat, montaj ve olası bakım/onarım adımlarına kadar geçen sürecin tanımı.

## 🎯 Amaç

- “Sipariş / proje” seviyesinden bağımsız olarak, tek bir elemanın baştan sona izlenebilirliğini modellemek.
- Kalite, garanti ve maliyetlendirme tartışmalarına girdi sağlayacak bir referans akış oluşturmak.

## 🧠 Tartışma Alanı

- Eleman ne zaman “doğmuş” kabul edilir: ilk taslak çizimde mi, üretim emrinde mi, kalıba girdiği anda mı?
- Kusurlu / reddedilen elemanların yeni eleman doğurarak mı, yoksa aynı kimlik altında mı yönetileceği.
- Aynı elemanın çoklu proje, faz veya revizyonlarla ilişkisinin nasıl tutulacağı.

## 🧱 Yapısal Analiz

Yüksek seviyede bir elemanın yaşam döngüsü:

1. Tasarım isteği / ihtiyaç tanımı
2. İlk mühendislik taslağı ve revizyonları
3. Nihai tasarım ve “üretilebilir” onayı
4. Üretim emrine bağlanma
5. Kalıba yerleşim ve beton dökümü
6. Kür, kalıptan çıkarma, ilk görsel/ölçü kontrol
7. Detaylı kalite kontrol (testler, raporlar)
8. Yard/stok alanına yerleştirme ve lokasyon takibi
9. Sevkiyat planına atanma
10. Araç yükleme ve sahaya gidiş
11. Şantiyede montaj ve son kontrol
12. Olası bakım/onarım ve kullanım ömrü boyunca takip (opsiyonel, şirket stratejisine bağlı)

## 🔄 Sistem İçindeki Yeri

- Üretim, kalite, stok, sevkiyat ve saha modüllerini birbirine bağlayan **en küçük takip birimi**nin hikayesidir.
- Seri numarası, barkod/RFID gibi izleme mekanizmalarının hangi aşamalarda zorunlu olacağını belirler.

## ❗ Riskler

- Gerçek hayattaki istisnaların (kalıptan çıkamayan eleman, şantiyede hasar, geri çağırma) basit gösterilmesi.
- Her firmada farklı olan eleman kimliklendirme sistemlerinin tek modelle çözülebileceğinin varsayılması.

## ❓ Açık Sorular

- Eleman kimliği proje-bazlı mı, fabrika-bazlı mı, global mi olmalı?
- Kalite retlerinde yeni eleman ID’si mi açılır, yoksa aynı ID altında statü mü değişir?

