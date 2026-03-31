# Rol bazlı ekran matrisi (üretim odaklı — taslak)

## Amaç

Hangi rolün hangi üretim ekranını göreceği ve **salt okunur / düzenle** ayrımı. İsteğe bağlı **site geneli rol önizleme** (demo): “Şu an X rolü gibi gör” butonu — sadece yetkili kullanıcı + audit notu.

## Örnek matris (doldurulacak)

| Ekran / modül parçası | Üretim şefi | Vardiya amiri | Usta | Santral op. | Planlama | Salt okunur üst (rapor hattı) |
|------------------------|-------------|----------------|------|-------------|----------|-------------------------------|
| Üretim dashboard / özet | Gör + düzenle | Gör + düzenle (vardiya) | Kısıtlı | Özet | Gör + düzenle | Gör |
| Emir listesi / detay | Gör + düzenle | Gör + düzenle | Gör | Gör (kendi emirleri) | Gör + düzenle | Gör |
| Öncelik / sıra raporu | Gör + düzenle | Gör + düzenle | Salt | Hayır | Gör + düzenle | Gör |
| Kalıp tahtası (board) | Gör + düzenle | Gör + düzenle | Gör | Hayır | Gör | Gör |
| Reçete / beton seçimi (emir) | Politikaya göre | Kısıtlı | Hayır | Gör (salt) | Gör + düzenle | Gör |
| Santral operatör ekranı | Gör (salt) | Gör (salt) | Hayır | Gör + düzenle | Gör (salt) | Gör (salt) |
| Arıza / duruş bildirimi | Gör | Gör + düzenle | Oluştur | Gör | Gör | Gör |

> Tablo şirket politikasına göre güncellenir; “Usta sadece kendi istasyonu” gibi kısıtlar satır içi not olarak eklenir.

## Rol önizleme / “Rol gibi gör” (isteğe bağlı)

- **Amaç:** Demo ve eğitim; yönetici veya ürün ekibi farklı rol deneyimini test eder.
- **Kurallar:** Gerçek veri üzerinde mi yoksa sandbox mı? Audit log zorunlu mu?
- **UI:** Üst barda “Önizleme: [Rol] — Çık” şeridi (neumorphic uyumlu tasarımda ayrı inset uyarı bandı).

## Sonraki adım

Senaryo kataloğu (`04-senaryo-katalogu-uretim.md`) ile bu matris satır satır doğrulanır.
