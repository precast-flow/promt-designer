# Kalıp tahtası, öncelik sırası ve “bekleyen işler” raporu

## Kullanıcılar

Öncelikle **üretim şefi** ve **vardiya amiri**; destekleyici olarak planlama.

## Amaç — bütüncül görünüm

Kullanıcı şunu tek bakışta görmeli:

- Hangi **kalıplar** meşgul / boş / arızalı.
- Hangi **emir / parça** hangi kalıba planlı veya öneriliyor.
- **Bugünün** iş yükü ile **bekleyen kuyruk** arasındaki fark.

## Önerilen ekranlar (ayrı veya sekmeli)

### 1) Kalıp tahtası (board)

- Eksenler: **Kalıp** (satır veya kolon) × **Zaman** (vardiya veya gün) — MVP’de basitleştirilebilir: sadece “kalıp listesi + üzerindeki iş kartı”.
- Kart içeriği: emir no, parça kodu, durum rengi (gri tonları), sorumlu ekip.
- **Öneri:** Sistem, plana göre “bu kalıba şu iş önerilir” şeklinde **öneri kartı** (secondary) gösterebilir; onay vardiya amirinde.

### 2) Bekleyen işler / öncelik raporu

- Liste veya sıralı tablo: emir, parça, bekleyen gün sayısı, risk etiketi, önerilen sıra.
- **Sıralama:** sürükle-bırak (mock) veya öncelik skoru sütunu.
- **Filtre:** hat, proje terminine göre aciliyet, malzeme türü (mock).

### 3) Şef “sabah” akışı ile bağlantı

Şef önce özet dashboard’a bakar → öncelik raporunda sırayı netleştirir → kalıp tahtasına atama yapar (bkz. `02-gunluk-ve-sabah-akisi.md`).

## Rol farkları

- **Şef:** Tüm fabrika bağlamında sıra ve atama.
- **Vardiya amiri:** Sadece kendi vardiyası için atama (politikaya göre).
- **Usta:** Kendi istasyonu kartları (daha dar görünüm).

## MVP sınırı

Tam **optimizasyon motoru** yok; **manuel sıra + görsel öneri** yeterli. Optimizasyon ileri faz.
