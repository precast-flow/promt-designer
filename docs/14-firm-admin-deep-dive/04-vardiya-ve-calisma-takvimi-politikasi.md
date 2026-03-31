# Vardiya ve çalışma takvimi politikası

## Kullanıcı sorularına karşılık

- **“Firmada vardiya usulü var mı?”** → Evet/Hayır veya model seçimi (tek vardiya = fiilen “sadece gündüz” gibi davranabilir).
- **“Gece–gündüz var mı?”** → Ayrı bir flag veya vardiya modelinin parçası (örn. 3 vardiya + gece).

## Önerilen model (ürün)

| Seçenek | Anlam | Üretim ekranına etki |
|---------|--------|----------------------|
| **Gündüz-only** | Tek çalışma dilimi (ör. 08:00–18:00) | Vardiya filtresi gizli veya sabit |
| **İki vardiya** | Gündüz / Akşam | Vardiya seçici 2 seçenek |
| **Üç vardiya** | 8 saatlik döngü | Üretim 12’deki vardiya ile uyumlu |
| **Gece–gündüz sürekli** | Hafta içi 7/24 veya belirli günler | Takvimde gece slotları |

## Veri yapısı (kavramsal)

- `Vardiya Politikası`: enum veya yapılandırılmış tablo (vardiya adı, başlangıç, bitiş).
- Fabrika bazında override: İstanbul fabrika 2 vardiya, Ankara 1 vardiya (artık aktif analiz konusu; `12-production-deep-dive/09` ile birlikte ele alınır).

## Render kuralları

- Vardiya filtresi **göster/gizle**: politika tek vardiya ise gizlenir.
- Dashboard “bugünkü vardiya” varsayılanı: ilk aktif vardiya veya kullanıcı tercihi.
