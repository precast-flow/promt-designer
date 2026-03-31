# Beton reçetesi ve kalite veri sözleşmesi (kalite UI yok — üretim odaklı)

## Problem cümlesi

Her ürün farklıdır; **hangi beton karışımının** kullanılacağı kalite laboratuvarı süreçlerinde **tanımlanır/onaylanır**; **üretim emri** aşamasında ise **hangi onaylı karışımın** hangi parçaya uygulanacağı **üretim sorumlusu** tarafından seçilir ve **beton santraline** giden bilgi paketi oluşur.

## Bu fazda bilinçli sınır

- **Kalite modülü ekranları** (test, numune, laboratuvar formları) **tasarlanmaz**.
- Varsayım: Sistemde **onaylı reçete / beton sınıfı havuzu** vardır (kalite tarafında üretilmiş veri).

## Veri nesneleri (kavramsal)

| Kavram | Açıklama |
|--------|----------|
| **Beton tanımı / reçete** | Kimlik, ad, sınıf (C30/37 vb.), onay durumu, geçerlilik |
| **Ürün / eleman satırı** | Parça tipi, projeye bağlı, teknik gereksinim |
| **Üretim emri satırı** | Hangi eleman(lar), miktar, hedef tamamlanma |
| **Karışım ataması** | Emir satırı veya eleman bazında `beton_tanim_id` seçimi |
| **Santral gönderi paketi** | Emir no, parça özeti, m³ (veya batch), reçete id, zaman damgası, isteğe bağlı görsel referanslar |

## İş kuralları (taslak)

1. Üretim, **sadece onaylı** reçeteler arasından seçim yapabilir (liste filtreli).
2. Reçete değişimi, emir “kilitli” iken kısıtlanabilir (politika).
3. Santral ekranı, **gönderilen paketin** bir özetini salt okur; operatör kendi onayıyla dökümü başlatır.

## Üretim ekranında görünmesi gerekenler (minimum)

- Seçili reçetenin **kısa özeti** (ad + sınıf + uyarı notu).
- **Hedef hacim** (m³) veya batch sayısı.
- **Hangi ürün/parça** için olduğu (kod, proje, çizim thumb mock).

## Kalite ile entegrasyon (ileride)

Laboratuvar ekranları geldiğinde: reçete havuzu buraya **yazılır**; üretim tarafı API ile aynı listeyi okur. Şimdilik **mock liste** yeterli.

**Derinleşme:** `docs/16-quality-deep-dive/` (testler, numuneler, raporlar) ve `docs/17-ui-quality-prompts/`.
