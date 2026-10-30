<div align="center">

<img src="docs/ikon.png" width="104" alt="Yıldız Akını ikonu">

# Yıldız Akını

**Neon galakside hayatta kal.**

Tek dosyalık HTML5 uzay savaşı. Tarayıcıda aç, telefona kur; internet, reklam veya hesap gerekmez.

[![Sürüm](https://img.shields.io/badge/s%C3%BCr%C3%BCm-v9.8-67e8f9?style=flat-square)](CHANGELOG.md)
[![HTML5](https://img.shields.io/badge/HTML5-tek%20dosya-e34f26?style=flat-square&logo=html5&logoColor=white)](yildiz-akini.html)
[![Canvas](https://img.shields.io/badge/Canvas-2D-38bdf8?style=flat-square)](yildiz-akini.html)
[![Android](https://img.shields.io/badge/Android-5.0%2B-3ddc84?style=flat-square&logo=android&logoColor=white)](Yildiz-Akini.apk)
[![Çevrimdışı](https://img.shields.io/badge/%C3%A7evrimd%C4%B1%C5%9F%C4%B1-evet-4ade80?style=flat-square)](#kurulum)
[![Dil](https://img.shields.io/badge/dil-TR%20%2F%20EN-ff5470?style=flat-square)](#english)
[![Lisans](https://img.shields.io/badge/lisans-%C3%B6zel-a78bfa?style=flat-square)](LICENSE)

</div>

![Yıldız Akını v9.8 kapak görseli](docs/kapak.png)

## Oyun nedir?

**Yıldız Akını**, tek bir HTML dosyasında çalışan dikey bir neon uzay savaşı oyunudur. Ateş otomatiktir; sen sadece konumlanır, kaçar ve doğru anda patlarsın. Dalgalar ilerledikçe düşmanlar sertleşir; her beş dalgada bir boss, her üç dalgada bir yükseltme ve 4, 9, 14, 19... dalgalarında 50 düşmanlık akın gelir.

v9.8 **Oynanış 2.0**, savaşa üç yeni katman ekler: **odak modu** (Boşluk/LT/ODAK tuşunu basılı tutunca gemi yavaşlar, nişan daralır ve 2.2 saniyede dolan şarj **delici mızrak** olarak ateşlenir), her pazartesi tohumu yenilenen ve 10 mutatörden birini uygulayan **Haftalık Akın**, ve skoru en fazla %20 kısıtlayan dört maddelik **asistan paketi**. v9.7'nin komuta güvertesi, Hangar 2.0, Yükseltme 2.0 ve erişilebilirlik ayarları; v9.5'in aksiyon ısısı, öldürme zinciri, şarapnel/nova ve bloom katmanı; v9.4'ün 15 füzyonu, kanat filosu, düellosu ve altın ışını aynen çalışmaya devam eder.

Oyun tamamen çevrimdışıdır. Ne bir sunucu, ne bir hesap, ne de çalışma anında indirilen bir dosya vardır: gemi, düşman, boss ve bölge sanatı HTML'in içine gömülüdür; müzik ve efektler Web Audio API ile anlık üretilir. Tek dosyayı kopyaladığında tüm sanat da yanında gelir.

## v9.8'in öne çıkanları

| Alan | İçerik |
|---|---|
| **Odak ve mızrak** | Boşluk, gamepad LT/RT veya dokunmatik ODAK tuşu basılıyken gemi %48 yavaşlar, yayılım %55 daralır, hasar %12 ve mermi hızı %18 artar. 2.2 saniyede dolan şarj, 4.2× hasarlı ve 8 düşman delen bir mızrak olarak otomatik ateşlenir; HUD'da şarj halkası ve "MIZRAK HAZIR" bildirimi görünür. |
| **Haftalık Akın** | Her pazartesi yenilenen tohum (`mulberry32(weekIdx()*7919+17)`) ve 10 mutatörden biri (Sürü, Zırh, Hızlı Ateş, Keskin Nişancı, Altın Akın, Elit Dalga, Meteor Yağmuru, Öfke, Cam Gövde, Titan). Ayrı haftalık rekor, haftalık tablo ve ana menüde HAFTA çipi. |
| **Asistan paketi** | OYNANIŞ sekmesinde dört isteğe bağlı yardım: Oto Bomba (ölümcül hasarda bombayı harcar), Nişan Yardımı (mermiler en yakın hedefe hafifçe yönelir), Yavaş Mermi (%15) ve Yedek Can (+1). Her açık asistan skoru %5 azaltır, taban %80'dir. |
| **Komuta güvertesi** | Ana menü; sezon şeridi, gemi vitrini, dört gemi/mod/zorluk/hafta çipi, büyük BAŞLA düğmesi, 3×3 kutucuk ızgarası ve günlük operasyon kartıyla tek ekranda toplanır. |
| **Hangar 2.0** | Gemi karuseli, canlı hız/ateş/can/bomba çubukları, pasif yetenek kartı, sayfalı 16 skin galerisi ve geliştirme ağacı/koleksiyon/füzyon kısayolları. |
| **Yükseltme 2.0** | Nadirlik renkli kartlar, kademe pipleri, NEW rozetleri; 30 coin'e yenileme ve +20 coin ile atlama. |
| **Duraklatma ve sonuç** | Duraklatmada dalga/kill/zincir özeti, donanım çipleri ve günlük hedef; sonuçta S/A/B/C/D derece halkası, para/toz/sezon XP dökümü. |
| **Erişilebilirlik** | ARAYÜZ sekmesi: sol el düzeni, sade HUD, nişan çizgisi ve sayfa animasyonu. Dokunmatik tuşlar ve bomba/can göstergeleri aynalanır. |
| **Altı yeni skin** | `void`, `reactor`, `prism`, `wraith`, `chrono` ve `zenith`; kombo, dalga, füzyon, süre ve sezon koşullarıyla açılır. Toplam 16. |
| **Aksiyon ısısı** | 0–100 arası bir metre, beş kademe (SOĞUK · ISINIYOR · HIZLI · ÖFKELİ · KAOS). Isı yükseldikçe ateş hızı %22'ye, hasar %20'ye kadar artar; kademe atlayışı ekran bandı, halka ve sesle duyurulur. Zincir sürerken ısı 1.7/sn, zincir boşken 3.4/sn soğur. Hasar almak ısıyı 30 puan düşürür ve zinciri sıfırlar. |
| **Öldürme zinciri** | Her öldürme 2.4 saniyelik pencereyi yeniler. 6 zincirden sonra her öldürme 2–4 şarapnel mermisi saçar; her 10 zincirde 92–172 px yarıçaplı nova patlar. Nova zinciri derinleştirir ama sonsuz döngüye girmez (en fazla 2 iç içe tetikleme). |
| **Görsel katman** | 120 × 180 çözünürlüklü bloom tamponu (en fazla 48 ışık lekesi), şarapnel yıldız patlamaları, nova halkaları, ısı ve zincir HUD'u. Tümü `fxLevel()`, parçacık bütçesi, `fpsCap`, pil tasarrufu ve azaltılmış hareket ayarlarına bağlıdır. |
| **300+ entegre özellik** | 63 koşu yükseltmesi · 37 düşman (17 temel + 20 varyant) · 11 boss (5 temel + 6 varyant) · 10 mod · 9 galaksi bölgesi · 68 başarım · 15 güçlendirme · 6 gemi · 15 füzyon · 16 skin · 3 çip · 7 mağaza ürünü · 3 iz · 2 patlama · 7 rozet · 16 kampanya modifikasyonu · 19 sezon ödülü · 3 zorluk · 9 görev türü · 8 kampanya hedefi — canlı sayım **327** kayıt. Ayrı bir "300 İÇERİK" sekmesi yoktur. |
| **15 gemi füzyonu** | Altı geminin tüm ikili eşleşmeleri (C(6,2) = 15). 6. dalgadan sonra yükseltme kartlarında çıkar, profiline kalıcı yazılır ve çiftteki iki gemiden biriyle uçarken etkindir. |
| **Kanat filosu** | Füzyon sayısına bağlı 0–3 kalıcı eskort. 1 füzyonda bir, 3'te iki, 5'te üç kanat uçar; en yakın düşmana 560 px içinde otomatik ateş eder. |
| **Çevrimdışı düello** | 60 saniyelik 1v1: sen ve yapay zekâ rakip aynı dalgada avlanır. En çok avlayan kazanır; galibiyet coin, toz ve "Düellocu" başarımı verir. |
| **Altın ışın** | 2.6 saniye boyunca oyuncunun kolonunu delip geçen, düşmanları ve modülleri yakan güçlendirme. HUD'da kalan süre sayacı gösterilir. |
| **Kanatlı bildirimler** | Kombo eşiklerinde `İYİ!`, `HARİKA!`, `MÜKEMMEL!`, `İNANILMAZ!`, `EFSANE!` yazıları dört altın tüylü enerji kanadıyla açılır. |
| **Overdrive + boss modülleri** | Graze, kill ve modül yıkımıyla dolan Overdrive 6.5 saniye sürer. Her boss iki yörünge taretle gelir; modüller hayattayken boss hasarı ×0.72, ikisi de yıkılınca ×1.12 zırh kırılması uygulanır. |
| **Daha kalabalık dalgalar** | Normal dalga tabanı `12 + 4.6n` (en fazla 150 kayıt); dalga ortasında 3–8 düşmanlık takviye. Aktif düşman tavanı normalde 72, akında 84, pil tasarrufunda 48. Aynı karede en fazla 5 spawn. |
| **Boss korumaları** | Boss dalgaları 8–28 koruma düşmanıyla gelir; boss'u öldürsen bile korumalar temizlenene kadar dalga bitmez. |
| **Bonus kampanya** | 5 halka × 60 görev = 300 görev; her görevin adı, hedefi ve modifikasyonları var. İlk temizlemede ödül, tekrar oynayışta yok. |
| **Sanat paketi** | Kenney Space Shooter Redux gemi/düşman/boss parçaları, NASA bölge fotoğrafları ve ambientCG metal dokusu; hepsi WebP olarak HTML'e gömülü. |
| **Müzik** | Phonk esintili prosedürel parçalar: 808 bas, cowbell melodi, trap davulları, plak cızırtısı. |

## Ekran görüntüleri

| Ana menü | Savaş | Boss |
|:---:|:---:|:---:|
| <img src="docs/screens/menu.jpg" width="230" alt="Ana menü"> | <img src="docs/screens/savas.jpg" width="230" alt="Aksiyon ısısı ve zincir HUD'u"> | <img src="docs/screens/boss.jpg" width="230" alt="Boss savaşı"> |
| **Boss modülleri** | **50'lik akın** | **Kanatlı bildirim** |
| <img src="docs/screens/modul.jpg" width="230" alt="Yörüngeli boss modülleri"> | <img src="docs/screens/horde.jpg" width="230" alt="50 düşmanlık akın dalgası"> | <img src="docs/screens/kanat.jpg" width="230" alt="Altın kanatlı kombo bildirimi"> |
| **Füzyonlar** | **Düello** | **Dokunmatik HUD** |
| <img src="docs/screens/fuzyon.jpg" width="230" alt="15 gemi füzyonu"> | <img src="docs/screens/duel.jpg" width="230" alt="Çevrimdışı 1v1 düello"> | <img src="docs/screens/dokunmatik.jpg" width="230" alt="Dokunmatik kontroller"> |
| **Hangar** | **Yükseltme ağacı** | **Görevler** |
| <img src="docs/screens/hangar.jpg" width="230" alt="Hangar"> | <img src="docs/screens/agac.jpg" width="230" alt="Yükseltme ağacı"> | <img src="docs/screens/gorevler.jpg" width="230" alt="Günlük ve haftalık görevler"> |
| **Başarımlar** | **İstatistikler** | **Koleksiyon** |
| <img src="docs/screens/basarimlar.jpg" width="230" alt="Başarımlar"> | <img src="docs/screens/istatistik.jpg" width="230" alt="İstatistikler"> | <img src="docs/screens/koleksiyon.jpg" width="230" alt="Koleksiyon"> |
| **Haftalık Akın** | **Odak ve mızrak** | **Oynanış asistanları** |
| <img src="docs/screens/haftalik.jpg" width="230" alt="Haftalık mutatör ve rekor ekranı"> | <img src="docs/screens/odak.jpg" width="230" alt="Odak şarjı ve delici mızrak"> | <img src="docs/screens/ayarlar-oynanis.jpg" width="230" alt="Asistan paketi ayarları"> |

### Bonus kampanya ve koşu sonucu

| Bonus kampanya | Koşu sonucu |
|:---:|:---:|
| <img src="docs/screens/kampanya.jpg" width="300" alt="300 görevlik bonus kampanya haritası"> | <img src="docs/screens/sonuc.jpg" width="300" alt="Koşu sonucu ekranı"> |

### Arayüz 6.0

| Yükseltme 2.0 | Duraklatma 2.0 | Arayüz ayarları |
|:---:|:---:|:---:|
| <img src="docs/screens/yukseltme.jpg" width="230" alt="Nadirlik renkli yükseltme kartları"> | <img src="docs/screens/duraklat.jpg" width="230" alt="Koşu özetli duraklatma ekranı"> | <img src="docs/screens/ayarlar.jpg" width="230" alt="Sol el ve HUD ayarları"> |

## İndir

### Android · APK

[**Yildiz-Akini.apk**](Yildiz-Akini.apk) · **~0.8 MB** · Android 5.0+ · sürüm **9.8** (versionCode 19)

- Tam ekran, portre, ikonlu ve çevrimdışı.
- APK **internet izni istemez**; hiçbir veri cihazdan çıkmaz.
- Sideload için debug anahtarıyla imzalanmıştır. Play Protect "bilinmeyen uygulama" uyarısı verebilir.

### Bilgisayar · Tarayıcı

[**yildiz-akini.html**](yildiz-akini.html) · **~1.4 MB** · Chrome, Edge, Firefox veya Safari

Dosyayı indirip çift tıklaman yeterli. Kurulum, sunucu veya internet bağlantısı gerekmez.

> Sürüm notları: [CHANGELOG.md](CHANGELOG.md) · Kararlı sürüm: [Releases](https://github.com/Saklabann/yildiz-akini/releases)

## Oyun modları

| Mod | Açıklama |
|---|---|
| **Klasik** | Ana deneyim. Boss her 5 dalgada, yükseltme her 3 dalgada, 50 düşmanlık akın 4, 9, 14, 19... dalgalarında. |
| **Sonsuz** | 20. dalgeden sonra tehlike durmadan artar; amaç hayatta kalabildiğin kadar kalmak. |
| **Zaman Yarışı** | 90 saniyede en yüksek skor. Kalan süre bonus, skor çarpanı %30. |
| **Günlük Görev** | Günün tohumu: herkes aynı akışı oynar. Günde bir kez ödül. |
| **Kusursuz** | Can kaybettiğin an koşu biter. Kalkan emişi serbesttir. |
| **Boss Akını** | Sadece boss savaşları; her dalgada boss, her 2 dalgada yükseltme. |
| **Tek Can** | Tek canla başla; yeniden canlanma ve başlangıç kalkanı yok. |
| **Kaos** | Her dalgada rastgele hız, yoğunluk, boss canı ve elit modifikasyonları. |
| **Haftalık Akın** | Her pazartesi yenilenen tohum ve 10 mutatörden biri; ayrı haftalık rekor ve tablo. |
| **Hızlı Akın** | 2 dalgada bir yükseltme; tempolu, kısa koşu. |

## Gemiler ve füzyonlar

| Gemi | Profil | Aktif yetenek |
|---|---|---|
| **Denge** | Dengeli hız ve ateş | Overload — kısa süreli ateş gücü patlaması |
| **Şimşek** | Çok hızlı, kırılgan | Blink — anlık ışınlanma |
| **Kale** | Dayanıklı, yavaş | Barrier — geçici kalkan |
| **Nova** | Seri ateş, dengeli gövde | Supernova — ekranı yakıp geçen patlama |
| **Hayalet** | Çevik ama kırılgan | Phase — kısa süreli dokunulmazlık |
| **Titan** | Ağır zırh, dört bomba | Salvo — roket yağmuru |

Her geminin kendi **Motor / Gövde / Silah / Çekirdek** dallarından oluşan 11 düğümlük kalıcı yükseltme ağacı vardır. Yükseltmeler coin ile alınır ve gemiye özeldir.

Altı geminin tüm ikili eşleşmeleri **15 füzyon** üretir. Füzyon kartı 6. dalgadan sonra yükseltme ekranında çıkar; seçildiğinde kalıcı olarak profiline yazılır ve iki gemiden biriyle uçarken etkin olur. Örnekler:

| Füzyon | Etki |
|---|---|
| **Fırtına Dengesi** (Denge + Şimşek) | Ateş hızı +%10, hız +%7 |
| **Kale Dengesi** (Denge + Kale) | +1 can, +4 kalkan |
| **Nova Dengesi** (Denge + Nova) | +1 hasar, +%8 kritik |
| **Yıldırım Zırhı** (Şimşek + Kale) | Hız +%6, +1 can |
| **Savaş Roketi** (Şimşek + Titan) | +1 hasar, hız +%5 |
| **Nova Kalesi** (Kale + Nova) | Nova +1, +1 hasar |
| **Gölge Titanı** (Hayalet + Titan) | +1 can, diken +1, hız +%5 |

Füzyonlar ayrıca **kanat filosu** besler: 1 füzyonda bir, 3'te iki, 5'te üç eskort gemisi yanında uçar ve otomatik ateş eder.

## İlerleme ve ekonomi

- **Coin**: koşu içinde ve dışında kazanılır; mağaza ve gemi ağacında harcanır.
- **Yıldız tozu**: nadir para birimi; özel mağaza ürünleri ve kozmetikler için kullanılır.
- **Mağaza**: başlangıç kalkanı, ekstra bomba, mıknatıs, silah seviyesi, altın paleti, yan silah çipi ve öfke.
- **Görevler**: 3 günlük + 3 haftalık görev; ilerleme otomatik sayılır, ödül elle alınır. Haftalık görevler pazartesi yenilenir.
- **Kozmetikler**: 16 skin, 3 iz ve 2 patlama efekti; kill, dalga, boss, başarım ve sezon koşullarıyla açılır.
- **Sezon**: "Neon Şafak" 20 seviye; puan, boss ve görevlerden XP. Ödüller coin, yıldız tozu, rozet ve Aurora/Tutulma görünümleri.
- **Eğitim**: İlk açılışta hareket, ateş, bomba ve yükseltmeyi öğreten 4 kısa görev. Atlanabilir, menüden yeniden başlatılabilir.
- **Yedekleme**: Profili panoya kopyala veya `.txt` indir; geri yüklerken sürüm ve sağlama toplamı doğrulanır.
- **Kayıtlar**: cihazda `localStorage` içinde tutulur. Hesap veya bulut gerekmez; yedek kodu `YA2.` biçimindedir.

## Düello

Ana menüdeki **DÜELLO** satırı 60 saniyelik çevrimdışı 1v1 başlatır. Sen ve rakip yapay zekâ aynı dalgada avlanırsınız; süre bitince en çok düşman avlayan kazanır.

- Rakip gemi kendi nişan sistemiyle ateş eder, hasar alınca kısa süre sarsılır ve yeniden konumlanır.
- Rakibin öldürdüğü düşmanlar senin skoruna yazmaz; ikiniz de aynı anda aynı hedefe yönelebilirsiniz.
- Galibiyet `30 + 2 × av` coin, 1 yıldız tozu ve ilk 5 galibiyette **Düellocu** başarımı verir.
- En iyi av sayısı ve toplam düello sayısı profilde saklanır.

## Bonus kampanya

Ana menüdeki **BONUS KAMPANYA** satırı 300 görevlik isteğe bağlı bir kampanya açar. 5 halka ve her halkada 60 görev vardır; tüm görevler baştan açıktır.

- Her görevin kendi adı, hedefi, modifikasyonları, yıldız derecesi ve ilk temizleme ödülü vardır.
- Hedef türleri: dalga, kill, boss, puan, kombo, süre, hasarsız dalga ve para.
- Modifikasyonlar: hızlı/yavaş düşman, sık/seyrek akın, güçlü/zayıf boss, tek/bol can, hızlı ateş, büyük mermi, kritik, kalkan, meteor, elit, altın ve dar hedef.
- İlk temizlemede ödül verilir; aynı görevi tekrar oynayınca ödül verilmez. Daha düşük yıldız, kayıtlı en iyi sonucun üzerine yazmaz.

## Kontroller

| Girdi | İşlev |
|---|---|
| **WASD / Ok tuşları / Fare / Dokunma / Gamepad** | Hareket |
| **Otomatik** | Ateş |
| **Shift** | Dash |
| **Boşluk / Gamepad LT·RT / ODAK tuşu** | Odak: yavaşla, nişanı daralt, mızrak şarj et |
| **E** | Gemi yeteneği |
| **B** | Bomba |
| **U** | Öfke (rage) |
| **1 · 2 · 3** | Yükseltme seçimi |
| **P / Esc** | Duraklat |
| **M** | Sesi aç/kapat |
| **F** | Tam ekran |

Mobilde ekranın sol yarısını sürükleyerek hareket edersin; sağ alttaki butonlar bomba, dash ve yetenek içindir. Arayüz tek elle oynanacak şekilde yerleştirilmiştir.

## Kurulum

### Android

1. [Yildiz-Akini.apk](Yildiz-Akini.apk) dosyasını telefona indir.
2. Dosyayı aç. "Bilinmeyen kaynaklara izin ver" istenirse tarayıcı/dosya yöneticisi için izni ver.
3. Play Protect uyarısında **Yine de yükle** seçeneğini kullan.
4. **Yıldız Akını** ikonuna dokun.

Ayrıntılı adımlar: [APK-KURULUM.txt](APK-KURULUM.txt)

### Windows / macOS / Linux

1. [yildiz-akini.html](yildiz-akini.html) dosyasını indir.
2. Çift tıkla. Oyun varsayılan tarayıcıda açılır.
3. Tam ekran için **F** tuşuna bas.

## Teknik

| | |
|---|---|
| **Motor** | Saf HTML5 Canvas 2D, tek IIFE, bağımlılık yok |
| **Mantıksal çözünürlük** | 480 × 720 (dikey), DPR'ye duyarlı ölçekleme |
| **Ses** | Web Audio API ile phonk esintili prosedürel müzik: 808 bas, cowbell melodi, trap davulları, plak cızırtısı |
| **Kayıt** | `localStorage` (`ya_profile`, `ya_settings`) |
| **Dosya boyutu** | HTML ~1.4 MB · APK ~0.8 MB (gömülü WebP sanat dahil) |
| **APK** | WebView sarmalayıcı · `com.saklabann.yildizakini` · v9.8 (versionCode 19) · minSdk 21 · targetSdk 29 |
| **Ağ** | Hiçbir ağ isteği yok; APK'da `INTERNET` izni yok |
| **Derleme** | Gradle'sız: `aapt2` + `javac` + `d8` + `jarsigner` |

Mimari ve kod düzeni: [docs/TEKNIK.md](docs/TEKNIK.md)

## SSS

**Oyun ücretsiz mi?**
Evet. Reklam, uygulama içi satın alma veya abonelik yoktur.

**İnternet gerekiyor mu?**
Hayır. Hem HTML hem APK tamamen çevrimdışı çalışır.

**Verilerim nereye gidiyor?**
Hiçbir yere. Skorlar, ayarlar ve koleksiyon yalnızca cihazın yerel deposunda tutulur.

**300 içerik sekmesi nerede?**
Kaldırıldı. 300+ özellik ayrı bir liste sekmesi yerine doğrudan oynanışa, hangara, mağazaya, başarımlara ve bonus kampanyaya dağıtıldı.

**Güncelleme kayıtlarımı siler mi?**
Aynı paket adı ve imzayla üzerine kurulduğunda hayır.

**Neden Play Protect uyarısı çıkıyor?**
APK mağaza dışı dağıtım için kendi debug anahtarıyla imzalandığından Google sertifika zincirini tanımaz. Uyarı beklenen bir durumdur.

**iOS'ta oynanır mı?**
HTML dosyası Safari'de çalışır. Şu an imzalı bir iOS paketi yoktur.

**Kaynak kodu değiştirebilir miyim?**
Depo özeldir ve tüm hakları saklıdır. Kullanım koşulları için [LICENSE](LICENSE) dosyasına bak.

## Yol haritası

v9.8 ile odak/şarjlı mızrak, haftalık mutatör modu ve asistan paketi oyuna eklendi; v9.7'nin komuta güvertesi, Hangar 2.0, Yükseltme 2.0 ve ARAYÜZ ayarları korunuyor. Sonraki sürümlerde yeni mutatörler, asistan istatistikleri ve sezon genişlemesi değerlendirilecek.

Ayrıntılar: [ROADMAP.md](ROADMAP.md)

## English

**Yıldız Akını** (Star Rush) is a single-file, offline neon space shooter built with HTML5 Canvas and Web Audio. It ships as both a standalone HTML game and a tiny Android APK.

- **300+ integrated features**: 63 run perks, 37 enemies (17 base + 20 variants), 11 bosses (5 base + 6 variants), 10 modes, 9 regions, 68 achievements, 15 power-ups, 6 ships, 15 fusions, 16 skins, 3 chips, 7 shop items, 3 trails, 2 explosion styles, 7 badges, 16 campaign modifiers, 19 season rewards, 3 difficulties, 9 mission types and 8 campaign goals — 327 live entries
- **Gameplay 2.0**: hold Space / LT / the FOCUS button to slow the ship, tighten the spread and charge a piercing lance (2.2 s, 4.2× damage, pierces 8 enemies)
- **Weekly Raid**: a deterministic weekly seed and one of 10 mutators (Swarm, Armor, Rapid Fire, Sniper, Gold Rush, Elite Wave, Meteor Rain, Frenzy, Glass Hull, Titan), with a separate weekly best and board
- **Assist pack**: Auto Bomb, Aim Assist, Slow Bullets and Spare Life; each active assist costs 5% score with an 80% floor
- **UI 6.0**: command-deck main menu, Hangar 2.0 carousel with stat bars and a paged 16-skin gallery, rarity-colored upgrade cards with reroll/skip, a pause build summary, and an S–D grade ring with a reward breakdown on the results screen
- Left-hand layout, minimal HUD, aim guide and interface-animation toggles in the new UI settings tab
- Six new skins (void, reactor, prism, wraith, chrono, zenith), 16 total
- No separate "300 content" tab: the content is woven into gameplay, the hangar, the shop, achievements and the bonus campaign
- **Action heat** (0–100, five tiers): up to 22% faster fire and 20% more damage, with tier callouts; cools down 1.7/s while a kill chain is alive and 3.4/s when it is not
- **Kill chain**: every kill refreshes a 2.4 s window; 6+ chain scatters shrapnel bullets, every 10th kill detonates a nova that can chain at most twice
- **Low-res bloom buffer** (120 × 180, max 48 blobs) plus shrapnel stars and nova rings, all gated by `fxLevel()`, particle budget, FPS cap, battery saver and reduced motion
- **15 ship fusions**: every pair of the six ships, permanent once picked from wave 6 upgrade cards, active while flying either ship of the pair
- **Wing fleet**: 0–3 permanent escorts unlocked at 1, 3 and 5 fusions; they auto-fire at the nearest enemy within 560 px
- **Offline 1v1 duel**: 60 seconds, you versus a rival AI, most kills wins; rewards coins, dust and the Duelist achievement
- **Golden beam**: 2.6 s piercing column power-up with a HUD countdown
- **Winged callouts**: GOOD!, GREAT!, EXCELLENT!, AMAZING!, LEGEND! with four-feather golden energy wings
- **Overdrive** meter and orbiting boss modules: ×0.72 damage while modules live, ×1.12 armor break when both are destroyed
- Denser waves: base count `12 + 4.6n` (max 150 queue entries), mid-wave reinforcement, active enemy cap 72 (84 in horde, 48 in battery saver), at most 5 spawns per frame
- Boss waves arrive with 8–28 escorts; the wave does not end until escorts are cleared
- Embedded art pack: Kenney Space Shooter Redux ships/enemies/bosses, nine NASA region backdrops and an ambientCG metal texture, all inlined as WebP
- 300-mission bonus campaign: 5 chapters × 60 missions, all open, first-clear rewards only
- 10 modes including Boss Rush, One Life, Chaos and Weekly Raid
- Daily and weekly missions, 68 achievements, detailed stats
- Skippable 4-step tutorial and a 20-level season with badges
- Validated profile backup export/import
- A 50-enemy surge every 4th wave, with V formations, divers, rushers, tanks and elites
- Weapon-specific trails, enemy-specific explosions, boss armor breaks and a skippable defeat cinematic
- Layered galaxy backgrounds with distant planets, nebulae and parallax star clusters
- Effect quality, FPS cap, battery saver and touch sensitivity settings
- Touch, keyboard, mouse and gamepad support
- Turkish and English UI, colorblind mode, reduced motion
- No ads, no accounts, no analytics, no network requests

Download the [APK](Yildiz-Akini.apk) or the [HTML file](yildiz-akini.html) and play.

## Lisans

© 2026 Saklabann. Tüm hakları saklıdır. Bu depo ve içindeki oyun; kod, görsel ve ses varlıkları dahil olmak üzere yazılı izin olmadan çoğaltılamaz, dağıtılamaz veya ticari olarak kullanılamaz. Ayrıntılar için [LICENSE](LICENSE). Üçüncü taraf sanat varlıklarının kaynak ve lisansları [CREDITS.md](CREDITS.md) dosyasındadır.

---

<div align="center">

**İyi akınlar.** · [Sürüm notları](CHANGELOG.md) · [Güvenlik](SECURITY.md) · [Katkı](CONTRIBUTING.md)

</div>
