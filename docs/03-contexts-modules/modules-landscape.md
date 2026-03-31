## 🔍 Konu Tanımı

Beton prefabrik süreç yönetimi için ihtiyaç duyulan modül/bounded context manzarasının, mevcut sektör çözümleri (örneğin Concrete Vision) ile karşılaştırmalı olarak kısa tanımı.

## 🎯 Amaç

- Hangi modüllerin bu ürün için “olmazsa olmaz”, hangilerinin faz-2/3 olduğunu görmek.
- Her modülün kabaca hangi iş problemini çözdüğünü ve hangi bağlamda çalıştığını netleştirmek.

## 🧠 Tartışma Alanı

- Tek ürün mü, yoksa birden çok ürün (örn. temel platform + mobil saha uygulaması) olarak mı düşünülmeli?
- Hangi modüller klasik ERP’ye entegre olacak, hangileri tamamen bu sistemin içinde sahiplenilecek?

## 🧱 Yapısal Analiz (Kısa Modül Listesi)

- **Contact / CRM**
- **Estimating & Quoting (Teklif)**
- **Project Management (Proje)**
- **Engineering Integration (CAD/BIM)**
- **Production Scheduling / MES**
- **Quality Control**
- **Yard / Stock Management**
- **Dispatch / Logistics (Sevkiyat)**
- **Field / Site (Şantiye)**
- **Reporting & Analytics (Raporlama)**
- **Mobile (Saha ve yöneticiler için mobil yüzler)**

Her modül için detaylı kapsam, giriş/çıkış verileri ve diğer modüllerle ilişkiler daha sonra doldurulacaktır.

## ❗ Riskler

- Mevcut ERP’lerle çakışan modüllerin iki kere tanımlanması.

## ❓ Açık Sorular

- Hangi modüller bu ürünün “çekirdeği” olarak görülmeli, hangileri isteğe bağlı eklentiler olmalı?

