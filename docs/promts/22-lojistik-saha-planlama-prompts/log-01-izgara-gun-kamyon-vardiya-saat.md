# log-01 — Izgara: gün × (isteğe bağlı vardiya) × kamyon satırları + taşıma zamanı

```
[Buraya 00-ORTAK-BLOK-LOJISTIK-SAHA-PLANLAMA.md bağlamını ekle]
[Buraya 00-ORTAK-BLOK.md + 00b + 00-ORTAK-BLOK-URETIM-UI.md içeriklerini yapıştır veya dosya yollarıyla bağla]

GÖREV: Lojistik modülü “Planlama” sayfasının **iskelet ızgarasını** tasarla (**tek saha**).

## 🔍 Konu tanımı
Kullanıcı; hangi **kamyonla**, hangi **gün** (ve istenirse hangi **gün içi banda**) hangi **taşıma kaleminin** (ürün / sevkiyat satırı) planlandığını görmeli. **Ürünün taşınma zamanı** (saat veya “pencere”) okunabilir olmalı — vardiya üretimdeki gibi zorunlu değil; **zaman bilgisi kartın üzerinde veya hücre içi timeline** ile verilir.

## 🎯 Amaç
Üretim planlama ızgarası ile aynı okunabilirlik: gün başlıkları, sol tarafta **kamyon** listesi (kalıp yerine).

### P0
- **Sütun hiyerarşisi:** Seviye 1 = **takvim günü** (tarih + haftanın günü kısaltması).
- **Seviye 2 (isteğe bağlı toggle):** **Vardiya bandı** — Sabah / Öğle / Gece veya “Gün içi 3 slot” mock; **kapalıyken** sütun sadece günlük tek blok (ama kartta **saat** gösterilir).
- **Sol donmuş kolon:** Kamyon kimliği (plaka veya iç kod + kısa ad); ikincil satır: kapasite ipucu (ör. “max ton / m³” mock).
- **Hücre / zaman:** `(gün, [vardiya], kamyon)` kesişiminde **taşıma kartı**; kartta zorunlu alanlar: **ürün veya yük etiketi**, **planlanan saat veya başlangıç–bitiş penceresi** (mock format: `HH:mm` veya “08:00–10:00”).
- **Sticky:** Yatay kaydırmada gün başlıkları, dikeyde kamyon kolonu sabit (wireframe notu).
- **Bağlam etiketi:** Tek saha adı / proje kısa adı üst bantta (mock).

### P1
- Kamyon satır grupları (ör. “Filo şirket içi” / “Taşeron”).
- Vardiya bandı açık/kapalı — kullanıcı tercihi veya firma ayarı.

### P2
- Yoğun planda sanal scroll veya “sadece o gün seferi olan kamyonları göster”.

### Mock tablolar (zorunlu)
1) **Günler:** 7 satır — `date`, `weekday`, `isNoDispatch` (bool, taşıma yok günü).  
2) **Vardiya bantları (opsiyonel):** 3 satır — `id`, `label`, `order`.  
3) **Kamyonlar:** 10 satır — `truckId`, `plateOrCode`, `capacityHint` (string), `isExternal` (bool).

ÇIKTI: Bilgi mimarisi + bölüm listesi + bileşen listesi + neumorphic özet + P0/P1/P2 + **3–5 UX sorusu**
```
