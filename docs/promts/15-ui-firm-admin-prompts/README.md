# UI prompt paketi — Firma admin & ilk kurulum (Adım 15)

**Ön koşul:** `docs/14-firm-admin-deep-dive/` analiz dosyaları.  
**Görsel dil:** `docs/10-ui-prototype/prompts/00b-NEOMORPHISM-TAILWIND.md` + `00-ORTAK-BLOK.md`.

## Amaç

- **Firma oluşturma (kayıt / wizard)** ve **firma ayarları** ekranlarını **mock veri** ile tasarlamak.
- Vardiya politikası, fabrika CRUD ve “ayarlara göre render” metinlerinin UI’da **görünür** olması.
- Fabrika bazlı farklılıklar: her fabrikanın ayrı vardiya modeli, kalıp durumu ve çalışan ataması gösterebilmesi.
- Bu paket **platform SaaS süper-admin** ekranlarını kapsamaz (kısa not yeterli).

## Çalıştırma sırası

| Sıra | Dosya |
|------|--------|
| 0 | `00-ORTAK-BLOK-FIRMA-ADMIN-UI.md` |
| 1 | `firm-01-admin-shell-ve-menus.md` |
| 2 | `firm-02-ilk-firma-kurulum-wizard.md` |
| 3 | `firm-03-firma-genel-ayarlar.md` |
| 4 | `firm-04-vardiya-ve-takvim-ayarlari.md` |
| 5 | `firm-05-fabrika-yonetimi-ayarlar-ici.md` |
| 6 | `firm-06-ayar-degisim-ozet-ve-uyari.md` |

Her dosyada **P0 / P1 / P2** + mock tablolar zorunludur.
