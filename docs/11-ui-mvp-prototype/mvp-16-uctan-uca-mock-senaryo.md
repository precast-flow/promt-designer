# mvp-16 — Uçtan uca mock senaryo (P0 + P1 parçaları)

```
[Buraya 00-ORTAK-BLOK-MVP-UI.md içeriğini yapıştır]

GÖREV: Tek senaryoda tüm MVP ekranlarını sırayla gez; her adımda mock veri güncellenmiş gibi göster.

SENARYO ADIMLARI (minimum 18 adım):

1. Yönetici giriş → fabrika seçer (IST-HAD).
2. Rol oluşturur / izin atar (mock).
3. Onay akışı şablonu: Teklif için 3 adım (rol + eşik mock) kaydeder.
4. Kullanıcı oluşturur (Satış rolü, tek fabrika).
5. Satış kullanıcısı ile giriş (rol değişimi mock).
6. Müşteri oluşturur.
7. Teklif oluşturur, kalemler doldurur, onaya gönderir.
8. Onaycı 1 onaylar (mock kullanıcı değiştir veya aynı oturumda rol notu).
9. Onaycı 2 onaylar; tutar eşiği geçerse 3. adım mock.
10. Proje açılır (otomatik veya buton — not).
11. Mühendislik: dosya yüklenmiş gibi 2 satır + manuel alan doldurulur, üretime hazır.
12. Üretim emri oluşturulur, başlatılır.
13. Kalite sekmesi: ölçü girilir, onaylanır.
14. Yard’a lokasyon atanır, sevkiyata hazır işaretlenir.
15. Sevkiyat çıkışı oluşturulur, onay akışı (sevkiyat şablonu mock) işletilir.
16. Saha web: teslim alındı.
17. Dashboard KPI güncellenmiş gösterilir.
18. Bildirim listesi “tamamlandı” mock.
19. (Birim iş) Tahir, **Üzerime atanan (birim)** sekmesinde kendi birimine düşen iş emirlerini görür; **Atadığım işler** ile biriminin çıkardığı emirleri takip eder (mock). Kişi bazlı görev panosu yok — operasyon birim üzerinden.

Her adım için: **ekran adı**, **basılan kontrol**, **P0/P1**, **mock state değişimi** (tek cümle).

ÇIKTI: Tablo veya numaralı liste + eksik kalan tek risk maddesi + UX soruları
```
