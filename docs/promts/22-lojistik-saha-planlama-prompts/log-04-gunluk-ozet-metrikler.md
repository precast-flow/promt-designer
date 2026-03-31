# log-04 — Günlük özet metrikler (sefer, hacim, ürün)

```
[Buraya 00-ORTAK-BLOK-LOJISTIK-SAHA-PLANLAMA.md bağlamını ekle]
[Buraya 00-ORTAK-BLOK.md + 00b + 00-ORTAK-BLOK-URETIM-UI.md içeriklerini yapıştır veya dosya yollarıyla bağla]

GÖREV: Izgara altında veya üst toolbar yakınında **gün bazlı özet şeridi**: o gün kaç sefer, toplam m³, önemli ürün sayıları.

## 🎯 Amaç
Üretim `plan-04` ile paralel: yöneticiye bir bakışta “bu gün taşıma yükü”.

### P0
- Seçili gün veya görünür hafta için: **toplam sefer**, **toplam m³** (mock), **aktif kamyon sayısı**.

### P1
- Günlük breakdown — mini tab veya chip satırı.

### P2
- Önceki haftaya göre sapma yüzdesi (mock).

### Mock tablolar (zorunlu)
1) **GunlukOzet:** 7 satır — `date`, `tripCount`, `totalM3`, `truckCountActive`.

ÇIKTI: Wireframe + P0/P1/P2 + mock + UX soruları
```
