# Fabrika yönetimi (firma ayarları içinde)

## Amaç

`12-production-deep-dive` ve `11` MVP’deki **fabrika seçici** için kaynak: **firma tanımı altında** birden fazla fabrika.

## Alanlar (fabrika kaydı)

- Kod (kısa, benzersiz — örn. `IST-HAD`)
- Ad
- Adres (şehir, açık adres)
- Aktif / pasif
- Varsayılan fabrika (boolean, tek seçili)
- Vardiya modeli (firma default veya fabrika override)
- Kalıp envanteri özeti (adet)
- Çalışan sayısı / ekip ataması özeti

## İş kuralları

- En az **bir** aktif fabrika kalmalı (son fabrika pasif edilemez).
- Pasif fabrika: yeni emir atanamaz; geçmiş veri salt okunur.
- Fabrika pasifleştirilmeden önce aktif çalışan/aktif kalıp bağımlılık kontrolü gerekir (uyarı).

## İlişki

- Kullanıcı–fabrika erişimi (`mvp-04` ve org dokümanları) ile birleşir: kullanıcı hangi fabrikalara erişebilir.
- Fabrika özel vardiya/kalıp/ekip analizi: `docs/12-production-deep-dive/09-fabrika-ozel-vardiya-kalip-ve-ekip-analizi.md`.
