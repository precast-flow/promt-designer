# UI prompt paketi — Lojistik (saha) planlama (Adım 22 — gün × kamyon × taşıma zamanı)

**Konum:** Lojistik modülü — **tek saha** bağlamında planlama ekranı: üstte **günler**, solda **kamyon** satırları; hücrelerde **taşınacak ürün / yük** kartları; **ne zaman yüklenecek / yola çıkacak** bilgisi ön planda (saat veya zaman penceresi).

**Üretim planlama ile ilişki:** Aynı “planlama ızgarası” kalıbı `docs/19-planlama-tasarim-prompts/` ile paralel düşünülür; **satır boyutu kalıp değil kamyon**, **anlam üretim değil sevkiyat yüküdür**.

**Ön koşullar:**

- `docs/10-ui-prototype/prompts/00-ORTAK-BLOK.md`
- `docs/10-ui-prototype/prompts/00b-NEOMORPHISM-TAILWIND.md`
- `docs/13-ui-production-prompts/00-ORTAK-BLOK-URETIM-UI.md` (görsel tutarlılık)
- Bağlam: `docs/20-proje-is-akisi-deep-dive/04-lojistik-saha-otomatik-atama.md`, `docs/21-ui-birim-is-emri-prompts/bie-08-lojistik-saha-is-emirleri.md`

**Kapsam dışı (bilinçli):** Saha içi **montaj sırası** planı — sonraki adım; bu paket sadece **lojistik taşıma planı**.

## Çalıştırma sırası

| Sıra | Dosya | Odak |
|------|--------|------|
| 0 | `00-ORTAK-BLOK-LOJISTIK-SAHA-PLANLAMA.md` | Her prompt öncesi kısa bağlam + ortak blok referansı |
| 1 | `log-01-izgara-gun-kamyon-vardiya-saat.md` | Sütun: günler; alt: isteğe bağlı vardiya; satır: kamyonlar; saat / penceresi |
| 2 | `log-02-tasima-yuku-span-cakisma-kapasite.md` | Çok hücreli süre, kamyon çift rezervasyonu, yük hacmi ipuçları |
| 3 | `log-03-etkilesim-dnd-bos-hucre-detay.md` | Sürükle-bırak, boş hücre, yük / sevkiyat satırı detay drawer |
| 4 | `log-04-gunluk-ozet-metrikler.md` | Günlük sefer, m³, ürün adedi toplamları |
| 5 | `log-05-durum-renkleri-legend.md` | Durum → renk (yükleme hazır, yolda, gecikme, iptal) |
| 6 | `log-06-zoom-navigasyon-takvim.md` | Zoom, hafta kaydırma, taşıma olmayan günler |
| 7 | `log-07-kamyon-yonetimi-dis-siparis-toolbar-yetki.md` | Kamyon ekle/çıkar, dışarıdan kamyon siparişi (eksik kapasite), toolbar, taslak/yayın |
| 8 | `log-08-mock-veri-sema-kenar-durumlari.md` | Mock şema, tablolar, yükleme/boş/hata |

Her dosyada **P0 / P1 / P2** ve **mock gereksinimleri** zorunludur.

## Çıktı beklentisi (tüm promptlar için)

Wireframe açıklaması + **mock veri** (dosyada istenen satır sayısı) + **P0/P1/P2** + kısa **Tailwind/neumorphic** notları + **UX soruları**.
