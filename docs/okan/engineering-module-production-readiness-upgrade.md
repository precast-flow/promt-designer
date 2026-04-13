# Mühendislik modülü — Üretim hazırlık merkezi (frontend uygulama promptu)

Bu dosya **prompt-designer** ürün tanımına göre düzenlenmiştir.

**Uygulama şekli (zorunlu):** Projede **halihazırda çalışan mühendislik entegrasyonu / mühendislik ekranına dokunulmayacak** — dosya, route veya bileşen refaktörü yok. Bu özellikler **yeni bir sayfa** olarak, eski ekranın **üzerine eklenerek** (yan menü / modül listesi / sekme ile erişilen ayrı bir route) geliştirilecek. **Sayfa başlığı ve menüde görünen ad:** **Mühendislik Entegrasyonu-okan**.

---

## Tasarım kaynakları (referans — bu repoda)

| Konu | Doküman |
|------|---------|
| Mühendislik MVP ekranı (paket listesi, Dosyalar / Manuel / Özet, üretime hazır) | `docs/11-ui-mvp-prototype/mvp-08-muhendislik.md` |
| Ortak MVP UI kuralları (mock, fabrika bağlamı, P0/P1/P2) | `docs/11-ui-mvp-prototype/00-ORTAK-BLOK-MVP-UI.md` |
| İş emri Tip A / Tip B ve üretim emri köprüsü | `docs/promts/21-ui-birim-is-emri-prompts/bie-06-muhendislik-is-emirleri-metraj-uretim-koprusu.md` |
| İş emri tipleri (metraj vs üretim öncesi) | `docs/20-proje-is-akisi-deep-dive/03-is-emri-tipleri-ve-muhendislik-devri.md` |
| Mühendislik → MES zorunlu çıktı ve D4 “gate” | `docs/09-dependencies/matrix-relationship-details/engineering-to-production-mes.md` |

**Ürün özeti:** Beton prefabrik ERP/MES bağlamında **Engineering Integration**; üretim, tasarım “üretilebilir” ve onaylı olmadan ilerlememeli (D4 süreç bağımlılığı). UI tamamen **mock**; gerçek CAD/BIM API yok — IFC satırı varsa **“işlenmedi” / gelecek entegrasyon** notu ile kalabilir (`mvp-08` P2).

---

## Aşağıdaki metni frontend projesine yapıştırın

