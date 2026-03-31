## 🔍 Konu Tanımı

Modüller (bounded context’ler) arası ilişkilerin ve bağımlılık tiplerinin yüksek seviye haritası.

## 🎯 Amaç

- “Hangi modül hangi modüle neden bağlı?” sorusunu netleştirip tasarım risklerini görünür kılmak.
- MVP ve faz planında bağımlılık kaynaklı darboğazları erkenden yakalamak.

## 🧠 Tartışma Alanı

- Bağımlılıkların türleri: veri okuma, veri sahipliği, event tüketimi, süreç onayı, entegrasyon köprüsü.
- Modüller arası bağın sıkılığı: gevşek (event) vs sıkı (senkron çağrı).

## 🧱 Yapısal Analiz

### Bağımlılık Tipleri (Tanımlar)

- **D1 – Referans bağımlılığı:** Bir modül diğer modülün kimliklerini (ID) referans alır.
- **D2 – Veri okuma bağımlılığı:** Diğer modülün sahip olduğu veriyi okur (read-model).
- **D3 – Event bağımlılığı:** Diğer modülün yayımladığı event’leri tüketir.
- **D4 – Süreç bağımlılığı:** Bir iş adımı diğer modülün onayı/çıktısı olmadan ilerleyemez.
- **D5 – Entegrasyon bağımlılığı:** Dış sistemlere erişim tek bir modül üzerinden yapılır (anti-corruption / gateway).

### Örnek İlişki Haritası (İlk Taslak)

- **Estimating & Quoting → Project Management:** D4 (teklif onayı → proje açılışı)
- **Engineering → Production/MES:** D4 (üretilebilir tasarım olmadan üretim emri)
- **Production/MES → Quality:** D3/D4 (üretim tamamlandı → kalite onayı)
- **Quality → Yard/Inventory:** D4 (onay olmadan yard’a giriş)
- **Yard/Inventory → Dispatch/Logistics:** D2/D4 (sevkiyat için uygun eleman seçimi)
- **Dispatch/Logistics → Field/Site:** D3 (araç çıktı / teslimat → saha kabul)
- **Field/Site → Project Management:** D3/D4 (montaj ilerlemesi → proje ilerleme/hakediş)

Bu harita, gerçek use case’ler yazıldıkça revize edilecektir.

## ❗ Riskler

- Yanlış sahiplik kararları nedeniyle “döngüsel bağımlılıklar” oluşması.

## ❓ Açık Sorular

- Hangi bağımlılıklar senkron olmalı, hangileri event ile asenkron olmalı?

