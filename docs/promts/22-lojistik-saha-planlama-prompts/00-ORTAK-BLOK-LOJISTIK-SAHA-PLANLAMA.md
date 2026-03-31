# 00 — Ortak blok — Lojistik (saha) planlama prompt paketi

Her `log-XX` dosyasını çalıştırmadan önce aşağıdaki blokları **üst üste** bağla:

1. `docs/10-ui-prototype/prompts/00-ORTAK-BLOK.md` — tam metin (ROL, kod politikası, görsel dil, çıktı formatı).
2. `docs/10-ui-prototype/prompts/00b-NEOMORPHISM-TAILWIND.md` — görsel kurallar.
3. `docs/13-ui-production-prompts/00-ORTAK-BLOK-URETIM-UI.md` — üretim özeti (12 analiz, fabrika bağlamı, roller); **lojistik ekranı üretim fabrikası değil** ama görsel dil ve mock yoğunluğu için referans.

**Bu pakete özel:**

- Ekran türü: **2D planlama ızgarası** — üretim “Planlama / Tasarım” ile **aynı UX ailesi** (Excel benzeri; üstte zaman, solda kaynak satırları).
- **Kaynak ekseni:** Kalıp **değil**; **kamyon** (taşıyıcı). Satırlar dinamik: yeni kamyon eklenebilir, kullanılmayan/plan dışı kamyon gizlenebilir veya listeden çıkarılabilir (mock davranış net tanımlanır).
- **Zaman ekseni:** Üstte **günler** (takvim sütunları). Alt seviye: isteğe bağlı **vardiya bandı** (Sabah / Öğle / Gece) — fabrika üretimindeki gibi **olabilir veya kapatılabilir**; asıl vurgu **hangi ürünün ne zaman taşınacağı** (tarih + saat veya gün içi zaman penceresi).
- **Kapsam (MVP bu paket):** **Tek şantiye / tek saha bağlamı** — çok şantiye seçimi P2 veya sonraki iterasyon.
- **Saha montaj planı** (hangi ürün ne zaman monte edilecek): **bu pakette yok** — ayrı modül olarak bilinçli ertelendi; sadece **taşıma / lojistik yükleme planı**.

**Standart çıktı** (00-ORTAK ile uyumlu, ek madde):

9) **Rol matrisi:** lojistik sorumlusu / saha koordinatörü / operasyon için bu ekranda hangi aksiyonlar açık (tek tablo).
