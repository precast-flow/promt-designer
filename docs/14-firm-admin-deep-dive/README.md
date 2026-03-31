# Firma / tenant yönetimi — derinleşme alanı

Bu klasör, uygulamayı **uçtan uca kullanacak beton prefabrik firmasının** sistemde **oluşturulması**, **ilk kurulumu** ve **firma ayarları** üzerinden uygulama davranışının **nasıl şekilleneceği** konusunda analiz ve kararları toplar.

## İlişki

- **Global SaaS operatör admin** (tüm müşteri firmalarını yöneten panel) bu pakette **derin UI üretmez**; “firma admin” tarafı, **tek firma bağlamında** veya “ilk firma oluşturma” akışında tasarlanır.
- `docs/12-production-deep-dive/` içindeki fabrika kavramı burada **firma ayarlarından yönetilen** alt varlık olarak konumlanır (`05-fabrika-yonetimi-firma-ayarlari.md` ↔ üretimdeki fabrika seçici).

## Doküman listesi

| Dosya | İçerik |
|--------|--------|
| `00-kapsam-iceri-disari.md` | Ne yapıyoruz / yapmıyoruz |
| `01-firma-kimligi-ve-tenant-kavrami.md` | Firma kaydı, kimlik alanları |
| `02-ilk-kurulum-ve-onboarding-akisi.md` | İlk firma / ilk admin akışı |
| `03-firma-ayarlari-alan-katalogu.md` | Ayarlar sayfası alanları (geniş liste) |
| `04-vardiya-ve-calisma-takvimi-politikasi.md` | Gündüz-only, gece-gündüz, vardiya sayısı |
| `05-fabrika-yonetimi-firma-ayarlari.md` | Fabrika ekle/çıkar, kod, adres, vardiya/kalıp/çalışan özeti |
| `06-uygulama-davranisina-etki-render-kurallari.md` | Ayarlara göre **ne nasıl render edilir** |
| `07-acik-kararlar.md` | Netleştirilecek ürün kararları |

## Sonraki adım

`docs/15-ui-firm-admin-prompts/` — UI + mock prompt’ları.
