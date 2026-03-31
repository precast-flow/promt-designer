## 🔍 Konu Tanımı

Temel verilerin (teklif, proje, eleman, üretim emri, sevkiyat vb.) hangi bounded context’te “sahip” olduğu ve zaman içindeki yaşam döngüsünün kısa haritası.

## 🎯 Amaç

- Veri kopyalarının ve tutarsızlıkların önüne geçmek için hangi verinin “tek gerçek kaynak” olduğunu netleştirmek.
- Event-driven entegrasyon tasarımına zemin sağlamak.

## 🧠 Tartışma Alanı

- Hangi veriler tam olarak bu sistemde tutulmalı, hangileri ERP gibi dış sistemlerden sadece okunmalı?

## 🧱 Yapısal Analiz (Ön Taslak)

- **Teklif:** Sales & Estimating context tarafından sahiplenilir; ERP ile fiyatlama/finans entegrasyonu olabilir.
- **Proje:** Project Management context ana sahip; diğer context’ler referans alır.
- **Eleman ve Eleman Tipi:** Engineering + Production context’leri arasında ortak ilgi alanı; sahiplik kararı kritik.
- **Üretim Emri:** Production Planning & MES context sahip; kalite ve yard context’leri tüketir.
- **Kalite Kaydı:** Quality context sahip; raporlama context’i tüketir.
- **Yard Lokasyon ve Stok:** Yard / Inventory context sahip; sevkiyat ve saha context’leri tüketir.
- **Sevkiyat Planı:** Dispatch / Logistics context sahip; saha ve proje context’i tüketir.

Detaylı lifecycle diyagramları sonraki aşamada tanımlanacaktır.

## ❗ Riskler

- ERP ile çakışan veri sahipliği kararlarının ileride entegrasyonu zorlaştırması.

## ❓ Açık Sorular

- Fiyat ve maliyet kalemleri hangi sistemde “gerçek” olmalı: ERP mi, bu platform mu?

