# Kapsam: içeri / dışarı (firma admin derinleşmesi)

## Bu fazda YAPACAĞIMIZ

1. **Firma (şirket) kaydı** için gerekli **alan kataloğu** ve **ilk kurulum akışı** (wizard veya adımlı form).
2. **Firma ayarları** sayfası: temel bilgiler, iletişim, vergi/kurumsal kimlik (ürün gereksinimine göre).
3. **Çalışma takvimi / vardiya politikası:** gündüz-only mi, gece–gündüz mü, kaç vardiya; üretim ve planlama ekranlarına **etkisi** (mantıksal).
4. **Fabrika yönetimi** firma ayarları içinde: ekleme, pasifleştirme, kod, isim, adres (12. faz ile uyumlu).
5. **“Ayarlara göre render”** prensibi: hangi bayraklar hangi menüleri, filtreleri, varsayılan vardiyayı değiştirir (kısa kural listesi).
6. **Firma admin** kabuğu: bu bağlamda kullanılan menü ve sayfa iskeleti (konsept).

## Bu fazda YAPMAYACAĞIMIZ (bilinçli)

1. **SaaS platform sahibinin** tüm müşteri firmalarını yönettiği **mega panel** ekranları (liste fiyat, faturalama, lisans) — ayrı ürün dilimi.
2. **Detaylı finans / muhasebe** ayarları.
3. **Gerçek kimlik doğrulama** (SSO, LDAP) entegrasyon detayı — sadece “ileride” notu.

## İlişki: “İlk değerler değiştirilebilir”

İlk kurulumda girilen değerlerin tamamı **firma ayarları** üzerinden sonradan güncellenebilir olmalıdır; tek istisna ürün kararı ile **kilitlenebilir** alanlar (ör. vergi no değişimi onaylı).
