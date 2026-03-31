# Üretim org hiyerarşisi ve roller (öneri iskelet)

## Amaç

Üretim sahasında **rapor hattı (`reports_to`)** ile birlikte düşünülebilen, ayrıca **operasyonel hiyerarşi** (kim kimin vardiyasını/planını yönetir) için ortak bir dil oluşturmak.

> Not: Aşağıdaki unvanlar örnektir; firmaya göre birleşebilir veya farklı adlar alır.

## Önerilen katmanlar

| Katman | Örnek unvan | Tipik sorular |
|--------|-------------|----------------|
| **Stratejik / günlük plan** | Üretim Müdürü / Fabrika Müdürü | Kapasite, hedef, çok fabrika özet (ileride) |
| **Taktik / vardiya** | Üretim Şefi | Bugünün planı, öncelik, kalıp–hat dengeleme, gecikme |
| **Vardiya operasyon** | Vardiya Amiri | O vardiyada hat/kalıp ataması, iş başlat/durdur, usta koordinasyonu |
| **Uygulama** | Usta / Kalıpçı / Operatör | İş istasyonu ekranı, adım tamamla, arıza bildir |
| **Santral** | Beton Santrali Operatörü | Emir + m³ + reçete + döküm kaydı (ayrı ekran) |
| **Destek** | Kalite (bu fazda UI yok) | Reçete havuzu, test sonucu — üretime veri |

## RBAC vs operasyonel hiyerarşi

- **RBAC:** Menü ve aksiyon (ör. `uretim.emri.olustur`).
- **Org `reports_to`:** Üstün astın işlerini izlemesi (salt okunur).
- **Operasyonel hiyerarşi:** “Bu vardiyayı şef onaylar”, “bu kalıp atamasını vardiya amiri yapar” — **iş kuralı** ve ekran yetkisi birlikte tanımlanır.

## Bu faz için netleştirilecek

1. Sizin fabrikada **kaç seviye** zorunlu? (2: şef + usta mı, 3: şef + vardiya + usta mu?)
2. “Vardiya amiri” her hatta mı, yoksa bölge bazlı mı?
3. Santral operatörü üretim şefine mi raporlar, ayrı bir “malzeme” hattına mı bağlıdır?

Bu soruların yanıtı `03-rol-bazli-ekran-matrisi.md` ve `08-acik-kararlar.md` ile kapanır.
