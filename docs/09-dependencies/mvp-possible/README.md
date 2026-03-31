## 🔍 Konu Tanımı

`dependency-map.md` içindeki bağımlılık ilişkilerinden, MVP akışında (bkz. `07-product-strategy/mvp-scope.md`) anlamlı olacak ve makul sadeleştirmelerle uygulanabilecek olanları burada ayrı toplarız.

## 🎯 Amaç

- MVP’ye dahil olmayan bağımlılıkları erken fark edip kapsamı korumak.
- MVP’ye giren bağımlılıkları “minimum karar seti” ile sadeleştirerek ilerlemek.

## 🧱 MVP İnceleme Listesi (Tek Tek Planlanacak)

1. `Estimating → Project` (`D4`)
2. `Engineering → Production/MES` (`D4`)
3. `Production/MES → Quality` (`D3/D4`)  *(MVP’de “minimal kalite gate” mi, yoksa “raporlama” mı?)*
4. `Quality → Yard/Inventory` (`D4`)  *(MVP’de kalite modülü var mı?)*
5. `Yard/Inventory → Dispatch/Logistics` (`D2/D4`)
6. `Dispatch/Logistics → Field/Site` (`D3`)
7. `Field/Site → Project Management` (`D3/D4`)

Her birini sırayla planlayacağız. Bu klasördeki dokümanlar ilgili ilişki için:
- MVP uygunluğu (E/H)
- MVP’de sadeleştirme yaklaşımı
- Hangi kararın kesinleşmesi gerektiği

alanlarını tutar.

