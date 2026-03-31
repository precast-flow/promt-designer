# Üretim senaryo kataloğu (olası tüm ana durumlar)

Her satır: tetikleyici → kim müdahale eder → hangi ekran → beklenen sonuç (mock mantığı).

## A) Emir yaşam döngüsü

1. **Emir oluşturuldu, planlandı** — Planlama/şef — emir listesi — durum “Planlandı”.
2. **Emir vardiyaya alındı** — Vardiya amiri — vardiya board — “Bugünün işi”.
3. **Kalıp atandı** — Vardiya amiri — kalıp tahtası — kalıp durumu “Dolu/Planlı”.
4. **Üretim başlatıldı** — Usta/operatör — istasyon ekranı — durum “Üretimde”.
5. **Ara / mola** — Usta — aynı ekran — durum “Duraklatıldı”.
6. **Tamamlandı** — Usta + (gerekirse kalite baypas bu fazda yok) — durum “Tamamlandı”.
7. **Emir iptal / revizyon** — Şef/planlama — emir detay — yeni revizyon emri veya iptal nedeni.

## B) Beton / santral

8. **Reçete seçimi yapıldı** — Yetkili rol — emir satırı — santrale gidecek paket hazır.
9. **Santral döküm başladı** — Santral op. — santral ekranı — m³ sayaç mock.
10. **Reçete uyumsuzluğu şüphesi** — Santral op. / şef — uyarı modal — üretim durdur veya onay ile devam (politika).

## C) Kalıp ve kapasite

11. **Kalıp çakışması** — Vardiya amiri — board — alternatif kalıp veya sıra kaydırma.
12. **Kalıp arızası** — Usta — arıza formu — emir bloke.
13. **Hat kapasitesi doldu** — Şef — öncelik raporu — sıra değişimi.

## D) Öncelik ve raporlama

14. **Bekleyen işler sıralandı** — Şef — öncelik ekranı — sıra numarası güncellendi.
15. **Gecikme uyarısı** — Sistem (mock) — dashboard — “X gündür bekliyor”.

## E) Organizasyon ve görünürlük

16. **Üst yönetici astın geciken emrini görür** — Rapor hattı — ast ekranı salt okunur — müdahale yok.

## F) Rol önizleme (isteğe bağlı)

17. **Demo kullanıcı vardiya amiri gibi görüntüler** — Ürün yöneticisi — tüm site — salt mı tam mı (ayar).

---

Bu katalog UI prompt’larında **tek tek ekran** olarak parçalanır; eksik senaryo kalırsa buraya ek satır açılır.
