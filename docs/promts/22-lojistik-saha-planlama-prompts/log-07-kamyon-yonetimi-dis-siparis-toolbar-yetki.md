# log-07 — Kamyon listesi, dış sipariş, toolbar, kayıt, yetki

```
[Buraya 00-ORTAK-BLOK-LOJISTIK-SAHA-PLANLAMA.md bağlamını ekle]
[Buraya 00-ORTAK-BLOK.md + 00b + 00-ORTAK-BLOK-URETIM-UI.md içeriklerini yapıştır veya dosya yollarıyla bağla]

GÖREV: Sol taraftaki **kamyon satırlarını yönet**; eksik kapasitede **dışarıdan kamyon siparişi** (taşeron / kiralık) akışını mock’la; üst **toolbar** (filtre, taslak/yayın); **rol bazlı** düzenleme.

## 🔍 Konu tanımı
Kullanıcı yeni kamyon ekleyebilir, plan dışı bırakılabilir veya listeden kaldırılabilir (iş kuralları mock’ta net). “Eksik gibi” senaryo: planlanan yük > mevcut filo → **dış kamyon talebi** oluşturma (basit form veya modal).

### P0
- **Kamyon ekle:** Plaka/kod, kapasite ipucu, iç mi dış mı (checkbox).
- **Kamyon kaldır / gizle:** Satırda menü (mock — soft delete veya “planlamada gösterme”).
- **Dış sipariş:** “Kapasite yetmiyor” uyarısından kısayol → talep formu: tarih aralığı, tahmini ton/m³, not (mock).
- **Toolbar:** Kaydet taslak, Yayınla (mock), proje/saha adı (tek saha — salt gösterim).

### P1
- Filtre: sadece dış kamyonlar, sadece dolu satırlar.

### P2
- Denetim izi: kim ekledi/sildi (mock alan).

### Mock tablolar (zorunlu)
1) **Kamyonlar:** 10 satır (log-01 ile uyumlu).  
2) **DisKamyonTalepleri:** 3 satır — `requestId`, `dateFrom`, `dateTo`, `volumeRequested`, `status`.

### Rol matrisi (zorunlu çıktı maddesi)
- Lojistik sorumlusu: tam düzenleme.
- Saha koordinatörü: okuma + yorum (mock).
- Admin: kamyon CRUD (mock).

ÇIKTI: Wireframe + P0/P1/P2 + mock tablolar + rol tablosu + UX soruları
```
