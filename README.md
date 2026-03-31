# Promt Designer

Prekast süreçleri için fikir geliştirme, prompt tasarlama ve dokümantasyon üretimini sistematik hale getiren bir çalışma deposu.

Bu repo, ürün/operasyon ekiplerinin yeni bir ihtiyacı önce netleştirmesi, ardından bu ihtiyaca uygun prompt setlerini üretmesi için ortak bir çerçeve sunar.

## Proje Ne İşe Yarar?

- Prekast iş akışlarına özel fikirleri, kararları ve senaryoları merkezi bir yerde toplar.
- Ekiplerin aynı formatta prompt üretmesini sağlar.
- Prompt çıktılarının zaman içinde takip edilebilir olmasına yardımcı olur.
- Ürün keşfi ile uygulanabilir prompt tasarımını birbirine bağlar.

## Çalışma Prensibi

Bu repoda yeni bir konu açarken önerilen akış:

1. **Önce fikir tartışması** yapılır ve ilgili notlar tartışma klasörüne eklenir.
2. Fikir olgunlaşınca aynı konu için **prompt dosyaları** oluşturulur.
3. Promptlar kullanıldıkça geri bildirimle güncellenir.

Kısaca: **Önce fikir tartışma klasörü, ardından prompt üretimi.**

## Önerilen Klasör Mantığı

- `docs/` altında iş süreci, roller, modüller ve strateji notları tutulur.
- `docs/promts/` altında prompt üretimi ve modül bazlı prompt dosyaları tutulur.

## Katkı Akışı (Önerilen)

- `main` branch'e doğrudan commit yerine branch + PR akışı kullanın.
- Her yeni fikir için küçük ve odaklı bir PR açın.
- PR açıklamasında şu 3 başlık olsun:
  - Problem / ihtiyaç
  - Önerilen yaklaşım
  - Beklenen çıktı (hangi promptlar üretilecek)

## Lisans

Bu proje MIT lisansı ile lisanslanmıştır. Detaylar için `LICENSE` dosyasına bakın.
