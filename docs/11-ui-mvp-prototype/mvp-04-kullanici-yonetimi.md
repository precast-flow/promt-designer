# mvp-04 — Kullanıcı yönetimi (fabrika erişimi mock)

```
[Buraya 00-ORTAK-BLOK-MVP-UI.md içeriğini yapıştır]

GÖREV: Kullanıcı CRUD + rol atama + fabrika erişimi (mock). Neumorphic liste–detay.

### P0
- Liste: ad, e-posta, durum (aktif/pasif), roller (chip), **rapor gönderimi (üst kişi)** mock kolon veya detayda, son giriş mock.
- Filtre: rol, durum, fabrika (hangi fabrikada çalışıyor mock).
- Detay: **Profil**, **Roller** (çoklu seçim), **Fabrika erişimi** (çoklu checkbox mock), **Rapor gönderimi (`reports_to`)** — üst kullanıcı seçimi + "Bağlı olduğun yönetici" önizlemesi (organizasyon şeması metni).
- Aksiyonlar: Pasifleştir (modal onay), Şifre sıfırla (toast mock).

### P1
- Davet e-postası gönderildi durumu (badge mock) — backend yok, sadece UI state.
- “Varsayılan fabrika” seçimi (tek).

### P2
- Oturum listesi mock (cihaz, son aktivite) — salt okunur.

MOCK: 6 kullanıcı satırı; 2’si çoklu fabrika, 1’i pasif.

ÇIKTI: Wireframe + pasif kullanıcının menüde ne göremeyeceği notu + UX soruları

İLGİLİ: Rapor hattı (`reports_to`) alanı için **`mvp-17-organizasyon-rapor-hatti-kullanici-formu.md`** ile birlikte çalıştır. Birim iş kuyrukları için **`docs/21-ui-birim-is-emri-prompts/bie-05-birim-is-kuyrugu-atanan-ve-atadigim.md`**.
```
