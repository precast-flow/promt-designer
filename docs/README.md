## Beton Prefabrik Süreç Yönetimi Dokümantasyonu

Bu klasör, beton prefabrik ERP + MES + lojistik platformu için analiz ve tasarım dokümanlarını içerir. Kod yok, sadece düşünsel tasarım ve karar kayıtları vardır.

### Okuma Sırası (Önerilen)

1. `01-business-process/overview.md`
2. `01-business-process/prefab-lifecycle.md`
3. `02-actors/roles-and-responsibilities.md`
3b. `02-actors/organizasyon-hiyerarsi-ve-gorev-gorunurlugu.md` (rapor hattı; operasyonel kuyruk birim iş emirleri — bkz. `20-proje-is-akisi-deep-dive/`)
4. `03-contexts-modules/modules-landscape.md`
5. `03-contexts-modules/bounded-context-map.md`
6. `08-use-cases/module-use-cases-index.md`
7. `08-use-cases/use-case-scenario-template.md`
8. `09-dependencies/dependency-map.md`
9. `09-dependencies/dependency-matrix.md`
10. `09-dependencies/matrix-relationship-details/README.md`
11. `04-data-ownership/core-entities.md`
12. `04-data-ownership/ownership-and-lifecycle.md`
13. `05-integration-events/event-starters.md`
14. `05-integration-events/cross-context-flows.md`
15. `06-operations-reality/bottlenecks-and-failure-modes.md`
16. `07-product-strategy/mvp-scope.md`
17. `07-product-strategy/mvp-detailed-analysis-report.md`
18. `07-product-strategy/release-phases.md`

### UI deneme / wireframe prompt’ları (kod yok)

- `10-ui-prototype/react-wireframe-prompts.md` — indeks (giriş)
- `10-ui-prototype/prompts/` — ayrı prompt dosyaları + `README.md` (çalıştırma sırası)
- `10-ui-prototype/prompts/00b-NEOMORPHISM-TAILWIND.md` — Neomorphism + gri/beyaz + Tailwind görsel referansı
- `10-ui-prototype/prompts/00c-DINAMIK-VERI-GORUNUMU-SABLONU.md` — tüm sayfalarda tekrar kullanılabilir dinamik veri görünümü (ikon / liste / tablo / galeri); ilk örnek: `13-ui-production-prompts/prod-04`

### Adım 11 — MVP UI + mock (10 üzerine)

- `07-product-strategy/mvp-decisions-reanalysis.md` — kararlar ve UI etkileri
- `11-ui-mvp-prototype/README.md` — MVP mock prompt sırası (`mvp-00` … `mvp-17`)

### Adım 12–13 — Üretim derinleşmesi (analiz → UI prompt)

- `12-production-deep-dive/README.md` — üretim odaklı kapsam, hiyerarşi, sabah akışı, beton/santral/kalıp (kalite UI bu fazda yok)
- `13-ui-production-prompts/README.md` — üretim ekranları için parça parça UI prompt’ları (`prod-01` … `prod-08`)

### Adım 14–15 — Firma admin & ilk kurulum (analiz → UI prompt)

- `14-firm-admin-deep-dive/README.md` — firma oluşturma, firma ayarları, vardiya politikası, fabrika CRUD, ayarlara göre “render” kuralları (SaaS süper-admin hariç)
- `15-ui-firm-admin-prompts/README.md` — firma admin UI prompt’ları (`firm-01` … `firm-06`)

### Adım 16–17 — Kalite / laboratuvar (analiz → UI prompt)

- `16-quality-deep-dive/README.md` — numune, test kataloğu (slump/çekme, basınç), raporlar, periyodik teslim, izlenebilirlik, santral–üretim köprüsü
- `17-ui-quality-prompts/README.md` — kalite ekranları UI prompt’ları (`qual-01` … `qual-10`)

### Adım 18 — Parametrik 3B prefab (MVP komutları)

- `18-parametric-3d-mvp/README.md` — ölçüden otomatik 3B geometri: JSON sözleşmesi, beş eleman (kolon, kiriş, menfez, panel, L/U perde), spike, viewer/ERP bağlantısı (`01` … `08` + `00-kapsam…` okuma dosyası)

### Adım 19 — Üretim planlama / tasarım (gün × vardiya × kalıp ızgarası)

- `19-planlama-tasarim-prompts/README.md` — Excel benzeri planlama yüzeyi: zaman ekseni, vardiyalar, kalıp satırları, süre span’i, sürükle-bırak, günlük özetler, durum renkleri, zoom, toolbar (`plan-01` … `plan-09` + `00-ORTAK-BLOK-PLANLAMA-TASARIM.md`; `plan-09` düzeltme/iyileştirme paketi)

### Adım 20–21 — Proje yaşam döngüsü + birim bazlı iş emirleri (analiz → UI prompt)

- `20-proje-is-akisi-deep-dive/README.md` — satıştan şantiyeye süreç, kavramlar, birim kuyrukları, iş emri tipleri, lojistik/saha atama, proje zaman çizelgesi / mesajlaşma
- `21-ui-birim-is-emri-prompts/README.md` — birim iş kuyruğu ve proje merkezli UI prompt’ları (`bie-01` … `bie-08` + `00-ORTAK-BLOK-BIRIM-IS-UI.md`). **Kişi bazlı görev panosu (`mvp-17` eski görev panosu) kaldırıldı**; `mvp-17-organizasyon-rapor-hatti-kullanici-formu.md` yalnızca `reports_to` formunu kapsar.

Her dosya, .cursorfile’da tanımlanan ortak şablonu kullanır:

- **🔍 Konu Tanımı**
- **🎯 Amaç**
- **🧠 Tartışma Alanı**
- **⚖️ Alternatifler**
- **🧱 Yapısal Analiz**
- **🔄 Sistem İçindeki Yeri**
- **❗ Riskler**
- **❓ Açık Sorular**

