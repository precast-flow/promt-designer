# MVP kararları — yeniden analiz (UI ve kapsam)

## 🔍 Amaç

`mvp-detailed-analysis-report.md` içindeki açık sorulara verilen yanıtlar ve ürün tercihleri doğrultusunda **MVP’nin anlamını**, **UI prototipinin taşıması gereken yapıları** ve **bilinçli olarak ertelenen** konuları netleştirmek.

Bu doküman, **`docs/11-ui-mvp-prototype/`** altındaki detaylı UI prompt’larının girdisidir.

---

## ✅ Paydaş kararları (özet)

| Konu | Karar |
|------|--------|
| **Kiracı / şirket modeli** | Tasarım şu an **tek şirket** varsayımıyla; o şirket içinde **birden fazla fabrika** olabilir. Çok şirketli SaaS ve “hangi modül satın alındı” yönetimi **ayrı bir global admin panel** konusu; şimdilik prototipe derinlemesine girilmiyor. |
| **Modül lisansı** | İleride şirket bazında modüller dinamik açılıp kapanacak; **şu anki UI çalışması** tüm modülleri göstererek yapılır veya feature-flag placeholder ile not düşülür (implementasyon yok, sadece tasarım notu). |
| **Onay / hiyerarşi** | Sadece teklif değil; **tüm süreçlerde** hangi rol ve kişilerden geçileceği **dinamik ve hiyerarşik** tanımlanabilmeli. UI’da genel bir “onay akışı şablonu” ve süreç türü (teklif, üretim emri, sevkiyat vb.) bağlamı düşünülür. |
| **Mühendislik** | **Hem dosya yükleme hem manuel** ayarlar; veri **mock**. |
| **Kalite** | Üretim kapanış onayı yerine **üretimle iç içe tam kalite modülü** olarak ele alınır (aynı ekran akışlarında veya bitişik modülde). |
| **Şantiye** | İlk aşamada **yalnızca web**; mobil sonraya. |

---

## 🧠 Analiz: Bu kararların ürün ve UI etkileri

### 1) Tek şirket + çok fabrika

- **Zorunlu UI öğesi:** Üst bar veya ayarlar yakınında **aktif fabrika seçici** (mock: 2–3 fabrika adı).
- **Veri mock’u:** Tüm listeler (emir, yard, sevkiyat) fabrika bağlamına göre filtrelenmiş gibi gösterilir.
- **Ertelenen:** Şirketler arası geçiş, fiyatlandırma, lisans — global admin.

### 2) Dinamik modül kapsamı (gelecek)

- Prototipte: tüm modüller menüde kalabilir; isteğe bağlı **“Modül görünürlüğü (demo)”** açıklaması veya gizli dev notu.
- Gerçek “satın alınan modül” kapatma işi **müşteri yönetim admin’inde** kalır.

### 3) Süreç genelinde hiyerarşik onay

- Tek “teklif onaycısı” yeterli değil; **yeniden kullanılabilir** bir **Onay akışı tasarımı** UI’si gerekir:
  - Süreç tipi seçimi (ör. Teklif, Üretim emri kilidi, Sevkiyat çıkışı — MVP mock listesi).
  - Adımlar: sıra, rol veya kullanıcı ataması, isteğe bağlı **tutar / eşik** alanı (teklif için anlamlı; diğer süreçlerde N/A veya boş).
- Bu, rol/izin ekranı ile **çakışmadan** tamamlanmalı: rol “kim yapabilir”, onay akışı “sıra ve zorunlu geçiş”.

### 4) Mühendislik: dosya + manuel

- Aynı ekranda veya sekmelerde: **Dosyalar** + **Manuel parametreler / checklist** (üretime hazır bayrağı manuel de kalkabilsin).
- Mock: örnek PDF/DWG satırları + checkbox’lar.

### 5) Kalite ↔ üretim

- Navigasyon: “Üretim” altında veya yanında **Kalite**; paylaşılan kuyruk veya sekme ile **aynı emir / eleman** bağlamı.
- Mock: üretim satırından kalite formuna geçiş, durumlar senkron.

### 6) Şantiye web

- `10-ui-prototype` mobil önizleme prompt’u **korunur** ama MVP akışında öncelik **responsive web saha** ekranlarıdır; native mobil sonraki faz.

---

## 📋 P0 / P1 / P2 — bu kararlarla uyumlu anlam

| Seviye | Bu karar setine göre odak |
|--------|----------------------------|
| **P0** | Giriş kabuğu, fabrika seçici (mock), kullanıcı + rol + izin, onay akışı tasarımcısı (en az 1 süreç tipi mock), teklif→proje→üretim→kalite (bitişik)→yard→sevkiyat için **tıklanabilir mock akış**, şantiye web basit teslim. |
| **P1** | Çok adımlı onay şablonları, mühendislik dosya + manuel tam akış, raporlar, denetim satırı mock, fabrika bazlı filtreler her modülde tutarlı. |
| **P2** | Gelişmiş onay koşulları (eşik + paralel adım placeholder), modül görünürlük simülasyonu, mobil önizleme ile parity denemeleri, export mock. |

---

## ❗ Riskler

- **Onay tasarımcısı + RBAC** aynı anda karmaşıklaşırsa MVP UI şişer → prompt’larda **aşamalı** (önce teklif süreci, sonra şablon kopyala) yaklaşımı yazıldı.
- **Kalite–üretim** birleşik ekranlar rol karmaşası yaratır → yetki matrisinde “kalite.onay” ayrı izin olarak kalır.

---

## 👥 Organizasyon rapor hattı ve görev görünürlüğü (ürün mantığı)

Kullanıcıda **`reports_to` (ör. alan adı: rapor gönderimi)** ile ast–üst ilişkisi tanımlanır. **Üst kullanıcı**, astının ekranında görünen görevleri, iş akışı bu görevi üste atamasa bile **salt okunur** izler (müdürün muhasebeci üzerindeki işleri takip etmesi gibi senaryo). Bu, RBAC’ten ayrı bir **görünürlük** kuralıdır.

Detay: `docs/02-actors/organizasyon-hiyerarsi-ve-gorev-gorunurlugu.md` — kullanıcı formu UI: `docs/11-ui-mvp-prototype/mvp-17-organizasyon-rapor-hatti-kullanici-formu.md`. Operasyonel kuyruk (birim iş emirleri): `docs/21-ui-birim-is-emri-prompts/README.md`.

---

## ❓ İleride netleştirilecek (bu pakette derinleşme yok)

- Global müşteri admin paneli ekranları ve modül lisans matrisi.
- Gerçek çok kiracı veri izolasyonu ve kurulum otomasyonu.

---

## 🔗 Sonraki adım

`docs/11-ui-mvp-prototype/` — Adım 11: mock veri + P0/P1/P2 parça parça UI prompt’ları (`README.md` sırasına göre).

**Üretim derinleşmesi (MVP odağı):** `docs/12-production-deep-dive/` (analiz), ardından `docs/13-ui-production-prompts/` (UI prompt paketi).

**Firma admin & ilk kurulum:** `docs/14-firm-admin-deep-dive/` (analiz), ardından `docs/15-ui-firm-admin-prompts/` (UI prompt paketi).

**Kalite / laboratuvar:** `docs/16-quality-deep-dive/` (analiz), ardından `docs/17-ui-quality-prompts/` (UI prompt paketi).
