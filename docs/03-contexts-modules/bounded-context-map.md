## 🔍 Konu Tanımı

Beton prefabrik platformu için DDD yaklaşımıyla tanımlanacak bounded context’lerin (bağlam adaları) yüksek seviye listesi ve aralarındaki ilişki tipi.

## 🎯 Amaç

- Modüler mimari ve entegrasyon kararlarını, net sorumluluk sınırları üzerinden verebilmek.
- Veri sahipliği ve event akışlarını tasarlarken hangi bağlamın hangi dili ve kavramları kontrol ettiğini belirlemek.

## 🧠 Tartışma Alanı

- Modüller bire bir bounded context midir, yoksa bazı modüller tek bir context altında mı birleşmelidir?
- “Proje” mi ana context, yoksa “Üretim” mi?

## 🧱 Yapısal Analiz (Ön Taslak Context Listesi)

- **CRM / Contact Context**
- **Sales & Estimating Context**
- **Project Management Context**
- **Engineering / BIM Context**
- **Production Planning & MES Context**
- **Quality Context**
- **Yard / Inventory Context**
- **Dispatch / Logistics Context**
- **Field / Site Execution Context**
- **Reporting / Analytics Context**

İlerleyen adımlarda her context için:

- Sorumluluk (ne yapar / ne yapmaz)
- Ana entity ve value object’ler
- Kullandığı dil ve terimler
- Dışa açtığı olaylar (events) ve API’ler

tanımlanacaktır.

## ❗ Riskler

- Çok sayıda küçük context oluşturmanın yönetimsel karmaşıklık yaratması.

## ❓ Açık Sorular

- Proje ve üretim context’leri ne kadar sıkı veya gevşek bağlanmalı?

