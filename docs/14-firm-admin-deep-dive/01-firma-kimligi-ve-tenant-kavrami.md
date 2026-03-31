# Firma kimliği ve tenant kavramı

## Amaç

Sistemde “çalışılan firma”yı tek bir **tenant** (kiracı) olarak modellemek: **Organization / Company** kaydı.

## Önerilen temel alanlar (kavramsal)

| Alan grubu | Örnek alanlar | Not |
|------------|---------------|-----|
| **Yasal / kurumsal** | Ticari unvan, vergi no, vergi dairesi, ülke/şehir | Doğrulama politikası ürün kararı |
| **Marka** | Kısa ad, logo URL (veya yükleme), e-posta domain tercihi | |
| **İletişim** | Genel telefon, e-posta, adres | |
| **Dil / yerel** | Saat dilimi, tarih/saat formatı, varsayılan dil | Render: etiketler |
| **Teknik kimlik** | TenantId (iç), slug (opsiyonel) | URL veya subdomain ileride |

## “Firma oluşturuldu” sonrası

- En az bir **firma yöneticisi** kullanıcı atanır (ilk admin).
- İlk fabrika (fabrika) opsiyonel: wizard’dan hemen veya ayarlardan sonra.

## Çok kiracı (ileride)

Aynı şema, SaaS tarafında **birden fazla** Company kaydı için tekrarlanır; bu fazda **tek firma** odaklı UI yeterlidir.
