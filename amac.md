# Bu proje ne işe yarıyor?

Bu depo, **beton prefabrik süreç yönetimi** için tasarlanan bir **ERP + MES + lojistik** platformunun **ürün ve sistem tasarımını** üretmeye odaklanır. Burada öncelikle **kod değil**, **düşünce, analiz, karar kayıtları ve yapılandırılmış dokümantasyon** vardır.

`.cursorfile` ile tanımlanan çalışma biçimi: **yazılım geliştirici gibi kod yazmak değil**; sistem mimarı, DDD, ERP/MES danışmanlığı, iş analizi ve ürün stratejisi perspektifiyle **önce problemi netleştirip**, modüller arası sınırları, veri sahipliğini, entegrasyon olaylarını ve operasyonel gerçekliği **dokümante etmek**.

`docs/` altında yedi ana bağlam üzerinden (E2E süreç, aktörler, bounded context, veri sahipliği, entegrasyon, operasyonel riskler, MVP/strateji) ilerleyen bir **klasör yapısı** ve okuma sırası vardır. Amaç, yazılıma geçmeden önce sistemin büyük resmini ve modül ilişkilerini **paylaşılabilir ve tekrar kullanılabilir** hale getirmektir.

Ayrıca bu proje, **UI prototip ve wireframe üretimi için prompt paketleri** içerir (`docs/10-ui-prototype/`, `11-ui-mvp-prototype/`, üretim/kalite/firma admin/planlama/birim iş emri vb. adımlar). Bu promptlar harici veya ayrı bir frontend kod tabanında kullanılmak üzere yazılır; bu repodaki odak **ürün tanımı ve prompt tasarımıdır**, çalışan uygulama kodu değildir.

**Mühendislik altı örnek (Okan):** `Manual Piece & Template Studio-okan` (**MPTS-okan**) — katalog (material items/assemblies) → piece mark şablonları → işe bağlı üretim parçası; tam UI–IA spesifikasyonu `docs/11-ui-mvp-prototype/okan/manual-piece-template-studio-okan.md`, giriş noktası `docs/MPTS-okan-ui-ia.md`.

---

# Neyi amaçlıyoruz?

- **Uçtan uca prefabrik iş modelini** (satıştan şantiyeye, mühendislikten üretime, kaliteden sevkiyata) **tek bir tutarlı çerçevede** anlatmak.
- **Modül sınırları, bağımlılıklar ve olaylar** üzerinden entegrasyonu erken tartışılabilir kılmak; “kim neyi üretir, kim tüketir” sorusunu netleştirmek.
- **MVP ve fazlama** kararlarını dokümante ederek, geliştirme öncesi **öncelik ve kapsam** için referans oluşturmak.
- İhtiyaç duyulduğunda **UI/UX denemeleri** için tekrar kullanılabilir **prompt şablonları ve adım adım paketler** sunmak; tasarım dilini (ör. Neomorphism, mock veri, P0/P1/P2) ürünle uyumlu tutmak.

Özetle amaç: **Yazılıma başlamadan sistemin büyük kısmını netleştirmek**, paydaşlarla ve ileride yazılacak uygulamayla **ortak bir blueprint** olarak kullanılabilecek bir dokümantasyon ve prompt tasarımı üretmektir.

---

*Bu dosya, fikir alırken ve kapsamı hatırlamak için tek sayfalık bir özet olarak tutulur; detaylar `docs/README.md` ve ilgili klasörlerdeki dokümanlardadır.*
