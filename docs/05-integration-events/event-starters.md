## 🔍 Konu Tanımı

Sistem içinde önemli bağlamlar arası etkileşimleri tetikleyen temel iş olaylarının (events) kısa listesi.

## 🎯 Amaç

- Event-driven mimari için kritik “başlangıç noktalarını” görünür hale getirmek.
- Süreçler arası bağımlılıkları daha net tartışmak.

## 🧠 Tartışma Alanı

- Hangi olaylar “zorunlu event”, hangileri yalnızca raporlama açısından önemli durum kayıtları?

## 🧱 Yapısal Analiz (Ön Taslak Olay Listesi)

- **Teklif Oluşturuldu**
- **Teklif Güncellendi**
- **Teklif Onaylandı / Reddedildi**
- **Proje Açıldı**
- **Mühendislik Paketi Hazırlandı**
- **Eleman Listesi Onaylandı**
- **Üretim Emri Oluşturuldu**
- **Üretim Emri Başladı / Tamamlandı**
- **Eleman Kalite Onayı Verildi / Ret Edildi**
- **Eleman Yard’a Giriş Yaptı**
- **Sevkiyat Planı Oluşturuldu / Güncellendi**
- **Araç Yüklendi / Tesisten Çıktı**
- **Eleman Şantiyeye Ulaştı**
- **Eleman Montajı Tamamlandı**
- **Hakediş Hesaplandı / Onaylandı**

Detaylı event payload’ları ve kaynak/sink context’ler daha sonra tanımlanacaktır.

## ❗ Riskler

- Çok fazla event tanımlayarak sistemi yönetilemez hale getirmek.

## ❓ Açık Sorular

- Hangi event’ler “near real-time” kritik, hangileri batch/özet bilgi olarak yeterli?

