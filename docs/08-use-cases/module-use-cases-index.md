## 🔍 Konu Tanımı

Her modül için yazılacak use case senaryolarının (kısa, iş diliyle) indeks dokümanı. Bu dosya sadece liste ve kapsam sınırı tutar; detaylar alt dosyalardadır.

## 🎯 Amaç

- Modül bazında “sistem neyi yapmalı?” sorusunu somut senaryolara indirgemek.
- MVP kapsamı ve faz planını, gerçek senaryolarla kalibre etmek.

## 🧠 Tartışma Alanı

- Use case’ler “happy path” mi ağırlıklı, yoksa istisnalar ve hata senaryoları mı öncelikli?
- Aynı senaryonun farklı rollerle varyantları ayrı use case mi, yoksa tek use case altında varyant mı?

## 🧱 Yapısal Analiz (Use Case Dokümanları)

- **CRM / Contact**
  - `crm-contact.md`
- **Estimating & Quoting (Teklif)**
  - `estimating-quoting.md`
- **Project Management**
  - `project-management.md`
- **Engineering Integration (CAD/BIM)**
  - `engineering-integration.md`
- **Production Scheduling / MES**
  - `production-mes.md`
- **Quality Control**
  - `quality-control.md`
- **Yard / Stock Management**
  - `yard-inventory.md`
- **Dispatch / Logistics**
  - `dispatch-logistics.md`
- **Field / Site**
  - `field-site.md`
- **Reporting & Analytics**
  - `reporting-analytics.md`
- **Mobile**
  - `mobile.md`

## 🔄 Sistem İçindeki Yeri

- Bu indeks, modül manzarası (`03-contexts-modules/`) ile bağımlılık haritaları (`09-dependencies/`) arasında köprüdür.
- Her use case, mümkün olduğunca en az bir “tetikleyici event” ile ilişkilendirilecektir.

## ❗ Riskler

- Use case’lerin “ekran listesi”ne dönüşmesi (iş değerinden kopması).
- Çok detay erken girilmesi ve gerçek saha keşfine kapalı kalınması.

## ❓ Açık Sorular

- İlk faz (MVP) için kaç use case “çekirdek” olarak seçilmeli?

