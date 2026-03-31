# Faz: Üretim derinleşmesi (MVP odağı)

Bu klasör, MVP kapsamında **Üretim (MES / üretim emri / hat–kalıp–vardiya operasyonu)** tarafını **öncelikli** ve **bütüncül** ele almak için açılmıştır.

## İsim / konsept

- Çalışma adı: **Üretim derinleşmesi fazı** (kullanıcı dilinde “Faz 1 üretim”).
- Amaç: Sayfalar, roller, sabah operasyon akışı, beton–ürün–santral el sıkışması ve öncelik/kalıp görünürlüğünü **analiz ve tasarım kararı** seviyesinde netleştirmek.

## Bu fazda nereden besleniyoruz?

- `docs/07-product-strategy/mvp-decisions-reanalysis.md`
- `docs/02-actors/organizasyon-hiyerarsi-ve-gorev-gorunurlugu.md`
- `docs/11-ui-mvp-prototype/` (UI mock genel kurallar; üretim için ayrıntı burada)
- `docs/14-firm-admin-deep-dive/` — fabrika tanımı ve vardiya politikası **firma ayarları** ile yönetilir; üretim buna göre render olur
- `docs/16-quality-deep-dive/` — beton testleri, numuneler ve raporlar; üretim/reçete ile **kalite** köprüsü

## Doküman listesi

| Dosya | İçerik |
|--------|--------|
| `00-kapsam-iceri-disari.md` | Ne yapacağız / yapmayacağız |
| `01-uretim-org-hiyerarsi-roller.md` | Üretim şefi → vardiya amiri → usta / operatör kurgusu |
| `02-gunluk-ve-sabah-akisi.md` | Güne başlama, kısa vadeli plan, durum toplantısı mantığı |
| `03-rol-bazli-ekran-matrisi.md` | Rol × sayfa × salt okunur / düzenle |
| `04-senaryo-katalogu-uretim.md` | Olabilecek tüm iş senaryoları (katalog) |
| `05-beton-recete-ve-kalite-veri-sozlesmesi.md` | Kalite laboratuvarı çıktısı → üretim seçimi (kalite UI yok) |
| `06-beton-santrali-operator-ekrani.md` | Santral operatörü özel görünüm |
| `07-kalip-tahtasi-oncelik-ve-rapor.md` | Kalıp envanteri, öncelik sırası, öneri mantığı |
| `08-acik-kararlar.md` | Netleştirilecek ürün kararları |
| `09-fabrika-ozel-vardiya-kalip-ve-ekip-analizi.md` | Fabrika bazında vardiya, kalıp ve çalışan yönetimi analizi |

## Sonraki adım

- UI prompt paketi: `docs/13-ui-production-prompts/README.md`
