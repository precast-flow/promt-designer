# Ayarlara göre uygulama davranışı (“render” kuralları)

**Kullanıcı vurgusu:** İlk girilen / firma ayarlarından yönetilen bilgiler **uygulamanın nasıl görüneceğini ve hangi varsayılanların seçileceğini** belirler.

## Kural örnekleri (katalog)

| Ayar | Uygulama davranışı |
|------|---------------------|
| Saat dilimi | Tüm tarih/saat gösterimi, rapor kesim saatleri |
| Varsayılan dil | UI etiketleri (i18n) |
| Vardiya politikası | Vardiya filtresinin görünürlüğü ve seçenek sayısı |
| Fabrika vardiya override | Aynı kullanıcı farklı fabrikaya geçince vardiya seçenekleri değişir |
| Varsayılan fabrika | Üst bar ilk yükleme seçimi |
| Fabrika kalıp aktif/pasif | Kalıp tahtasında görünür kalıp listesi değişir |
| Fabrika çalışan ataması | Vardiya ve görev atama listelerinde görünen personel değişir |
| Hafta sonu üretimi = kapalı | Takvimde Cumartesi/Pazar günleri gri veya kilitli |
| Tek fabrika | Fabrika seçici gizlenir veya salt bilgi gösterilir |

## Teknik olmayan ifade

“Render” burada **React render** değil; **ürün diliyle** menü, filtre, varsayılan ve uyarıların **dinamik oluşumu**.

## Versiyonlama (opsiyonel)

- Ayar değişikliği “geçerli olduğu tarih” ile kaydedilirse geçmiş raporlar tutarlı kalır — P2.

## Risk

- Ayar değişince açık emirlerin etkilenmesi: uyarı modalı veya salt bilgilendirme.