```text
You are a senior frontend architect and product designer working in a React + TypeScript app.

## Implementation approach (mandatory — read first)

- **Do NOT modify, refactor, or replace** the current **Mühendislik entegrasyonu / Engineering** screen, routes, or components that already ship in production. Leave them as-is.
- Implement all features below as a **NEW page** built **on top of** the existing app (additional route + menu entry). Reuse patterns visually if helpful, but **do not edit** the old engineering integration code path.
- **Page title and navigation label:** **Mühendislik Entegrasyonu-okan** (use this exact user-facing name in the shell / sidebar / module list).
- The new page hosts the **production readiness control center** UI described in this prompt (new components, local mock state).

## Product alignment (must follow)

- Domain: prefab concrete ERP/MES. Engineering holds **packages/revisions** (e.g. Rev A, Rev B), **files** (PDF/DWG; IFC may appear as a future-integration row with “not processed” badge), and **manual fields** (e.g. concrete class placeholder, tolerance note, special warning checkboxes — mock labels OK).
- **Job type matters:**
  - **Type A (Tip A):** Metraj / teklif destek — must NOT create a production order. Show a clear banner: “Bu iş üretim emri oluşturmaz.” Readiness and risk UI may still apply; hide or disable “Create production order” / equivalent primary path.
  - **Type B (Tip B):** Üretim öncesi mühendislik — when ready, user can open **“Üretim emri oluştur”** flow (factory, deadline, summary in modal — mock). Success: mock production order id **PRD-####** (existing convention).
- Readiness is tied to the design doc idea of “üretime hazır”: at minimum, conceptual alignment with piece/element list, design parameters, **revision id**, and explicit ready flag — all **simulated in client state**, no API.

## Hard constraints

- **Do not change** existing global routing or module-loading mechanics beyond **registering one new route / menu item** for **Mühendislik Entegrasyonu-okan** (e.g. MainCanvas / activeId style apps: add a new `activeId` target without altering how existing IDs work).
- **No backend, no real integrations.** All data and state transitions are **frontend mock / local state**.
- Do not add heavy new dependencies (large charting/CAD libs). Prefer small local components.
- Keep visual language consistent with the app’s current design system (Neomorphism / Tailwind patterns if already used).

---

## Goal

On the **new page “Mühendislik Entegrasyonu-okan”**, deliver a **production readiness control center** (readiness score, risk panel, workflow stepper, smart production-order modal, etc.). Engineers and operations see **readiness**, **risks**, and **next actions** at a glance, with reactive feedback — **without** changing the legacy engineering integration page.

---

## 1. Production readiness score (0–100%)

Derive a **Readiness %** from mock rules (document the weights in a small constant or comment), e.g.:

- Files present (CAD/PDF/DWG; IFC optional weight or separate “future” flag)
- Manual **critical** fields filled vs optional
- Checklist completion
- Workflow / approval state (see section 4)

**UI**

- Detail view: progress bar **near the top** + semantic badge:
  - **Red — Not ready** (kritik eksikler)
  - **Yellow — Risky** (ilerlenebilir ama uyarı var)
  - **Green — Ready** (üretim emri için uygun, Tip B’de)
- **List view:** her satır/kartta Readiness % + aynı renk dilimi (zorunlu).

---

## 2. Checklist: progress + reactivity

- Show **progress** text: e.g. “6 / 10” plus visual progress.
- Mark items as **critical vs optional** (styling + risk panel).
- **Reactive:** uploading a file, toggling checklist items, or editing manual fields **immediately** updates checklist completion, readiness %, and risk panel. No static-only UI.

---

## 3. Risk & insight panel (detail view — sticky right column)

Sticky right sidebar on the **package/job detail** layout on this new page. Use tabs aligned with the product spec: **Dosyalar / Manuel ayarlar / Özet** (`mvp-08`); place the panel beside or below tabs as layout fits.

Sections:

1. **Current workflow status** (aligned with section 4 — Draft / In review / Approved / Production created)
2. **Missing items** (dynamic bullets)
3. **Risk alerts** (e.g. “IFC satırı işlenmedi”, “Tolerans tanımlı değil”, “Revizyon kilidi — üretimde kullanılan dosya”)
4. **Suggested actions** (e.g. “Üretim emri oluşturmadan önce onay al” — Tip B)

Updates live from UI state.

---

## 4. Status flow (client-side state machine)

Visible horizontal **stepper / timeline**:

States (labels can be Turkish in UI if the app is Turkish):

- Draft (Taslak)
- In review (İncelemede)
- Approved (Onaylı)
- Production created (Üretim oluşturuldu)

**Actions by state (mock only):**

- Draft → primary: **“İncelemeye gönder”** (Submit for review)
- In review → **“Onayla”** / **“Revizyon iste”**
- Approved (Tip B) → **“Üretim emri oluştur”** (opens enhanced modal from section 5)
- Production created → disable duplicate creation or show read-only summary

Type A: do not offer production order creation; adjust CTAs accordingly (e.g. complete / archive mock).

---

## 5. Smart “Üretim emri oluştur” flow (Tip B only)

Before submit:

- Modal shows **missing items**, **warnings**, **summary** (fabrika, termin, özet — mock).

User choices:

- **“Önce eksikleri tamamla”** / Fix issues first (close and focus)
- **“Yine de devam et”** / Proceed anyway (with extra confirmation if critical gaps)

After success:

- Assign mock id **PRD-####**
- Set state to **Production created**
- Optional: append timeline event text for project view (mock string)

---

## 6. Summary card (detail — quick overview)

Compact card (can live under stepper or in Özet tab):

- Proje adı
- İş emri tipi (**A / B**)
- Workflow status
- Readiness %
- Son güncelleme (mock timestamp)

---

## 7. List view (high impact)

Each engineering job row/card:

- Status badge (workflow)
- Readiness %
- Risk icon or severity hint
- Quick actions: **Aç**, and **“Hazır işaretle”** or equivalent only when rules allow (mock)

Optional: **liste / kart** görünümü toggle.

---

## 8. Reactivity (critical)

Chain updates:

- File upload / file list change → checklist + readiness + risk panel
- Manual field change → readiness + risk
- Checklist toggle → readiness + risk

---

## 9. UX polish

- Tooltips / inline warnings for critical fields
- Collapsible sections where content is dense
- Clear **critical vs optional** field grouping in “Manuel ayarlar”

---

## Deliverables

- **New route + page** for **Mühendislik Entegrasyonu-okan**; **new** components only (e.g. `ReadinessBar`, `RiskInsightPanel`, `WorkflowStepper`, `ReadinessBadge` — names flexible). Optionally a thin page container such as `EngineeringIntegrationOkanPage` or similar.
- **Zero changes** to the existing engineering integration module files unless the project strictly requires a single shared types file — prefer local mock types inside the new page folder.
- Mock data rich enough to demo Type A and Type B, Rev A/B, and at least one locked file row (same domain as `mvp-08`).

Focus: clarity, decision support, and real-time feedback for engineers and operations.
```

---

**Yazar:** Okan · **Kaynak:** `docs/11-ui-mvp-prototype/okan/` — prompt-designer ürün dokümanlarıyla uyumlu sürüm
