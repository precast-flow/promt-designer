# UI prompt paketi — Üretim derinleşmesi (Adım 13)

**Ön koşul:** `docs/12-production-deep-dive/` analiz dokümanları okunmuş olmalı.  
**Görsel dil:** `docs/10-ui-prototype/prompts/00b-NEOMORPHISM-TAILWIND.md` + `00-ORTAK-BLOK.md`.  
**Tekrar kullanılabilir veri kabuğu:** `docs/10-ui-prototype/prompts/00c-DINAMIK-VERI-GORUNUMU-SABLONU.md` (ikon / liste / tablo / galeri); ilk uygulama `prod-04`.

## Amaç

Sadece **frontend + mock veri** ile üretim modülüne ait ekranları **rol bazlı** tasarlamak. Kalite laboratuvarı ekranları **yok**; beton sadece **seçilebilir onaylı reçete havuzu** olarak mock listelenir. Fabrika bazlı vardiya/kalıp/ekip farklılıkları için `prod-08` eklenmiştir.

## Çalıştırma sırası

| Sıra | Dosya | Odak |
|------|--------|------|
| 0 | `00-ORTAK-BLOK-URETIM-UI.md` | Her prompt öncesi yapıştır |
| 0c | `../10-ui-prototype/prompts/00c-DINAMIK-VERI-GORUNUMU-SABLONU.md` | `prod-04` öncesi zorunlu; diğer liste ekranlarında tekrar kullan |
| 1 | `prod-01-uretim-ozet-dashboard.md` | Şef/vardiya sabah özeti |
| 2 | `prod-02-emir-listesi-ve-detay.md` | Emir CRUD görünümü mock |
| 3 | `prod-03-kalip-tahtasi-board.md` | Kalıp × iş kartları |
| 4 | `prod-04-bekleyen-is-oncelik-raporu.md` | Sıralama, gecikme |
| 5 | `prod-05-beton-recete-secimi.md` | Emirde karışım seçimi → santral paketi özeti |
| 6 | `prod-06-beton-santrali-operator.md` | Santral ekranı |
| 7 | `prod-07-rol-bazli-gorunum-ve-onizleme.md` | Matris + rol gibi gör |
| 8 | `prod-08-fabrika-ozel-vardiya-kalip-ve-ekip-komutu.md` | Fabrika özel vardiya + kalıp + ekip yönetimi |

Her dosyada **P0 / P1 / P2** ve **mock tablolar** zorunludur.
