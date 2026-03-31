# Roller ve yetki (kalite)

## Örnek roller

- Laboratuvar teknisyeni (sonuç girişi)
- Kalite müdürü / sorumlusu (onay, rapor kilidi)
- Üretim temsilcisi (salt okunur veya sınırlı giriş — firma politikası)
- Proje müşteri temsilcisi (rapor indirme — harici rol ileride)

## İzin örnekleri (atomik)

- `kalite.numune.olustur`
- `kalite.sonuc.gir`
- `kalite.sonuc.onayla`
- `kalite.rapor.olustur`
- `kalite.rapor.teslim`
- `kalite.rapor.sil` (tehlikeli)

## Organizasyon rapor hattı

- Üst, astın bekleyen onaylarını görebilir (salt) — `organizasyon-hiyerarsi` ile uyum.
