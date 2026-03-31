# mvp-17 — Organizasyon rapor hattı (`reports_to`) — kullanıcı formu

```
[Buraya 00-ORTAK-BLOK-MVP-UI.md içeriğini yapıştır]

BAĞLAM (domain):
docs/02-actors/organizasyon-hiyerarsi-ve-gorev-gorunurlugu.md dosyasındaki **rapor hattı** mantığı ZORUNLUDUR. Özet:
- Kullanıcı kaydında üst kişi seçimi: alan adı ürün dilinde örn. "Rapor gönderimi" / teknik `reports_to`.
- Operasyonel iş kuyruğu **kişi bazlı görev panosu ile değil**, **birim bazlı iş emirleri** ile yönetilir — bkz. `docs/21-ui-birim-is-emri-prompts/README.md`.

GÖREV: Aşağıdaki ekranları Neomorphism + gri-beyaz ile tasarla; tamamen MOCK veri. **Görev / iş panosu ekranı bu promptun kapsamında DEĞİLDİR** (kaldırıldı).

---

## A) Kullanıcı formu genişlemesi (mvp-04 ile entegre)

### P0
- Kullanıcı oluştur/düzenle formunda alan: **Rapor gönderimi** (veya "Bağlı olduğu yönetici") — kullanıcı arama / select (mock: Tahir Y., Ayşe K.).
- Seçim sonrası küçük **org önizleme** metni: "Bu kullanıcı [Üst Ad Soyad]'a bağlıdır (ast)."
- İsteğe bağlı alan: **Benim durumum** (serbest metin veya önceden tanımlı durum select — mock).
- Döngü engeli notu: kullanıcı kendisini veya altını üst seçemez (validasyon metni, mock).

### P1
- "Doğrudan astları" sayısı badge (mock: 3 kişi).
- Mini org chart ASCII veya basit ağaç (1 üst, astlar listesi).

### P2
- Çoklu üst / matris organizasyon placeholder (disabled + "ileride" tooltip).

MOCK KULLANICILAR: Tahir (müdür, üstü yok), Sen (uzman, reports_to=Tahir), Emre (iş atayan, aynı departman).

---

## ÇIKTI ZORUNLULUĞU

1) ASCII veya blok wireframe: Kullanıcı formu (`reports_to` vurgulu)
2) RBAC notu: `reports_to` hangi izinlerle düzenlenir
3) Her ana blok için 1 satır Tailwind (`00b` uyumlu)
4) 3–4 UX sorusu (döngü engeli, gizlilik, çoklu üst)

NOT: Bu prompt `mvp-04-kullanici-yonetimi.md` ile arka arkaya veya birleştirilmiş çıktı üretilecek şekilde çalıştırılabilir. Birim iş kuyrukları için **`bie-05-birim-is-kuyrugu-atanan-ve-atadigim.md`** kullanılır.

```
