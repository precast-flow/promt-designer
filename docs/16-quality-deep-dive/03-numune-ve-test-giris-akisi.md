# Numune ve test girişi — iş akışı

## Günlük laboratuvar döngüsü (öneri)

1. **Numune kaydı oluştur** — kaynak: santral dökümü, sahada alınan numune, şantiye (ileride).
2. **Etiket / barkod** (mock) — numune id.
3. **Test isteği** — hangi testler (katalogdan).
4. **Sonuç girişi** — operatör; tekrar ölçüm / düzeltme versiyonu (audit).
5. **Kalite kontrol** — ikinci kişi onayı (politikaya göre).
6. **Rapor üret** — şablondan PDF mock.
7. **Teslim** — müşteri / proje klasörü / e-posta (mock).

## Çekme (slump) özel akışı

- Hızlı giriş ekranı: emir/döküm seç → slump değeri → kaydet.
- Limit kontrolü: reçete / şartnameden gelen min–max (mock kural).

## Red / yeniden test

- Sonuç limit dışı → `Red` veya `Yeniden numune` akışı; üretim bildirimi (12 ile köprü — ürün kararı).
