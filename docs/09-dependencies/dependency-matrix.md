## 🔍 Konu Tanımı

Modüller arası bağımlılıkların hızlı okunabilmesi için “matris” formatında özet tablo. Bu dosya bir harita değil, karar destek özetidir.

## 🎯 Amaç

- Bağımlılık yoğunluğunu ve kritik modülleri (hub) erken tespit etmek.
- Faz planı yaparken “önce şu modül gerekir” tartışmasını somutlaştırmak.

## 🧠 Tartışma Alanı

- Matrisin kriteri: sadece zorunlu bağımlılıklar mı, yoksa “nice-to-have” ilişkiler de mi?

## 🧱 Yapısal Analiz (İlk Taslak Matris)

Not: Hücrelerde bağımlılık tipi(leri) yazılır (D1..D5). Boş hücre = doğrudan bağımlılık yok.


| From To         | CRM | Estimating | Project | Engineering | MES   | Quality | Yard  | Dispatch | Field | Reporting |
| --------------- | --- | ---------- | ------- | ----------- | ----- | ------- | ----- | -------- | ----- | --------- |
| **CRM**         | -   |            | D1      |             |       |         |       |          |       | D2        |
| **Estimating**  | D2  | -          | D4      |             |       |         |       |          |       | D2        |
| **Project**     | D2  | D2         | -       | D4          | D4    |         |       | D4       | D4    | D2        |
| **Engineering** |     |            | D2      | -           | D4    |         |       |          |       | D2        |
| **MES**         |     |            | D2      | D2          | -     | D3/D4   | D3/D4 |          |       | D2        |
| **Quality**     |     |            | D2      |             | D3/D4 | -       | D4    |          |       | D2        |
| **Yard**        |     |            | D2      |             | D2    | D2      | -     | D4       |       | D2        |
| **Dispatch**    |     |            | D2      |             |       |         | D2    | -        | D3/D4 | D2        |
| **Field**       |     |            | D3/D4   |             |       |         |       | D2       | -     | D2        |
| **Reporting**   | D2  | D2         | D2      | D2          | D2    | D2      | D2    | D2       | D2    | -         |


## 🔄 Sistem İçindeki Yeri

- Bu tablo, `dependency-map.md` ile birlikte kullanılır.
- Use case senaryoları netleştikçe matris hücreleri güncellenecek.

## ❗ Riskler

- Matrisin “gerçek tasarım kararı” yerine “yaklaşık tablo” olarak kalması.

## ❓ Açık Sorular

- Reporting/Analytics hangi verileri gerçek zamanlı, hangilerini gecikmeli (batch) almalı?

