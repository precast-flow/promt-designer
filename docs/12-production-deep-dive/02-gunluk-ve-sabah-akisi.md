# Günlük ve sabah üretim akışı (konsept)

## Amaç

“Sabah üretim şefi geldi…” senaryosunu sistem davranışına çevirmek: hangi ekranlar sırayla açılır, hangi veri **dün akşamdan** gelir, hangisi **bu sabah** üretilir.

## Önerilen sabah döngüsü (yüksek seviye)

1. **Bağlam seçimi:** Kullanıcı fabrika + (varsa) aktif vardiya seçer.
2. **Durum özeti (dashboard üretim widget):** Dün tamamlanmayan, bugün planlı, geciken emirler.
3. **Kalıp / hat durumu:** Hangi kalıplar dolu, hangi hat müsait — *tek bakış* (board).
4. **Öncelik kararı:** Bekleyen işler listesinden sıralama / kilitleme (şef veya yetkili rol).
5. **Atama:** Vardiya amiri veya şef, işleri hat/kalıp/ekibe bağlar.
6. **Beton emri hazırlığı:** Seçilen reçete + m³ + zaman penceresi → santral bilgisi (ayrı ekran veya entegrasyon öncesi “gönderilecek paket”).
7. **Üretim yürütme:** Başlat / ara / tamamla / arıza — saha ekranları.
8. **Kapanış:** Vardiya raporu (özet) — ileride detay.

## Kim ne zaman müdahale eder?

| Olay | Tipik rol |
|------|-----------|
| Öncelik sırasını değiştir | Üretim şefi (veya yetki verilmiş vardiya amiri) |
| Kalıp ataması yap | Vardiya amiri |
| Emir satırında reçete seçimi | Üretim planlamacı / şef (politikaya göre) |
| Santrale “döküm” onayı | Santral operatörü + çift onay ihtiyacı (ürün kararı) |

## MVP sınırı

İlk sürümde **tam otomatik optimizasyon** (AI ile sıra) şart değil; **manuel sıra + görsel board** yeterli olabilir. Optimizasyon P2 olarak işaretlenir.
