# Kapsam: içeri / dışarı (üretim derinleşmesi fazı)

## Bu fazda YAPACAĞIMIZ

1. **Üretim operasyonunun** tamamını ürün diliyle tarif etmek: emir, hat, vardiya, kalıp, sıra, durum, öncelik.
2. **Org hiyerarşisini** üretim sahasına indirmek: üretim şefi → vardiya amirleri → ustalar/operatörler (firma dilinize göre isimler netleştirilebilir).
3. **Rol bazlı ekran matrisi:** hangi rol hangi sayfayı görür, neyi değiştirir, neyi salt okur; isteğe bağlı **rol önizleme / rol değiştirme** (demo) notu.
4. **Günlük ve “sabah” akışı:** ilk giren kimin neyi kontrol ettiği, planın nasıl kilitlendiği veya güncellendiği.
5. **Beton / reçete seçimi:** Kalite laboratuvarında **onaylı/tanımlı beton sınıfları veya reçeteler** üretim emrinde **hangi ürün için hangi karışım** olacağının üretim tarafından seçilmesi; **santrale giden bilgi paketi** (metin olarak veri sözleşmesi).
6. **Beton santrali operatörü** için ayrı ekran: hangi emir, kaç m³, hangi karışım, hangi ürün görselleri/parça bilgisi (mock mantığı).
7. **Kalıp tahtası / board:** Hangi kalıpta ne iş var, sıra, durum, atama; **bekleyen işler öncelik raporu** (öneri sırası + gerekçe alanı).
8. **Senaryo kataloğu:** üretimde oluşabilecek tüm anlamlı durumlar (gecikme, kalıp arızası, reçete değişimi vb.) listesi.
9. **Fabrika özel işletim:** her fabrikanın vardiya modeli, kalıp envanteri ve çalışan/ekip atamaları farklı olabilir; bu farklılıkların analiz edilmesi.

## Bu fazda YAPMAYACAĞIMIZ (bilinçli sınır)

1. **Kalite modülü ekranlarının** detaylı tasarımı (laboratuvar test formları, numune akışı, ret/onay süreçleri) — **bu fazda yok**.
2. **Mühendislik / BIM** derinliği (sadece üretim emrine düşen çıktıların “var olduğu” varsayılır).
3. **Gerçek santral PLC / entegrasyon protokolü** seçimi — sadece **hangi verinin gideceği** tanımı.
4. **Global müşteri admin** (modül lisansı) — dokunulmaz.
5. **Native mobil** saha uygulaması — web/ mock odak; mobil sonraya bırakılır.

## Kalite ile sınır (önemli)

- Kullanıcı betonun **laboratuvarda nasıl üretildiğini** bu fazda ekranlamıyoruz.
- Ancak üretim emrinde **“hangi onaylı karışım/reçete kullanılacak”** seçiminin **kalite tarafından önceden tanımlanmış havuzdan** gelmesi **iş kuralı** olarak yazılır (veri sözleşmesi: `05-beton-recete-ve-kalite-veri-sozlesmesi.md`).

## Çıktı tanımı

Bu klasördeki dosyalar **kod içermez**; ürün, süreç ve ekran kararları için referanstır. UI üretimi için ayrı prompt seti açılacaktır.
