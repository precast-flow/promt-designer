# log-02 — Taşıma yükü: süre, span, çakışma, kapasite

```
[Buraya 00-ORTAK-BLOK-LOJISTIK-SAHA-PLANLAMA.md bağlamını ekle]
[Buraya 00-ORTAK-BLOK.md + 00b + 00-ORTAK-BLOK-URETIM-UI.md içeriklerini yapıştır veya dosya yollarıyla bağla]

GÖREV: Aynı kamyon veya aynı zaman penceresinde **çakışan** taşımaları ve **yük / süre** kısıtlarını göster.

## 🔍 Konu tanımı
Bir kamyon aynı anda iki farklı yükleme **çakışmasın**; aynı gün içinde ardışık seferler **mantıklı sıra** ile görünsün. Üretimdeki “çok günlük span” benzeri: taşıma **birden fazla hücreyi** kaplayabiliyorsa görsel **birleşik blok** veya bağlayıcı çizgi (mock seç).

## 🎯 Amaç
Planlayıcı riski düşük: çakışma uyarısı, kapasite aşımı ipucu.

### P0
- **Çakışma kuralı (mock):** Aynı `truckId` + örtüşen zaman aralığı → **uyarı rengi** veya ikon.
- **Yük göstergesi:** Kart üzerinde ton veya m³ (mock sayı); kapasite üstü için uyarı (P1 detay).
- **Gün içi sıra:** Aynı kamyon satırında birden fazla kart — dikey stack veya küçük zaman çizelgesi (wireframe).

### P1
- Kamyon bazlı “boşluk” önerisi (ör. “10:00–12:00 boş” metin mock).

### P2
- Otomatik öneri: “Bu yükü şu kamyona kaydır” (salt metin öneri, gerçek optimizasyon yok).

### Mock tablolar (zorunlu)
1) **Taşıma kalemleri:** en az 15 satır — `loadId`, `truckId`, `day`, `windowStart`, `windowEnd`, `productLabel`, `volumeM3`, `status`.  
2) **Çakışma örneği:** en az 2 satır bilinçli çakışma (test senaryosu notu).

ÇIKTI: Wireframe notları + P0/P1/P2 + mock tablolar + UX soruları
```
