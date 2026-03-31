# Ürün, reçete ve üretim emri ile ilişkilendirme

## Amaç

Test sonuçlarının **anlamlı** olması için bağlantılar:

| Bağlantı | Zorunluluk | Açıklama |
|----------|------------|----------|
| **Firma** | Evet | Tenant |
| **Fabrika** | Evet | Hangi santral / hangi laboratuvar |
| **Beton tanımı / reçete** | Çoğu senaryoda evet | Hangi karışımın testi |
| **Ürün / eleman (parça)** | İstenir | Prefabrik parça kodu |
| **Üretim emri / döküm lotu** | Önerilir | Santral ve üretim ile köprü |
| **Proje / müşteri** | Rapor için sık | Dış rapor başlığı |

## Üretim tarafı ile tutarlılık

- Üretim emrinde seçilen reçete ile numune reçetesi **aynı kimlik** üzerinden eşleşebilir.
- Çelişki: emirde C30, testte farklı reçete seçilmiş — uyarı kuralı (ürün kararı).

## Rapor başlığında görünen bilgi

- Firma unvanı, fabrika, proje adı, parça listesi özeti, emir no, tarih aralığı — `06-izlenebilirlik` ile uyumlu.
