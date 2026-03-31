# Kalite (QC / laboratuvar) — derinleşme alanı

Bu klasör, **beton ve malzeme kalite süreçlerini** (laboratuvar testleri, numuneler, sonuç girişi, ürün ve reçete ile ilişkilendirme, raporlama ve izlenebilirlik) ürün dilinde tanımlar.

## İlişkiler

- **Üretim:** `docs/12-production-deep-dive/` — emir, santral, reçete seçimi; kalite tarafı **onaylı karışım / test sonuçları** üretir ve üretim bunu tüketir (`05-beton-recete-ve-kalite-veri-sozlesmesi.md`).
- **Firma:** `docs/14-firm-admin-deep-dive/` — firma ve fabrika bağlamı; raporların **hangi firmaya / hangi fabrikaya** ait olduğu zorunludur.
- **Organizasyon:** `docs/02-actors/organizasyon-hiyerarsi-ve-gorev-gorunurlugu.md` — kalite personeli ve onay rolleri.

## Doküman listesi

| Dosya | İçerik |
|--------|--------|
| `00-kapsam-iceri-disari.md` | Kapsam sınırları |
| `01-kalite-domain-ve-kavramlar.md` | Numune, test, rapor, onay |
| `02-test-katalogu-beton-ve-santral.md` | Slump, basınç, nem vb.; santralde kullanılabilir testler |
| `03-numune-ve-test-giris-akisi.md` | Günlük laboratuvar iş akışı |
| `04-urun-recete-emir-iliskisi.md` | Sonuçların ürün / parça / emir / döküm ile bağlanması |
| `05-raporlar-periyodik-ve-teslim.md` | Rapor şablonları, periyodik üretim, teslim / arşiv |
| `06-izlenebilirlik-firma-fabrika-rapor.md` | Hangi bilgi hangi firma/fabrika raporuna yazılır |
| `07-roller-ve-yetki-kalite.md` | Laboratuvar, kalite müdürü, onay |
| `08-entegrasyon-uretim-ve-santral.md` | Santral ekranı ve üretim emri ile veri köprüsü |
| `09-acik-kararlar.md` | Ürün kararları |

## Sonraki adım

`docs/17-ui-quality-prompts/` — UI + mock prompt paketi.
