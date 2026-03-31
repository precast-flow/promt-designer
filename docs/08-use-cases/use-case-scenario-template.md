## 🔍 Konu Tanımı

Use case senaryolarını kısa, standardize ve karşılaştırılabilir şekilde yazmak için şablon.

## 🎯 Amaç

- Modüller arası tutarlı dokümantasyon üretmek.
- Senaryo → veri → bağımlılık → event bağlantılarını netleştirmek.

## 🧠 Tartışma Alanı

- “Zorunlu alan” seti ne olmalı? (çok kısa vs yeterince tanımlayıcı)

## 🧱 Use Case Şablonu

- **Adı (kısa ve iş diliyle)**
- **Modül / Context**
- **Aktör(ler)**
- **Ön Koşullar**
- **Tetikleyici**
- **Ana Akış (5–9 adım)**
- **Alternatif Akışlar (varsa, 1–3 madde)**
- **İstisnalar / Hata Durumları (varsa, 1–3 madde)**
- **Üretilen / Güncellenen Veriler**
- **Yayımlanan Event(ler) (varsa)**
- **Bağımlılıklar (hangi modüller/context’ler)**
- **Başarı Kriteri**
- **Açık Sorular**

## 🔄 Sistem İçindeki Yeri

Bu şablonla yazılan her use case, `09-dependencies/` altındaki bağımlılık analizlerine doğrudan girdi sağlar.

