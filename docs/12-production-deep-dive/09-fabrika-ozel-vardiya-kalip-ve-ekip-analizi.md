# Fabrika özel vardiya, kalıp ve ekip analizi

## Neden eklendi?

Vardiya yapısı ve operasyon düzeni fabrika bazında değişebilir. Bu yüzden firma genel ayarı tek başına yeterli değildir; her fabrika için ayrı operasyon profili gerekir.

## Fabrika bazlı değişkenler

- Vardiya modeli (tek/iki/üç/gece-gündüz)
- Kalıp envanteri (aktif, bakımda, pasif)
- Ekip ve çalışan atamaları (şef, vardiya amiri, usta, operatör)
- Fabrika bazlı iş yükü ve öncelik kuyruğu

## Zorunlu analiz alanları

1. **Vardiya override**
   - Firma default vardiyası + fabrika override ilişkisi
   - Override varsa üretim ekranında vardiya seçenekleri fabrika özel render edilir
2. **Kalıp durum yönetimi**
   - Kalıp ekle/çıkar/pasifleştir
   - Kalıp durumu: uygun, dolu, arızalı, bakımda
3. **Ekip/çalışan yönetimi (fabrika özel)**
   - Çalışanı fabrikaya ekleme/çıkarma
   - Rolü aynı kalsa da fabrika erişimi farklı olabilir
   - Vardiya bazlı görev atama görünürlüğü
4. **Operasyonel rapor etkisi**
   - “Bu fabrikanın bekleyen işleri”
   - “Bu fabrikanın kalıp doluluğu”
   - “Bu fabrikanın vardiya performansı”

## Ürün kuralı (öneri)

- Firma ayarları default sağlar.
- Fabrika ayarları bunu override edebilir.
- Uygulama ekranları her zaman aktif fabrika bağlamına göre render edilir.

## Açık kararlar

- Çalışan aynı anda birden çok fabrikada aktif görev alabilir mi?
- Kalıp transferi fabrikalar arası olacak mı?
- Fabrika override değişince açık emirler nasıl etkilenmeli?
