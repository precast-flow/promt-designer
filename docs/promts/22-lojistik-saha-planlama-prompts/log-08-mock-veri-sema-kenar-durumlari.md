# log-08 — Mock veri şeması ve kenar durumları

```
[Buraya 00-ORTAK-BLOK-LOJISTIK-SAHA-PLANLAMA.md bağlamını ekle]
[Buraya 00-ORTAK-BLOK.md + 00b + 00-ORTAK-BLOK-URETIM-UI.md içeriklerini yapıştır veya dosya yollarıyla bağla]

GÖREV: Lojistik planlama ekranı için **tutarlı mock şema** ve **kenar durumları** (yükleme, boş ızgara, hata, yetkisiz).

## Şema (özet — implementasyon için referans)
- `SiteContext`: tek saha — `siteId`, `siteName`, `projectShortName`.
- `Truck`: `truckId`, `label`, `capacityHint`, `isExternal`, `visibleInPlanner`.
- `DispatchLoad`: `loadId`, `truckId`, `day`, `windowStart`, `windowEnd`, `productLabel`, `volumeM3`, `status`, `productionOrderRef` (nullable).
- `ExternalTruckRequest`: talep kayıtları (log-07 ile uyumlu).

### P0 kenar durumları
- Hiç kamyon yok → boş durum + “kamyon ekle” CTA.
- Hiç yük yok → ızgara + bilgi bandı.
- API hata → inline hata + yeniden dene.

### P1
- Taslak yayınlandı → salt okunur mod (mock).

### P2
- Çok uzun kamyon listesi → arama kutusu.

### Mock tablolar (zorunlu)
Tüm tabloları tek çıktıda özetle; satır sayıları README ile uyumlu (kamyon 10, yük 15+, gün 7).

ÇIKTI: Şema özeti + kenar durum wireframe notları + P0/P1/P2 + UX soruları
```
