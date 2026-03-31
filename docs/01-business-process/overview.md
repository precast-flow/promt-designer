## 🔍 Konu Tanımı

Beton prefabrik şirketinde uçtan uca iş süreci: ilk temas ve tekliften başlayarak, sözleşme, mühendislik tasarımı, üretim planlama ve üretim, yard/stok yönetimi, sevkiyat ve şantiyede montaj ile hakediş ve proje kapanışına kadar uzanan akışın yüksek seviye haritası.

## 🎯 Amaç

- Şirketin gerçek iş akışını tek sayfalık, herkesin konuşabileceği ortak bir modelde toplamak.
- Daha sonra gelecek modül tasarımı, bounded context, veri sahipliği ve entegrasyon kararlarına zemin hazırlamak.

## 🧠 Tartışma Alanı

- Siparişin “doğduğu” nokta neresi: CRM kontağı mı, resmi sipariş mi, sözleşme mi?
- Mühendislik onayı ve revizyonları sürecin neresinde, hangi aşamada “üretilebilir” veri oluşuyor?
- Üretim ve sevkiyat planlama hangi bilgileri zorunlu olarak ister (çizim, termin tarihi, kalıp durumu, kapasite)?
- Şantiyedeki ilerleme, hakediş ve geribildirimler ana akışa nasıl geri beslenir?

## ⚖️ Alternatifler

- **Satış odaklı akış:** CRM ve teklif süreçlerinin detaylı, üretimin ise daha özet tutulduğu bakış açısı.
- **Üretim odaklı akış:** Üretim ve kalıp/kapasite planlamasının merkezde olduğu, satışın daha “girdi” gibi ele alındığı bakış açısı.
- **Proje odaklı akış:** Tüm sürecin proje yaşam döngüsü etrafında (proje fazları, revizyon dalgaları) kurgulandığı bakış açısı.

Bu dokümanda öncelik, proje odaklı ama üretim gerçeklerine duyarlı bir akıştır.

## 🧱 Yapısal Analiz

Yüksek seviyede uçtan uca süreç şu adımlardan oluşur:

1. **Ön temas ve fırsat yaratma**
   - Müşteri veya proje bilgisi ilk kez sisteme girilir (CRM / Contact Management).
   - Proje türü (konut, sanayi, altyapı vb.), lokasyon, tahmini metraj/tipler kaydedilir.
2. **Teklif ve maliyetlendirme**
   - Eleman tipleri, yaklaşık metrajlar, maliyet varsayımları üzerinden teklif oluşturulur.
   - Farklı senaryolar (fiyat kırılımları, alternatif çözümler) saklanır.
   - Teklif onay/ret bilgisi kaydedilir; onaylanan teklifler proje adayına dönüşür.
3. **Sözleşme ve proje açılışı**
   - Onaylanan teklif, sözleşme koşullarıyla birlikte “proje”ye dönüştürülür.
   - Jenerik bilgiler (termin planı, ödeme şartları, ana paydaşlar) belirlenir.
4. **Mühendislik tasarımı ve revizyon yönetimi**
   - Proje, mühendislik ekiplerine aktarılır (CAD/BIM entegrasyonu).
   - Eleman listesi (piece mark list), teknik şartlar ve revizyonlar yönetilir.
   - “Üretime hazır” statüsüne gelen elemanlar işaretlenir.
5. **Üretim planlama**
   - Üretim kapasitesi, kalıp durumu, vardiyalar ve saha şartları dikkate alınarak plan yapılır.
   - Elemanlar üretim emrine bağlanır; hat, gün, vardiya eşleştirmeleri belirlenir.
6. **Üretim ve kalite kontrol**
   - Günlük/ vardiyalık üretim gerçekleşir; beton döküm, kür, kalıptan çıkarma adımları izlenir.
   - Her eleman için kalite kayıtları (testler, kusurlar, retler, tamirler) tutulur.
   - Üretimi tamamlanan ve onaylanan elemanlar “yard’a hazır” olur.
7. **Yard / stok yönetimi**
   - Elemanların sahadaki fiziksel konumu (yard, stok alanları) takip edilir.
   - Yükleme sırası ve sevkiyat önceliği için uygun bloklama/gruplama yapılır.
8. **Sevkiyat planlama ve yükleme**
   - Proje termin planı, şantiye talebi ve saha kısıtlarına göre sevkiyat planı oluşturulur.
   - Araç planı, rota, yükleme sıralaması belirlenir; yükleme gerçekleşir ve çıkış kaydedilir.
9. **Şantiye / montaj ilerlemesi**
   - Elemanların sahaya varışı, boşaltma ve montaj durumları kaydedilir.
   - Montaj sıralaması, vinç/ekip kısıtları ve teknik sorunlar izlenir.
10. **Hakediş, kapanış ve geri besleme**
    - Sözleşme şartlarına göre hakedişler, gerçekleşen metraj ve ilerleme üzerinden hesaplanır.
    - Proje kapanışında, üretim ve şantiye verileri sonraki projeler için geri besleme (costing, planlama, risk) olarak kullanılır.

## 🔄 Sistem İçindeki Yeri

- Diğer tüm modül ve bounded context tasarımlarının referans alacağı **ana omurga**dır.
- Aktör analizinde tanımlanacak roller (satış, proje yöneticisi, mühendis, üretim planlamacı, şantiye şefi vb.) bu akış üzerindeki görevlerine göre konumlanır.
- Veri sahipliği tartışmalarında (hangi veri nerede doğar) temel zaman çizelgesi olarak kullanılır.

## ❗ Riskler

- Gerçek hayatta şirketten şirkete değişen ara adımların (taşeron, alt yüklenici, dış tesis üretimi vb.) bu modelde göz ardı edilmesi.
- Mühendislik ve üretim arasındaki revizyon döngülerinin olduğundan basit görünmesi.
- Şantiye tarafındaki kaotik durumların (hava, zemin, koordinasyon eksikliği) modelde yeterince temsil edilmemesi.

## ❓ Açık Sorular

- Hangi aşamada “resmi sipariş” kabul edilmelidir: teklif onayı mı, sözleşme imzası mı, avans ödemesi mi?
-, Şirketin tipik işlerinde mühendislik mi süreci sürüklüyor, yoksa satış/proje yönetimi mi?
- Üretim kapasitesi planlanırken hangi zaman çözünürlüğü (günlük, vardiyalık, saatlik) pratikte kullanılabilir?
- Şantiyeden geri dönen bilgi (gecikmeler, revizyon istekleri, montaj problemleri) iş akışının hangi adımlarını yeniden tetikliyor?

