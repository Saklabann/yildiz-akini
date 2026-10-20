# Teknik Dokümantasyon

## Genel bakış

Yıldız Akını, tek bir HTML dosyası içinde çalışan dikey bir uzay savaşı oyunudur. Harici kütüphane, derleme adımı, görsel dosyası veya ses dosyası yoktur. Tüm çizimler Canvas 2D, tüm sesler Web Audio API ile çalışma anında üretilir.

| | |
|---|---|
| Dosya | `yildiz-akini.html` |
| Boyut | ~252 KB |
| Dil | JavaScript (ES2017+), HTML, CSS |
| Çözünürlük | 480 × 720 mantıksal; DPR'ye duyarlı |
| Kayıt | `localStorage` |
| Ağ | Yok |
| Bağımlılık | Yok |

## Çalışma akışı

Kod tek bir IIFE içinde kapsüllenmiştir. Kabaca sıra şöyledir:

1. **Sabitler ve yardımcılar** — `W`, `H`, `TAU`, matematik ve biçimlendirme fonksiyonları.
2. **Yerel depolama sarmalayıcı** — `LS.get` / `LS.set`; bozuk JSON'a karşı korumalı.
3. **Veri tabloları** — gemiler, yetenekler, skinler, ağaç, perkler, mağaza, modlar, bölgeler, başarımlar, görev havuzları, metinler.
4. **Kalıcı durum** — `P` profili (coin, rekorlar, açılanlar, istatistikler) ve `S` ayarları.
5. **Çalışma durumu** — `state` (dalga, düşmanlar, mermiler, süre, mod).
6. **Girdi katmanı** — klavye, fare, dokunma, gamepad; tek bir hareket vektörüne indirgenir.
7. **Ses motoru** — prosedürel osilatörler, gürültü ve filtrelere dayalı müzik/efekt.
8. **Oyun döngüsü** — `requestAnimationFrame`; sabitlenmiş delta ile güncelleme ve çizim.
9. **Arayüz** — menü, hangar, ağaç, koleksiyon, görevler, istatistik, oyun sonu ekranları.
10. **Kayıt** — profil ve ayarlar değiştiğinde `localStorage`'a yazılır.

## Koordinat sistemi

Oyun 480 × 720 mantıksal alanda tasarlanır. Canvas, cihaz piksel oranına göre ölçeklenir; fiziksel çıktı tipik olarak 600 × 900'dür. Tüm çarpışma ve yerleşim hesapları mantıksal koordinatlarda yapılır. Bu sayede aynı kod farklı ekranlarda tutarlı davranır.

- Gemi çarpışma yarıçapı: 11–15 px (gemiye göre)
- Mermi hızları: ~590–700 px/s
- Gemi hızları: ~245–400 px/s
- Maksimum delta: kare atlamalarını önlemek için sınırlandırılır

## Önemli veri tabloları

| Tablo | İçerik |
|---|---|
| `SHIPS` | 6 gemi; hız, ateş bekleme, can, hitbox, bomba, dash ve yetenek |
| `ABIL` | 6 aktif yetenek; bekleme, süre ve renk |
| `SKINS` | 8 görsel palet |
| `TREE` | Gemi başına 4 dal, 11 düğüm ve artan coin maliyeti |
| `PERKS` | 30 koşu içi yükseltme |
| `SHOP` | 7 kalıcı mağaza ürünü |
| `GMODES` | 6 oyun modu |
| `REGIONS` | 5 bölge paleti |
| `ACHS` | 31 başarım |
| `MISS_POOL` / `WPOOL` | Günlük ve haftalık görev havuzları |

## Kayıt şeması

İki anahtar kullanılır:

- `ya_profile` — kalıcı ilerleme: coin, toz, rekorlar, oynanan gemiler, açılan skinler, başarımlar, gemi ağaçları, görev durumu, istatistikler.
- `ya_settings` — dil, ses, sarsıntı, parçacık kalitesi, renk körü modu, azaltılmış hareket, FPS sayacı.

Şema yüklenirken eksik alanlar varsayılanlarla tamamlanır. Bu, eski sürümlerden gelen profillerin bozulmadan açılmasını sağlar.

## Görev üretimi

- **Günlük görev:** tarih (`YYYY-M-D`) tohum olarak kullanılır; aynı gün herkeste aynı üç görev üretilir.
- **Haftalık görev:** haftanın pazartesi tarihi anahtarı FNV-1a ile karıştırılıp tohum yapılır.
- Görevler `pickTasks` ile havuzdan seçilir; hedef aralıkları sabittir.
- İlerleme olay tabanlıdır (`missAdd`); ödül talebi ayrı bir kullanıcı eylemidir.

## Bölgeler ve müzik

`regionIdx()` dalga numarasından bölgeyi hesaplar: `floor((wave - 1) / 5) % 5`. Bölge; arka plan renklerini, yıldız tonunu, sis katmanını ve müziğin kök sesini değiştirir. Müzik tamamen prosedüreldir; bölgeye göre yalnızca transpozisyon uygulanır.

## APK

APK, Gradle kullanılmadan elle derlenir:

1. `aapt2 compile` ile kaynaklar paketlenir.
2. `aapt2 link` ile `base.apk` üretilir; `assets/` içine HTML kopyalanır.
3. `javac` ile `MainActivity.java` derlenir.
4. `d8` ile `classes.dex` üretilir ve APK'ya eklenir.
5. `jarsigner` ile debug anahtarı kullanılarak imzalanır.

`MainActivity`, HTML'i `assets/yildiz-akini.html` üzerinden okur ve `loadDataWithBaseURL("https://appassets.local/", ...)` ile WebView'e yükler. Böylece `localStorage` kökeni sabit kalır ve güncellemelerde kayıtlar korunur.

| | |
|---|---|
| Paket | `com.saklabann.yildizakini` |
| Sürüm | 8.0 (versionCode 8) |
| minSdk | 21 (Android 5.0) |
| targetSdk | 29 |
| İzinler | Yok |
| İmza | Debug (sideload) |

## Geliştirme

Tarayıcıda açmak yeterlidir:

```powershell
start yildiz-akini.html
```

Yerel sunucu ile test etmek için:

```powershell
python -m http.server 8125 --bind 127.0.0.1
```

Ardından `http://127.0.0.1:8125/yildiz-akini.html` adresini aç.

## Test kontrol listesi

- Altı modun tamamı başlatılıp bitirilebiliyor.
- Altı gemi ve altı yetenek beklendiği gibi çalışıyor.
- 25+ dalga boyunca bölge ve boss geçişleri sorunsuz.
- Günlük/haftalık görev ilerlemesi ve ödül talebi doğru.
- Ağaç satın alımları coin düşürüyor ve etkili istatistiklere yansıyor.
- Kilitli skin/iz/patlama seçilemiyor; eski kayıt güvenli varsayılana dönüyor.
- Oyun sonu ekranı önceki rekorla karşılaştırma yapıyor.
- 360 px genişlikte dokunmatik HUD taşmıyor.
- TR/EN geçişinde eksik anahtar yok.
- Konsolda hata veya uyarı yok.

## Performans notları

- Parçacık yoğunluğu ayarlardan düşürülebilir.
- Ekran sarsıntısı ve azaltılmış hareket bağımsız kapatılabilir.
- Arka plana alınan sekmede oyun otomatik duraklar.
- Çizim tek canvas üzerinde yapılır; DOM katmanı yalnızca HUD için kullanılır.
