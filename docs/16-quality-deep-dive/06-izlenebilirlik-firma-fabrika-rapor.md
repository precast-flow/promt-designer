# İzlenebilirlik: hangi bilgi hangi raporda?

## Soru şablonu

> “Bu PDF / bu satır **hangi firmanın**, **hangi fabrikasının**, **hangi proje/emir/numune** kaydına ait?”

## Zorunlu meta veri (öneri)

Her kalite kaydı ve üretilen rapor üzerinde:

- `company_id` / görünen unvan
- `plant_id` / fabrika adı
- `report_id`, `report_version`
- `created_at`, `created_by`
- İsteğe bağlı: `project_id`, `order_id`, `pour_id`, `sample_id`

## Rapor şablonu alanları

- Üst bilgi bloğu: logo, firma unvanı, fabrika, tarih, rapor no (benzersiz).
- İmza: hazırlayan, kontrol eden, onaylayan (rol bazlı).

## Denetim (audit)

- Kim hangi sonucu değiştirdi — üretim ve kalite için ortak audit prensibi (detay P2).
