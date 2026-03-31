## 🔍 Konu Tanımı

Farklı bounded context’ler arasında akan birkaç temel iş akışının (örneğin Teklif → Proje → Üretim → Sevkiyat) yüksek seviye şematik tarifi.

## 🎯 Amaç

- En kritik 3–5 akışı görünür kılarak hem ürün tasarımına hem de mimariye yön vermek.

## 🧠 Tartışma Alanı

- Hangi akışların “uçtan uca otomasyon”, hangilerinin “yarı manuel onaylı” kalması gerektiği.

## 🧱 Yapısal Analiz (Ön Taslak Akış Örnekleri)

- **Akış 1:** Teklif Onayı → Proje Açılışı → Mühendislik → Üretim Emri
- **Akış 2:** Üretim Tamamlandı → Kalite Onayı → Yard Girişi → Sevkiyat Planlama
- **Akış 3:** Sevkiyat Çıkışı → Şantiyeye Varış → Montaj Tamamlandı → Hakediş

Detaylı adımlar ve context etkileşimleri ileride eklenecektir.

## ❗ Riskler

- Çok fazla varyantı tek akış altında toplamaya çalışarak modelin karmaşıklaşması.

## ❓ Açık Sorular

- Hangi akış MVP’de eksiksiz olmalı, hangileri daha sonraki fazlara bırakılabilir?

