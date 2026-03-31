# log-03 — Etkileşim: sürükle-bırak, boş hücre, taşıma detayı

```
[Buraya 00-ORTAK-BLOK-LOJISTIK-SAHA-PLANLAMA.md bağlamını ekle]
[Buraya 00-ORTAK-BLOK.md + 00b + 00-ORTAK-BLOK-URETIM-UI.md içeriklerini yapıştır veya dosya yollarıyla bağla]

GÖREV: Planlama yüzeyinde **DnD** ile taşıma kalemini kamyon/gün (ve varsa vardiya) arasında taşı; **boş hücreye bırakma**; satır/kart tıklanınca **detay paneli** (drawer).

## 🔍 Konu tanımı
Üretim planlama `plan-03` ile aynı etkileşim ailesi: sürükle-bırak, hücre hedefi, detay.

### P0
- **Sürükle-bırak:** Kartı başka kamyon satırına veya başka güne taşıma (mock).
- **Boş hücre:** Yeni atama veya havuzdan düşürme alanı (havuz varsa `docs/10-ui-prototype/prompts/00c-DINAMIK-VERI-GORUNUMU-SABLONU.md` ile uyumlu düşün).
- **Detay drawer:** Yük kimliği, ürün, miktar, hedef saha (tek saha — sabit metin olabilir), planlanan saat/pencere, üretim emri / sevkiyat ref (mock alan adları).

### P1
- Klavye ile tarih/kamyon değiştirme (erişilebilirlik) — kısa not.

### P2
- Çoklu seçim ve toplu taşıma.

### Mock gereksinimleri
- En az **1** havuzdan ızgaraya atama senaryosu anlatımı (mock).

ÇIKTI: Etkileşim akışı + P0/P1/P2 + UX soruları
```
