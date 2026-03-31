# Organizasyon hiyerarşisi, rapor hattı ve görev görünürlüğü

**Ürün güncellemesi:** Kişi bazlı **görev panosu** kaldırıldı. Operasyonel yük ve kuyruk görünümü **birim bazlı iş emirleri** üzerinden tanımlanır — `docs/20-proje-is-akisi-deep-dive/README.md`, UI prompt’lar `docs/21-ui-birim-is-emri-prompts/README.md`. Bu dosyadaki `reports_to` ve “üst / ast” tartışması, **organizasyon ilişkisi** ve ileride genişletilebilecek **hiyerarşik izleme** kuralları için referans kalır; birim iş kurallarıyla çakışan yerler ürün kararında netleştirilir.

## 🔍 Konu Tanımı

Kullanıcılar arasında **organizasyon şeması** (kim kime bağlı) tanımlandığında, **iş / görev** ekranlarında görünürlük kurallarının nasıl işleyeceği. Bu model; rol–izin (RBAC) sisteminden **ayırt edilir**: rol “neyi yapabilirim?” sorusunu, rapor hattı ise “kimin yükünü üstten **salt okunur** izleyebilirim?” sorusunu yanıtlar.

**Veri alanı (isimlendirme notu):** Örnekte geçen “rapor gönderimi” / `reports_to` — kullanıcı kaydında **üst kişi** (yönetici) seçimini ifade eder. Seçim yapıldığında: “Ben, seçilen kişiye bağlıyım” (ast → üst ilişkisi).

---

## 🎯 Amaç

- **Ast (uzman / operatör)** kendi işini görür ve çalışır.
- **Üst (müdür / yönetici)** astının ekranına düşen işleri **iş akışında kendisine atanmamış olsa bile** görebilir; müdahale değil **izleme ve takip** (salt okunur).
- Yöneticinin kendi üzerine atanan veya kendi başlattığı işler ile **astlarının yükü** aynı panoda anlaşılır şekilde ayrılır.
- “Benim durumum” gibi kişisel durum ifadesi kullanıcıya bağlanabilir (isteğe bağlı alan).

---

## 🧠 Kavramlar (sohbette geçen mantığın net hali)

### 1) Kim kime bağlı?

- Kullanıcı A, kullanıcı B’yi **rapor hattı üstü** olarak seçer (`reports_to` → B).
- Anlam: **A ast, B üst** (ör. A uzman, B müdür).
- Organizasyon ağacı: Tahir üstte; Tahir’e bağlı personel altta — Tahir, bağlı personellerin “ekranlarındaki iş yükünü” üstten izler.

### 2) Üst, astın işini neden görür?

- Bir görev **sisteme veya başka bir kullanıcıya (ör. Emre)** atanmış olabilir; iş akışı tanımı gereği **müdürün kuyruğuna hiç düşmeyebilir**.
- Buna rağmen **organizasyon hiyerarşisi** sayesinde: astın “üzerinde / ekranında” görünen görevler, üst kullanıcıya **salt okunur** yansır.
- İş değeri: “Bu iş sende X gündür bekliyor, bitirelim” gibi **operasyonel görünürlük** (ör. muhasebe müdürü, muhasebeci çocukların üzerindeki görevleri izler).

### 3) Salt okunur ne demek?

- Üst, astın görevinde **durum, tarih, atayan, bekleme süresi** gibi alanları görür.
- Varsayılan: **durumu değiştiremez / tamamlayamaz** (veya sadece ayrı izinle “eskale et” gibi sınırlı aksiyon — ürün kararı).
- Astın görevinde yapılan yorumlar, ekler vb. ürün politikasına göre üste açılır veya kısmen maskelenir.

### 4) Kendi işlerim vs astın işleri vs benim başlattıklarım

| Görünüm | Kim | Davranış |
|--------|-----|----------|
| **Bana / grubuma atanan** | Ast veya üst (rol bağlamında) | Çalışılabilir (yetkiye göre) |
| **Grubuma atanan işler** | Takım lideri vb. | Grup kuyruğu üzerinden çalışılabilir |
| **Benim başlattığım ve başkasına atadığım** | Atayan kullanıcı | **Salt okunur takip** (ilerleme izleme) |
| **Astlarımın ekranındakiler** | Rapor hattı üstü | **Salt okunur** (hiyerarşi sayesinde) |

### 5) Rol hiyerarşisi vs kişi hiyerarşisi

- **Rol hiyerarşisi:** Şablon veya iş unvanı seviyesi (genel).
- **Kişi hiyerarşisi (`reports_to`):** Gerçek org chart — görev görünürlüğü için burada tanımlanan model **kişi bazlıdır**.
- İkisi birlikte: RBAC hangi modülleri açar; rapor hattı hangi **görev satırlarını** üstte “izleme” sekmesinde gösterir.

---

## 🧱 Sistem içindeki yeri

- **Kullanıcı yönetimi** ekranında: `reports_to` seçimi + küçük org önizlemesi (“Tahir’e bağlısın”) — UI: `../11-ui-mvp-prototype/mvp-17-organizasyon-rapor-hatti-kullanici-formu.md`.
- **Operasyonel iş kuyruğu:** **Birim bazlı iş emirleri** (üzerime atanan / atadığım, birim bağlamında) — kişi bazlı görev panosu yok; detay `../20-proje-is-akisi-deep-dive/02-birim-kuyruklari-ve-rol-orgusu.md`, UI `../21-ui-birim-is-emri-prompts/bie-05-birim-is-kuyrugu-atanan-ve-atadigim.md`.
- **İsteğe bağlı (P1/P2):** Rapor hattı üstü için “ast birimindeki açık iş emirleri” özetine **salt okunur** bakış — ürün kararı; görev satırı modeli yerine **iş emri + birim** modeliyle hizalanır.
- **Dashboard / bildirim:** Birim veya rol bazlı “bekleyen iş emri” özeti (P1/P2 olabilir).

---

## ⚖️ RBAC ile çakışmayı önleme

- `gorev.goruntule` ile `organizasyon.ast_gorevleri.izle` (veya benzeri) izinleri **ayrı** tutulabilir.
- Bazı organizasyonlarda üst izleme **sadece belirli rollere** açılır (ör. sadece departman müdürü).

---

## ❗ Riskler

- **Gizlilik:** Astın görevi hassas içerik taşıyorsa üst görünürlüğü kısıtlanmalı (proje, modül veya “gizli görev” bayrağı).
- **Döngüsel rapor hattı:** A → B → A zinciri engellenmeli.
- **Performans:** Çok ast ve çok görevde “tüm alt ağaç” sorgusu ağır; sayfalama ve özet KPI şart.

---

## ❓ Açık ürün kararları

1. Üst, ast görevinde **yorum ekleyebilir mi** (salt okunur mu kesin)?
2. Çoklu üst (matris organizasyon) MVP’de var mı, yoksa tek `reports_to` yeterli mi?
3. Fabrika (`site`) bazında rapor hattı aynı mı, farklı mı?

---

## 🔗 İlişkili dokümanlar

- `roles-and-responsibilities.md`
- `../07-product-strategy/mvp-decisions-reanalysis.md`
- `../11-ui-mvp-prototype/mvp-17-organizasyon-rapor-hatti-kullanici-formu.md` (`reports_to` formu)
- `../20-proje-is-akisi-deep-dive/README.md` — proje süreci ve birim iş emirleri (analiz)
- `../21-ui-birim-is-emri-prompts/README.md` — birim iş UI prompt paketi
