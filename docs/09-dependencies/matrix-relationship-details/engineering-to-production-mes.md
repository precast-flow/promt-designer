## 🔍 Konu Tanımı

`Engineering Integration` (Mühendislik / CAD-BIM) modülünün `Production Scheduling / MES` modülüne bağımlılığı:
`Engineering Integration → Production/MES = D4 (Süreç bağımlılığı)`.

## 🎯 Amaç

- Tasarım “üretilebilir” hale gelmeden üretim emri / planlama adımlarını başlatmamak.
- Revizyon döngülerinde üretim planının doğru versiyonla eşleşmesini sağlamak.

## 🧠 Tartışma Alanı

- “Üretime hazır” kriteri tam olarak nedir? (eleman listesi onayı, toleranslar, kalite dokümanları, revizyon numarası vb.)
- Mühendislik revizyonu geldiğinde MES tarafında ne tür düzeltmeler gerekir: iptal/yeniden planlama mı, ek revizyon emri mi?

## ⚖️ Alternatifler

- **Alternatif 1 (D3):** Mühendislik event’leri üretim planlamaya “bilgi akışı” sağlar; planlama yine de insan onayıyla ilerler.
- **Alternatif 2 (D2):** MES mühendislik verisini sürekli okur (read modeli), “gate” olmadan tasarım değişiklikleri otomatik yansır.
- **Alternatif 3 (D4 + gate):** Üretim emri veya hat/vardiya tahsisi tasarım onayı event’i gelmeden oluşturulmaz.

Bu dokümanda D4 (gate yaklaşımı) önceliklendirilir.

## 🧱 Yapısal Analiz

### Bağımlılık neden D4?

`D4` burada şu anlama gelir:

- MES tarafında bir iş adımı (ör. “üretim emrini oluştur”, “üretim planını kilitle”, “kalıp/hat tahsisi yap”) **tasarımın üretilebilir çıktısı olmadan yapılamaz**.

### Zorunlu çıktı (mühendislik tarafı)

Engineering Integration’dan Production/MES tarafına aktarılması beklenen zorunlu minimum set:

- Eleman listesi / piece mark listesi (üretim kırılımı)
- Eleman tasarım parametreleri (en azından planlamayı etkileyen kısımlar)
- Tasarım revizyon numarası (hangi revizyonla üretileceği)
- “Üretime hazır” statüsü / onay işareti

### Tipik Senaryo (Akış)

1. Mühendislik çalışması tamamlanır ve revizyonlar yönetilir.
2. Üretime hazır onayı verilir.
3. `Üretime hazır (revizyon X)` gibi bir event üretilir.
4. MES event’i tüketir.
5. MES, revizyon kontrolü yapar (doğru proje + doğru revizyon).
6. MES üretim emri/planlama kayıtlarını oluşturur (veya mevcut planı kilitler).
7. Üretim başladığında MES tarafında “revizyon değiştirilemez” düzeyi belirlenir (firma politikasına göre).

### Senkron vs Asenkron strateji

- Event akışı asenkron olabilir.
- Ancak MES’te “üretilmeyecek” ya da “revizyonsuz” bir adımın başlatılmasını engelleyen gate mantığı gerekir (D4).

## 🔄 Sistem İçindeki Yeri

- Prefabrik sistemde kalite maliyeti ve yeniden üretim riski en yüksek olduğundan, tasarım → üretim bağının sıkılığı kritik bir tasarım kararıdır.

## ❗ Riskler

- “Üretime hazır” statüsü gevşek tanımlanırsa MES planı hatalı revizyonla başlar.
- Revizyon geldikten sonra üretim durdurma/yeniden planlama maliyeti yönetilmezse süreç kaosa döner.

## ❓ Açık Sorular

- Üretime hazır onayı kim tarafından verilir (mühendis mi, kalite mi, proje yöneticisi mi)?
- Tasarım revizyonları, MES tarafında “iptal + yeniden plan” mı yoksa “revizyon düzeltme” mi ile yönetilecek?

