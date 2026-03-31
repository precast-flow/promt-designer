# Beton santrali operatör ekranı (özel sayfa)

## Kullanıcı

Beton santrali operatörü — genelde üretim hattından farklı bir istasyon; **dar ekran / hızlı okuma** ihtiyacı yüksek.

## Amaç

“Bugün bana ne dökeceğim?” sorusuna tek ekranda cevap: emir özeti, **m³**, **reçete**, parça/ürün kimliği, güvenlik/onay durumu.

## Görünmesi gereken bloklar (öneri)

1. **Sıradaki iş** (veya seçilen iş): emir no, proje, fabrika.
2. **Parça / ürün kartı:** kod, tip (kiriş, kolon…), adet veya m³, **görsel placeholder** (çizim/thumbnail mock).
3. **Reçete özeti:** seçilen beton tanımı, kritik uyarılar (ör. sıcaklık, özel katkı — metin mock).
4. **Hedef:** planlanan m³, kalan m³, tamamlanan (progress bar).
5. **Aksiyonlar:** Dökümü başlat / Duraklat / Tamamla / Sorun bildir (neumorphic primary tek).
6. **Salt okunur:** Kimin seçtiği reçete, ne zaman kilitlendi (audit özeti — kısa).

## Rol

- Ana etkileşim: **Santral operatörü** yazma yetkisi.
- Üretim şefi: genelde **salt okunur** veya “iptal/eskale” gibi sınırlı.

## Senaryolar

- Sıradaki iş yok → boş durum (inset).
- Reçete uyumsuzluğu → modal uyarı.
- İş yarım kaldı → vardiya değişiminde devretme notu alanı.

## İlişki

`05-beton-recete-ve-kalite-veri-sozlesmesi.md` ile aynı “paket” dilini kullanır.
