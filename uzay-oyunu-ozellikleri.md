# Uzay / Space Shooter Oyun Özellikleri — 94 Fikir

> Kaynak taraması: Wikipedia (Shoot 'em up, Bullet hell), Shmups Wiki "Boghog's bullet hell shmup 101", Game Developer "Designing smart, meaningful SHMUPs", TV Tropes ve mobil uzay oyunu mağaza açıklamaları.
>
> Durum işaretleri **Yıldız Akını v10.0** için: ✅ var · 🟡 kısmen var · ❌ yok
>
> v10.0, 300+ özelliği oyunun mevcut sistemlerine dağıtır; ayrı bir "300 içerik" sekmesi yoktur. 300 görevlik bonus kampanya, 10 mod, 37 düşman, 11 boss ve çok daha kalabalık dalgalar korunur. v8.2 eğitim/sezon/yedekleme, v8.3 sunum katmanı, v8.4 50 düşmanlık akın, v9.2 gömülü sanat paketi, v9.3 Overdrive ve boss modülleri, v9.4 füzyon/kanat/düello/altın ışın, v9.5 aksiyon ısısı/zincir/şarapnel/nova/bloom, v9.6 gemi pasifleri/zincir ödülleri, v9.7 komuta güvertesi/hangar 2.0/erişilebilirlik, v9.8 odak/şarjlı mızrak/haftalık mutatör/asistan paketi, v9.9 Fırtına/Ray/Nova evrim yolları ve v10.0 gemi imza pasifleri/yetenek düğümü de oyunun parçasıdır.

---

## 1. Kontrol ve oyun hissi

1. **Otomatik ateş** — Oyuncu sadece hareket eder; ateş sürekli açıktır. Mobilde tek elle oynanabilirlik sağlar. ✅
2. **Odak / hassas mod** — Tuşu basılı tutunca gemi yavaşlar, atış daralır. Kurşun cehennemi oyunlarının temel kolaylık/derinlik aracıdır. ✅ (v9.8: Boşluk/LT/ODAK)
3. **Minik hitbox** — Gemi görseli büyük, çarpışma noktası küçüktür. Adil ama zor hissi verir. ✅
4. **Dash / blink** — Kısa mesafeli ani kaçış; bekleme süresiyle dengelenir. ✅
5. **Sürükleme kontrolü** — Parmağı ekranda kaydırınca gemi gecikmesiz takip eder. ✅
6. **Gamepad desteği** — Analog çubuk + tuş eşlemesi. ✅
7. **Vuruş hissi (hit-stop, flash, sarsıntı)** — İsabet anında kısa donma, beyaz parlama, kritik vurgusu ve ekran sarsıntısı. ✅
8. **Duraklat / devam** — Uygulama arka plana atılınca otomatik duraklar. ✅
9. **Tuşları yeniden atama** — Oyuncunun kendi kontrol düzenini kurması. ❌

## 2. Silahlar ve güçlenme

10. **Silah seviyesi / power-up** — Toplanan parçalarla atış genişler, hasar artar. 🟡
11. **Yayılı atış (spread)** — Önü geniş açıyla tarayan atış. 🟡
12. **Lazer / sürekli ışın** — Anlık, dar ve yüksek DPS'li silah. ❌
13. **Güdümlü füze** — Hedefi kendi bulan ikincil silah. ✅
14. **Yörünge drone / option** — Geminin etrafında dönen yardımcı ateş birimi. ✅
15. **Şarjlı atış** — Basılı tutup bırakınca güçlü tek vuruş. ✅ (v9.8: 2.2 sn şarj, delici mızrak)
16. **Bomba / smart bomb** — Ekranı temizleyen sınırlı acil durum kaynağı. ✅
17. **Ultimate / aktif yetenek** — Bekleme süreli özel güç (kalkan, faz, süpernova vb.). ✅
18. **Rage / overdrive** — Hasar aldıkça veya combo ile dolan öfke modu. ✅
19. **Graze (sıyırma)** — Kurşuna değmeden yakınından geçince bonus. ✅
20. **Element / durum etkisi** — Yanma, dondurma, zincirleme hasar. ✅ (v9.0: dondurma ve yanma perkleri)
21. **Absorbe / renk değiştirme** — Ikaruga tarzı polarite: aynı renk kurşunu yutma. ❌

## 3. Hayatta kalma ve kaynak yönetimi

22. **Can / 1UP** — Ekstra hayat ve bunun kazanılması. ✅
23. **Kalkan + rejenerasyon** — Hasarı emen, süreyle yenilenen kalkan. ✅
24. **Tamir / can toplama** — Düşmanlardan düşen onarım paketi. 🟡
25. **Mıknatıs** — Para ve parçaları gemine çeken toplama alanı. ✅
26. **Combo penceresi** — Süre içinde öldürmeye devam edince çarpan büyür. ✅
27. **Continue / jeton** — Ölünce kaldığın yerden devam hakkı. ❌
28. **Risk-ödül bonusu** — Bombasız bitirme, yakın mesafe kill gibi cesaret ödülleri. 🟡
29. **Koşuyu kaydet / devam et** — Uygulama kapanınca run'ı kaldığı yerden sürdürme. ❌

## 4. Düşman ve boss tasarımı

30. **Popcorn sürüleri** — Tek vuruşta ölen, ekranı dolduran küçük düşmanlar. ✅
31. **Formasyon hareketi** — V, dalga, sarmal gibi öğrenilebilir dizilişler. ✅
32. **Sabit turret / platform** — Hareket etmeyen, yönlü ateş eden tehdit. ✅
33. **Taşıyıcı (spawner)** — Sürekli düşman üreten öncelikli hedef. 🟡
34. **Elit varyant** — Normal düşmanın kalkanlı, hızlı veya özel atışlı hâli. ✅ (v9.0: elit düşmanlar)
35. **Ara boss (midboss)** — Bölüm ortasında tempoyu yükselten güçlü düşman. 🟡
36. **Çok fazlı boss** — Can azaldıkça yeni saldırı desenine geçen boss. ✅
37. **Zayıf nokta** — Sadece belirli bir bölgeye hasar verilebilmesi. ❌
38. **Telegraflı saldırı** — Önceden çizgi/alan gösterip sonra ateşleme. ✅ (v8.3: boss nişangâhı ve faz geçişi)
39. **Boss enrage / süre limiti** — Uzayan savaşta boss'un çıldırması. 🟡

## 5. Dalga, seviye ve çevre

40. **Kademeli zorluk** — Dalga ilerledikçe düşman sayısı ve hızı artar. ✅ (v8.4: daha yoğun dalgalar)
41. **Özel set-piece dalga** — Asteroid yağmuru, kuşatma, koridor gibi el yapımı anlar. ✅ (v9.0: 50 düşmanlık akın, 18 asteroid + 6 scout ve boss korumaları)
42. **Bonus / hedef dalgası** — Para balonları veya korunacak müttefik gibi yan hedefler. ❌
43. **Çevresel tehlike** — Asteroit, enkaz ve patlayan varil. ✅
44. **Kara delik / nebula pusu** — Ortamın hareketi ve görüşü değiştirmesi. ❌
45. **Bölge / biome çeşitliliği** — Her 5 dalgada değişen görsel ve müzikal tema. ✅
46. **Parallax arka plan** — Derinlik hissi veren çok katmanlı yıldızlar. ✅ (v8.3: 5 katmanlı galaksi)
47. **Prosedürel sonsuz akış** — Bitmeyen, her koşuda farklılaşan dalgalar. ✅

## 6. Meta ilerleme ve ekonomi

48. **Ana para (coin)** — Koşu içinde ve dışında biriken temel kaynak. ✅
49. **Nadir para (dust)** — Uzun vadeli, değerli yükseltme kaynağı. ✅
50. **Mağaza** — Koşu arasında harcama ve kalıcı güçlenme. ✅
51. **Gemi koleksiyonu** — Farklı hız/can/yetenek profilli gemiler. ✅ (6 gemi)
52. **Gemi bazlı yükseltme ağacı** — Her geminin kendi dalları ve kalıcı bonusları. ✅
53. **Modül / ekipman slotu** — Gemiye takılan silah, kalkan, motor parçaları. ❌
54. **Skin / boya** — Görsel kişiselleştirme; ilerlemeyle açılır. ✅
55. **İz ve patlama efektleri** — Kozmetik ödüller. ✅ (v8.3: düşmana özel patlamalar)
56. **Günlük ve haftalık görevler** — Tekrar oynanabilirliği ayakta tutan hedefler. ✅
57. **Başarımlar** — Uzun vadeli tamamlama listesi. ✅ (68 adet)
58. **Sezon / battle pass** — Dönemsel ödül yolu ve yeni içerik ritmi. ✅ (20 seviye)
59. **Koleksiyon defteri** — Açılan gemi, skin ve kozmetiklerin sergilendiği sayfa. ✅

## 7. Oyun modları

60. **Klasik** — Dalga dalga ilerleyen ana mod. ✅
61. **Sonsuz** — Ölümüne hayatta kalma. ✅
62. **Boss rush** — Sadece boss savaşlarından oluşan mod. ✅
63. **Zamana karşı** — Süre dolmadan en yüksek skor. ✅
64. **Günlük meydan okuma** — Herkese aynı koşullarda günlük run. ✅
65. **Kusursuz mod** — Can kaybedince run biter; kalkan emişi serbest. ✅
66. **Roguelite rastgele perk** — Her koşuda seçimle değişen güçlenmeler. ✅
67. **Haftalık özel mod / mutatör** — Örn. "sadece lazer", "ters kontroller", "hızlı düşmanlar". ✅ (v9.8: 10 mutatör, deterministik tohum)

## 8. Skor ve rekabet

68. **Skor + combo çarpanı** — Agresif oynamayı ödüllendiren puanlama. ✅
69. **Rank / harf notu** — Koşu sonunda S–D değerlendirmesi. ✅
70. **Yerel rekorlar ve istatistikler** — En iyi skor, dalga, süre, kill sayısı. ✅
71. **Son koşular grafiği** — Gelişimi gösteren mini çizelge. ✅
72. **Online liderlik tablosu** — Dünya/genel sıralama. ❌
73. **Hayalet / replay** — En iyi koşunun tekrar oynatılması. ❌
74. **Arkadaş skoru karşılaştırması** — Sosyal rekabet. ❌
75. **Turnuva / sezon sıralaması** — Dönemsel yarışma. ❌

## 9. Sunum ve atmosfer

76. **Dinamik müzik** — Bölgeye göre ton değiştiren prosedürel müzik. ✅
77. **Bölgeye özel görsel kimlik** — Renk paleti, yıldız rengi, sis. ✅ (v8.3: gezegen, nebula ve yıldız kümesi; v9.0: 480×720 bölge sahnesi, parallax, bölge silueti)
78. **Anonsçu / sesli geri bildirim** — "Wave 10", "Boss yaklaşıyor" gibi sesler. ❌
79. **Hikâye / kampanya** — Diyalog ve görev anlatımı. 🟡 (v9.0: 300 görevlik bonus kampanya; diyalog yok)
80. **Fotoğraf modu** — Duraklatıp ekran görüntüsü alma. ❌
81. **Sinematik giriş** — Bölüm başında kısa geçiş. 🟡 (v8.3: boss yenilgi sinematiği var; bölüm girişi yok)
82. **Titreşim (haptics)** — Çarpışma ve patlamada dokunsal geri bildirim. ✅

## 10. Erişilebilirlik ve platform

83. **Türkçe / İngilizce** — Dil değiştirme. ✅
84. **Renk körü modu** — Kurşun ve tehlike renklerini ayrıştırma. ✅
85. **Hareket azaltma** — Sarsıntı ve yoğun animasyonu kısma. ✅
86. **Partikül kalitesi** — Düşük/orta/yüksek seçenekleri. ✅
87. **Ekran sarsıntısını kapatma** — Ayrı erişilebilirlik anahtarı. ✅
88. **FPS sayacı** — Performans takibi. ✅
89. **Sol el modu** — Arayüzü ve kontrolleri aynalama. ✅ (v9.7: ARAYÜZ > Sol El Modu)
90. **Yardım / assist modu** — Hasarı yarıya indirme, ekstra can, yavaşlatma. ✅ (v9.8: oto bomba, nişan, yavaş mermi, yedek can)
91. **Çevrimdışı oynanış** — İnternetsiz tam deneyim. ✅
92. **Tam ekran** — Mobilde çentik/klavye uyumlu görünüm. ✅
93. **Bulut kayıt** — Cihazlar arası ilerleme aktarımı. 🟡 (dosya/panoya yedek var, bulut yok)
94. **Çok oyunculu / co-op** — Aynı ekranda ikinci pilot veya PvP. ❌

---

## Yıldız Akını v9.9 — tamamlananlar

| # | Özellik | Durum |
|---|---------|-------|
| 1 | 300+ entegre özellik; ayrı içerik sekmesi yok | ✅ |
| 2 | 300 görevlik bonus kampanya (5 halka × 60) | ✅ |
| 3 | 10 oyun modu: Klasik, Sonsuz, Hızlı Akın, Günlük, Zaman Yarışı, Kusursuz, Boss Akını, Tek Can, Kaos, Haftalık Akın | ✅ |
| 4 | 37 düşman (17 temel + 20 varyant), 11 boss (5 temel + 6 varyant) | ✅ |
| 5 | Daha kalabalık dalgalar: `12 + 4.6n`, en fazla 150 kayıt; dalga ortası 3–8 takviye; aktif tavan 72/84/48 | ✅ |
| 6 | Boss koruma sürüleri: 8–28 koruma, 0.14 sn spawn aralığı; boss ölse bile dalga bitmez | ✅ |
| 7 | 63 perk, 15 güçlendirme, 70 başarım, 15 füzyon, 9 bölge | ✅ |
| 8 | 6 gemi, 16 skin, 3 iz, 2 patlama, 7 rozet | ✅ |
| 9 | 20 seviyelik sezon ve doğrulanmış yedekleme | ✅ |
| 10 | Boss ölüm kilidi düzeltmesi: sinematik sırasında ek isabet ölümü ve hasar korumasını kilitlemez | ✅ |
| 11 | Görsel yenileme: 2× sahne çözünürlüğü, üç katmanlı parallax, 9 bölgede doygun nebula/gezegen, bölge siluetleri, 1.56 oyuncu, 1.26 düşman, 1.12 boss + aura/yıldırım, beyaz-sıcak raylı ışın, sıkı haleli mermiler, hasar çipli boss barı, altıgen dokunmatik tuşlar | ✅ |
| 12 | v9.2 gömülü sanat paketi: Kenney Space Shooter Redux gemi/düşman/boss parçaları, 9 NASA bölge fotoğrafı, ambientCG Metal032 dokusu; sanat yalnızca oyun içinde kullanılır | ✅ |
| 13 | v9.2 aksiyon geçişi: sıkı spawn aralıkları, dalga ortası takviye, güçlü boss korumaları, hit-stop/zoom/sarsıntı, katmanlı namlu alevi, duman, warp halkası ve akın hız çizgileri | ✅ |
| 14 | v9.2 hareketli arka plan: overscan kayma, alt karartma perdesi ve yavaş ışık süpürmesi | ✅ |
| 15 | v9.3 Overdrive: graze/kill/modülle dolan enerji metreği; 6.5 sn ateş hızı ve ek mermi | ✅ |
| 16 | v9.3 yörüngeli boss modülleri: iki taret, ×0.72 hasar azaltımı, ikisi yıkılınca ×1.12 zırh kırılması | ✅ |
| 17 | v9.4 15 gemi füzyonu (C(6,2)), füzyon sayfası ve kalıcı profil kaydı | ✅ |
| 18 | v9.4 kanat filosu: 1/3/5 füzyonda 1/2/3 eskort, 560 px içinde otomatik ateş | ✅ |
| 19 | v9.4 çevrimdışı 60 saniyelik 1v1 düello ve Düellocu başarımı | ✅ |
| 20 | v9.4 altın ışın güçlendirmesi ve dört kanatlı kombo bildirimleri | ✅ |
| 21 | v9.5 aksiyon ısısı: 0–100, beş kademe, %22 ateş hızı ve %20 hasar artışı | ✅ |
| 22 | v9.5 öldürme zinciri: 2.4 sn pencere, şarapnel (6/12/20) ve her 10 zincirde nova | ✅ |
| 23 | v9.5 bloom tamponu (120 × 180, en fazla 48 leke) ve ısı/zincir HUD'u | ✅ |
| 24 | v9.5 negatif delta ve koruma spawn NaN düzeltmeleri | ✅ |
| 25 | v9.6 gemi pasifleri: Denge +%15 Overdrive, Şimşek hızlı atılma/ateş, Kale +3 kalkan, Nova +%20 ısı, Hayalet +8 sıyırma, Titan +%12 boss hasarı | ✅ |
| 26 | v9.6 zincir ödülleri: 15/30/50 zincirde güçlendirme ve bildirim | ✅ |
| 27 | v9.6 boss modülü ısısı ve zırh kırılması Overdrive ödülü | ✅ |
| 28 | v9.7 komuta güvertesi ana menü: sezon şeridi, gemi vitrini, çipler, 3×3 kutucuk, günlük operasyon | ✅ |
| 29 | v9.7 Hangar 2.0: karusel, istatistik çubukları, pasif kartı, sayfalı 16 skin galerisi | ✅ |
| 30 | v9.7 Yükseltme 2.0: nadirlik kartları, NEW rozeti, 30 coin yenileme, +20 coin atlama | ✅ |
| 31 | v9.7 duraklatma/sonuç: koşu özeti, donanım çipleri, günlük hedef, S–D derece halkası, ödül dökümü | ✅ |
| 32 | v9.7 erişilebilirlik: sol el modu, sade HUD, nişan çizgisi, arayüz animasyonu | ✅ |
| 33 | v9.8 odak modu ve şarjlı delici mızrak: ×0.52 hız, ×0.45 yayılım, ×1.12 hasar, 2.2 sn şarj, 4.2× mızrak, 8 delme | ✅ |
| 34 | v9.8 Haftalık Akın: deterministik hafta tohumu, 10 mutatör, ayrı haftalık rekor ve tablo | ✅ |
| 35 | v9.8 asistan paketi: oto bomba, nişan yardımı, yavaş mermi, yedek can; her asistan −%5 skor, taban %80 | ✅ |
| 36 | v9.8 iki yeni başarım (Mızrak Ustası, Haftalık Akıncı) ve 327 kayıtlık özellik defteri | ✅ |
| 37 | v9.9 Fırtına evrimi: isabet zincir yıldırımı (2/3/4 hedef, artan hasar/menzil), 3. kademede her 10 öldürmede yıldırım novası | ✅ |
| 38 | v9.9 Ray evrimi: her 5/4/3 salvoda 2.2×/3.0×/3.6× hasarlı, 7/10/13 delici ray; 3. kademede çift ray | ✅ |
| 39 | v9.9 Nova evrimi: patlayıcı mermi çarpması (44/58/72 yarıçap), 3. kademede yanma hasarı | ✅ |
| 40 | v9.9 dalga 6 zorunlu üç evrim kartı; atlanan yol sonraki yükseltmelerde döner; 2. kademe dalga 12, 3. kademe dalga 18 | ✅ |
| 41 | v9.9 evrim rozeti (HUD) ve duraklatma yapı çipi; `evo1`/`evo3` başarımlarıyla 70 başarım ve 339 kayıtlık defter | ✅ |
| 42 | v9.9 can damlası: düşmanlardan seyrek, tank/healer/elitlerden daha sık; her boss'tan garantili +1 can (üst sınır 6) | ✅ |
| 43 | v10.0 gemi imza pasifleri: Denge overdrive zinciri, Şimşek dash şok dalgası, Kale 10 sn reaktif kalkan, Nova her 8. atışta mini nova, Hayalet faz yankısı, Titan +2 füze ve +%25 füze hasarı | ✅ |
| 44 | v10.0 gemi hasar profilleri (1.00/0.92/1.12/1.00/0.95/1.25) ve beşinci yükseltme düğümü abil (10 seviye; taban 400/900/1800, sonrası 1.8× artan maliyet) | ✅ |
| 45 | v10.0 yetenek yükseltmeleri: Overload +0,5 sn, Blink +30 px/+1 hasar, Barrier +0,6 sn/+1 kalkan, Supernova +0,15 sn/+1 hasar, Phase +0,5 sn/yankı, Salvo +1 füze; 3 yeni başarım (73 toplam) | ✅ |
| 46 | v10.0 hangar 2.0: imza pasifi ve yetenek kartları, yetenek seviye göstergesi, 2 sütunlu yükseltme ızgarası, gemiye özel aura | ✅ |
| 47 | v10.0 tam yığınlama: 63 koşu yükseltmesinin tamamı 99 seviyeye kadar birikir; can, hasar, diriliş, yan/arka atış, kalkan, süre ve çarpan etkileri üst üste biner | ✅ |
| 48 | v10.0 vuruş paketi: 20 yeni yığınlanabilir isabet özelliği — bölünen mermi, şok başlığı, zırh kırıcı, kafa vuruşu, zehir, yıldırım sıçraması, ağır mermi, ikiz namlu, çapraz ateş, sekmeli mermi, kinetik yük, kritik gücü, delme ustası, ölüm dalgası, aşırı yük, vuruş emme, güdümlü uç, zırh delen, buz ısırığı, zincir gücü | ✅ |
| 49 | v10.0 isabet geri bildirimi: kafa vuruşu/altın yıldız patlaması, ağır mermi şok halkası ve sarsıntısı, zehir yeşili kıvılcım, kıymık izleri, zırh kırığı ve zehir yığın sayaçları; toplam koşu yükseltmesi 83 | ✅ |
| 50 | v10.0 genişleme: 11 yeni güçlendirme — overdrive, yoğun atış, delici uç, hücum, hayalet faz, şok dalgası, para yağmuru, çift puan, onarım, cephane ve nova; HUD'da süre rozetleri | ✅ |
| 51 | v10.0 genişleme: 10 yeni elit varyant — zehirli bombacı, altın dokuyucu, kalkanlı izci, şarjlı hücumcu, bölünen izci, bombardıman tankı, oynak nişancı, buz hayaleti, çağırıcı kalkan, keskin tank (toplam 30 varyant) | ✅ |
| 52 | v10.0 genişleme: 10 yeni başarım — güç toplama (50/200/400), elit avı (10/50/100), overdrive, hücum, hayalet ve şok dalgası (toplam 83 başarım); elit sayacı kalıcı kayda eklendi | ✅ |
| 53 | v10.0 mağaza paketi: 15 yeni kalıcı ürün — güçlendirilmiş gövde, çevik itki, onaran kalkan, keskin nişangâh, şans yıldızı, hazine pusulası, cephane sandığı, delici çekirdek, güdüm çipi, yarış bilgisayarı, yedek kapsül, kalkan hücresi, bomba siperi, sıyırma ustası, mıknatıs nabzı (toplam 22 ürün); 2 sütunlu sayfalı vitrin | ✅ |

## Sonraki sürüm için adaylar

| # | Özellik | Neden | Emek |
|---|---------|-------|------|
| 1 | Boss zayıf noktası | Boss savaşlarını can süngeri olmaktan çıkarır | L |
| 2 | Yerel hayalet / replay | Kendi rekorunu izleme; sunucu gerektirmez | M |
| 3 | Modül slotları | Gemi ağacının üstüne yeni bir derinlik katmanı | L |
| 4 | Ara boss'lar | Bölüm ritmini güçlendirir | L |
| 5 | Düelloda zorluk ve rakip kişilikleri | Mevcut 1v1 modunu derinleştirir | M |

**Öneri:** v10.0 ile altı gemiye imza pasifi, yetenek yükseltmesi ve yeni hangar/ızgara arayüzü geldi. Sonraki sürüm için boss zayıf noktası, ara boss'lar ve düello zorluk seçimi öne çıkıyor; içerik sekmesi yerine oynanış derinliği korunmalı.

## Kaynaklar

- Wikipedia — [Shoot 'em up](https://en.wikipedia.org/wiki/Shoot_%27em_up)
- Wikipedia — [Bullet hell](https://en.wikipedia.org/wiki/Bullet_hell)
- Shmups Wiki — [Boghog's bullet hell shmup 101](https://shmups.wiki/library/Boghog%27s_bullet_hell_shmup_101)
- Game Developer — [Designing smart, meaningful SHMUPs](https://www.gamedeveloper.com/design/designing-smart-meaningful-shmups)
- TV Tropes — [Shoot 'em Up](https://tvtropes.org/pmwiki/pmwiki.php/Main/ShootEmUp)
- Google Play / APKPure uzay shooter açıklamaları (gemi koleksiyonu, power-up, sonsuz mod, günlük ödül örnekleri)
