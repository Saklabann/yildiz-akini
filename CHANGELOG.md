# Sürüm Notları

Tüm önemli değişiklikler bu dosyada tutulur. Biçim, [Keep a Changelog](https://keepachangelog.com/tr/1.1.0/) temel alınarak hazırlanmıştır; sürüm numaraları [Semantic Versioning](https://semver.org/lang/tr/) izler.

## [9.8.0] - 2026-10-30

### Eklendi

- **Odak modu ve şarjlı mızrak.** Boşluk, gamepad LT/RT veya dokunmatik ODAK tuşu basılı tutulunca gemi %48 yavaşlar, yayılım %55 daralır, hasar %12 ve mermi hızı %18 artar. 2.2 saniyede dolan şarj, 4.2× hasarlı, 8 düşman delen bir mızrak olarak otomatik ateşlenir. Gemi çevresinde şarj halkası, hazır olduğunda "MIZRAK HAZIR" bildirimi ve özel ses efekti vardır.
- **Haftalık Akın.** Onuncu oyun modu; her pazartesi yenilenen `mulberry32(weekIdx()*7919+17)` tohumu ve 10 mutatörden biriyle oynanır: Sürü, Zırh, Hızlı Ateş, Keskin Nişancı, Altın Akın, Elit Dalga, Meteor Yağmuru, Öfke, Cam Gövde ve Titan. Ayrı haftalık rekor, haftalık tablo ve ana menüde HAFTA çipi bulunur.
- **Asistan paketi.** OYNANIŞ sekmesinde dört isteğe bağlı yardım: Oto Bomba (ölümcül hasarda bombayı otomatik harcar), Nişan Yardımı (mermiler en yakın hedefe hafifçe yönelir), Yavaş Mermi (düşman mermileri %15 yavaşlar) ve Yedek Can (+1). Her açık asistan skoru %5 azaltır; taban %80'dir.
- **İki yeni başarım.** `Mızrak Ustası` (ilk şarjlı mızrağı ateşle) ve `Haftalık Akıncı` (haftalık akında 5. dalgaya ulaş); toplam 68.

### Değişti

- Ana menü çip satırı dört eşit çipe bölündü: gemi, mod, zorluk ve haftalık. Haftalık çip doğrudan Haftalık Akın sayfasını açar.
- Ayarlar beş sekmeye çıktı (GENEL · ARAYÜZ · OYNANIŞ · PERFORMANS · VERİ); asistanlar OYNANIŞ sekmesinde toplandı.
- Dokunmatik HUD'a beşinci tuş olarak ODAK eklendi; gamepad LT/RT odak tuşu olarak eşlendi.
- `defS` içine `asBomb`, `asAim`, `asSlow`, `asLife`; profil şemasına `weeklyBest` ve `weeklyWeek` eklendi. `sanitizeSettings` ve kayıt yükleme yolu bu anahtarları doğrular.
- `GMODES` 10, `CORE_MODES` 9 kayda ayrıldı; `modes9` başarımı yalnızca ilk dokuz modu ister.
- Sürüm `v9.8` (versionCode 19). README, teknik doküman, yol haritası, kurulum dosyası ve özellik defteri 327 kayda güncellendi.

### Düzeltildi

- Bitmemiş bir düello sonrası `vsPrevMode` değerinin bir sonraki koşunun modunu ezmesi engellendi; `startGame()` bu alanı temizler.
- Dört çipli ana menüde Haftalık çipinin ekran dışına taşması giderildi; çipler eşit genişliğe alındı.
- Asistan ayarlarındaki "Tüm asistanlar kapalı" satırı eylem düğmesi olarak "Tümünü Kapat" yapıldı; durum metni ayrı anahtara taşındı.
- Playwright paketi 80/80 geçti. 240 saniyelik otopilot 22 dalga, 1.316 kill, 3/6/9/12/15/18/21 yükseltmeleri, 0–3 boss, 4/9/14/19 akınları, 0 NaN ve 0 hata ile tamamlandı. Haftalık + dört asistan koşusu 10 dalga, 440 kill, mızrak ve haftalık rekor doğrulamasıyla geçti.

## [9.7.0] - 2026-10-29

### Eklendi

- **Komuta güvertesi ana menü.** Sezon şeridi, gemi vitrini, gemi/mod/zorluk çipleri, büyük BAŞLA düğmesi, 3×3 kutucuk ızgarası ve günlük operasyon kartı tek ekranda birleşti. Yardım düğmesi sağ üstte; altbilgi sürüm ve dalga kurallarını gösterir.
- **Hangar 2.0.** Gemi karuseli, canlı hız/ateş/can/bomba çubukları, pasif yetenek kartı, sayfalı 16 skin galerisi (kilit koşullarıyla) ve geliştirme ağacı/koleksiyon/füzyon kısayolları.
- **Yükseltme 2.0.** Kartlar nadirlik rengi, kademe pipleri, NEW rozeti ve füzyon vurgusu taşır. 30 coin'e yenileme (dalga başına bir kez) ve +20 coin karşılığında atlama eklendi; eğitimde bu düğmeler gizlenir.
- **Duraklatma 2.0.** Dalga/kill/en iyi zincir özeti, pasif yetenek, koşu donanımı çipleri, günlük hedef ilerlemesi ve sürüm bilgisi.
- **Sonuç 2.0.** S/A/B/C/D derece halkası, para/toz/sezon XP ödül dökümü, mod ve ısı/zincir rozetleri; rekor şeridi korunur.
- **ARAYÜZ ayarları.** Sol el modu (dokunmatik tuşlar, bomba/can göstergeleri ve joystick yarısı aynalanır), sade HUD, dikey nişan çizgisi ve sayfa geçiş animasyonu.
- **Altı yeni skin.** `void` (50 kombo), `reactor` (30. dalga), `prism` (10 füzyon), `wraith` (80 kombo), `chrono` (10 saat) ve `zenith` (sezon 18). Toplam 16 skin.
- **Arayüz geçişi.** Menü sayfaları arasında yumuşak karartma; `S.uiAnim` kapatıldığında devre dışı kalır.

### Değişti

- Sürüm `v9.7` (versionCode 18). HTML ~1.4 MB.
- `defS` içine `lefty`, `hudMin`, `aimLine`, `uiAnim` eklendi; `sanitizeSettings` ve yükleme yolu bu anahtarları doğrular.
- Ana menü, hangar, yükseltme, duraklatma ve sonuç ekranları yeniden çizildi; kutucuk/karusel düzeni kullanılır.
- README, teknik doküman, yol haritası, kurulum dosyası ve özellik defteri v9.7 için yenilendi; ekran görüntüleri ve kapak yeni arayüzden üretildi.

### Düzeltildi

- NEW rozetinden sonra metin hizasının kayması giderildi; derece etiketi halkanın üstüne taşındı.
- Playwright paketi 62/62 geçti; 240 saniyelik otopilot koşusu 21 dalga, 1.166 kill, 0 NaN ve 0 konsol hatasıyla tamamlandı.

## [9.6.0] - 2026-10-29

### Eklendi

- **Gemi pasifleri.** Denge Overdrive kazancı +%15; Şimşek atılma beklemesi ×0.85 ve ateş beklemesi ×0.92; Kale +3 başlangıç kalkanı ve +0.6 sn dokunulmazlık; Nova ısı kazancı +%20; Hayalet sıyırma yarıçapı +8 ve coin +%10; Titan boss hasarı +%12 ve +1 bomba. Pasifler füzyonlardan sonra uygulanır.
- **Zincir ödülleri.** 15, 30 ve 50 zincirde güçlendirme düşer; `ZİNCİR ÖDÜLÜ ×n` bildirimi ve sesi çalışır.
- **Modül ısısı.** Boss modülü yıkımı 12 ısı ve 0.05 Overdrive ekler; zırh kırılması ek 0.12 Overdrive verir.
- **Koşu istatistikleri.** Duraklatma ekranında dalga, kill, en iyi zincir ve pasif yetenek; sonuç ekranında ısı/zincir özeti gösterilir.

### Değişti

- Sürüm `v9.6` olarak hazırlandı; yayın v9.7'de tamamlandı.
- Overdrive dolumu gemi çarpanına (`st.odMul`), ısı kazancı `st.heatMul` değerine, dokunulmazlık `st.invBonus` değerine bağlandı.

## [9.5.0] - 2026-10-29

### Eklendi

- **Aksiyon ısısı.** 0–100 arası bir metre beş kademeye ayrıldı: SOĞUK, ISINIYOR, HIZLI, ÖFKELİ ve KAOS (eşikler 0/24/46/68/86). Isı yükseldikçe ateş beklemesi `1 − ısı × 0.0022`, hasar `1 + ısı × 0.002` çarpanıyla iyileşir; 100 ısıda ateş %22 hızlanır, hasar %20 artar. Kademe atlayışı ekran bandı, halka, sarsıntı ve sesle duyurulur. Zincir açıkken 1.7/sn, boşken 3.4/sn soğur; hasar almak 30 ısı düşürür.
- **Öldürme zinciri.** Her öldürme 2.4 saniyelik pencereyi yeniler ve `chainBest` rekorunu günceller. 6 zincirden sonra öldürmeler 2–4 delici şarapnel mermisi saçar (12'de 3, 20'de 4). Her 10 zincirde 92–172 px yarıçaplı nova patlar; `novaDepth` en fazla 2 iç içe tetiklemeye izin verir.
- **Bloom tamponu.** 120 × 180 çözünürlüklü ikinci tuval, `0.25` ölçek ve `lighter` karışımla en fazla 48 ışık lekesi toplar; `drawBloom()` bunu ekrana bindirir. `fxLevel() === 0` veya azaltılmış harekette tamamen atlanır.
- **Isı ve zincir HUD'u.** Aksiyon çubuğu kademe rengini, doluluk oranını ve `ZİNCİR ×n` rozetini gösterir; şarapnel/nova anlarında nabız animasyonu çalışır.
- **Yeni geri bildirim.** Şarapnel yıldız patlamaları, çift halkalı nova, `PARÇALANMA! ×n` bildirimi ve ısı kademesi sesleri.

### Değişti

- Sürüm `v9.5` (versionCode 17). HTML ~1.4 MB, APK ~0.8 MB.
- `state.heat`, `state.chain`, `state.chainT`, `state.chainBest`, `state.novaDepth` ve `state.novaPulse` çalışma durumuna eklendi; ısı/zincir koşu sonunda sıfırlanır.
- README, teknik doküman, yol haritası, kurulum dosyası ve sürüm notları v9.5 için yenilendi; ekran görüntüleri ve kapak yeni sürümden üretildi.

### Düzeltildi

- **Negatif delta.** Kare süresi `Math.max(0, Math.min(dt, 0.033))` ile sınırlandı; saat geri sıçramaları ve sekme dönüşleri artık sayaçları, ısıyı veya mermi fiziğini bozamaz.
- **Koruma spawn NaN'ı.** `x` değeri olmadan üretilen koruma düşmanları `mkEnemy` içinde `W / 2` konumuna düşürüldü; `x: NaN` kaynaklı kaybolma ve çarpışma hataları giderildi.
- 240 saniyelik otopilot koşusu: dalga 22, 1.257.777 puan, 1.172 kill, 0 NaN, 0 konsol hatası. Playwright paketi 62/62 geçti.

## [9.4.0] - 2026-10-28

### Eklendi

- **15 gemi füzyonu.** Altı geminin tüm ikili eşleşmeleri (C(6,2)) kalıcı füzyon kartlarına dönüştü. Kartlar 6. dalgadan sonra yükseltme ekranında çıkar, yalnızca uçulan gemiyle eşleşen ve açılmamış kayıtlardan seçilir; seçim `P.fusions` altına yazılır ve iki gemiden biriyle uçarken etkindir.
- **Füzyon sayfası.** Ana menüden açılan `FÜZYONLAR` ekranı 15 kartı üçerli sayfalar hâlinde gösterir; açık/kilitli durumu, çift eşleşmesi ve `x/15 füzyon` ilerlemesi görünür.
- **Kanat filosu.** Açılan füzyon sayısına bağlı 0–3 kalıcı eskort. 1 füzyonda bir, 3'te iki, 5'te üç kanat uçar; 560 px içindeki en yakın düşmana otomatik ateş eder ve Overdrive sırasında %35 daha güçlü vurur.
- **Çevrimdışı düello.** 60 saniyelik 1v1 modu: oyuncu ve rakip yapay zekâ aynı dalgada avlanır. Rakip kendi nişan sistemiyle ateş eder, hasar alınca sarsılır ve yeniden konumlanır. Galibiyet `30 + 2 × av` coin, 1 toz ve 5. galibiyette `Düellocu` başarımı verir.
- **Altın ışın.** 2.6 saniye süren delici kolon ışını güçlendirmesi; düşmanları ve boss modüllerini biçer, HUD'da kalan süre sayacı gösterilir.
- **Kanatlı kombo bildirimleri.** `İYİ!`, `HARİKA!`, `MÜKEMMEL!`, `İNANILMAZ!` ve `EFSANE!` yazıları dört tüylü altın enerji kanadı ve renkli radyal patlamayla açılır.
- **İki yeni başarım.** `Füzyon Ustası` (5 füzyon aç) ve `Düellocu` (5 düello kazan); toplam 66.
- **Yeni güçlendirme.** Altın ışın ile güçlendirme sayısı 15'e çıktı.

### Değişti

- Ana menüye `FÜZYONLAR` ve `DÜELLO` satırları eklendi; düello sonucu için ayrı `versusEnd` ekranı çizilir.
- `P.vsBest`, `P.vsPlayed`, `P.vsWins` ve `P.fusions` profil şemasına eklendi; eski kayıtlar eksik alanlarla sorunsuz tamamlanır.
- Sürüm `v9.4` (versionCode 16).

## [9.3.0] - 2026-10-27

### Eklendi

- **Overdrive (Aşırı Yük).** Graze, kill ve boss modülü yıktıkça dolan otomatik bir enerji metreği. Dolduğunda 6.5 saniye boyunca ateş hızı yaklaşık iki katına çıkar, öne üç ek mermi ve arkaya bir kuyruk atışı eklenir. HUD'da yüzde, aktif süre ve hazır durumu ayrı bir rozetle gösterilir; tetiklendiğinde `AŞIRI YÜK!` bandı, aura ve özel ses efekti çalışır.
- **Yörüngeli boss modülleri.** Her boss artık iki yörünge taretle gelir. Modüller oyuncuya nişan alan yay ateşi açar, gövdeden ayrı vurulabilir ve yok edildiklerinde coin, güçlendirme ve Overdrive şarjı bırakır. İki modül de yıkılınca bossun çekirdek zırhı kırılır.
- **Modül kalkanı ve zırh kırılması.** Modüller hayattayken boss'a gelen hasar `×0.72`; iki modül de yıkıldığında `×1.12` zırh kırılması bonusu uygulanır. Modül çubukları boss can barının altında ayrı ayrı izlenir.
- **Yüksek dalga düşman desenleri.** Shooter, tank, orbiter, sniper ve weaver düşmanlarına dalga numarasına bağlı yeni nişan, yay, yörünge ve sıyırma desenleri eklendi.
- **Yeni geri bildirim.** Overdrive aura halkası, modül patlama efekti, `MODÜL İMHA` ve `ÇEKİRDEK ZIRHI KIRILDI` bildirimleri, boss modül sesleri ve HUD rozetleri.

### Değişti

- **Galeri tamamen kaldırıldı.** `GALERİ` sayfası, menü kısayolu, klavye yolu, sanat yükleyicisi, metin anahtarları ve belgelerdeki altı el çizimi referansı oyundan ve depodan çıkarıldı. Gömülü Kenney/NASA/ambientCG sanat paketi korunuyor.
- Overdrive HUD'u geminin altında 150 px genişliğe daraltıldı; etiket koyu bir rozete alındı ve yüzde bilgisi etikete taşındı. Boss isabet parlaması `0.9` yerine `0.5` alfa ile çizilir; hızlı ateşte gövde beyaza boğulmaz.
- Sürüm `v9.3` (versionCode 15). HTML ~1.3 MB, APK ~1.2 MB.

### Düzeltildi

- Overdrive rozetinin gemi ve aura üzerinde okunamaması giderildi.
- Boss modülleri öldüğünde boss ölüm animasyonunun modülleri askıda bırakması engellendi.
- Modül mermilerinin boss gövdesine değil modüle çarpması sağlandı; delici mermiler modülden sonra yoluna devam eder.
- 240 saniyelik otomatik koşuda 11 dalga, 423 kill, 5 Overdrive tetiklemesi, 3 yükseltme ve sıfır konsol hatası doğrulandı.

## [9.2.0] - 2026-10-27

### Eklendi

- **Gömülü sanat paketi.** 6 oyuncu gemisi, 12 düşman sprite'ı, 8 boss montajı ve 9 bölge arka planı WebP olarak tek HTML'e gömüldü. Kaynaklar Kenney Space Shooter Redux (CC0), NASA bölge fotoğrafları (kamu malı) ve ambientCG Metal032 (CC0); ayrıntılar [CREDITS.md](CREDITS.md).
- **El çizimi galeri korundu.** Altı orijinal referans `GALERİ` sayfasında sergilenmeye devam ediyor.
- **Dalga ortası takviye.** Normal dalgalarda ana dizilimden sonra 3–8 düşmanlık kısa bir takviye dalgası gelir; tempo dalga sonuna kadar düşmez.
- **Daha güçlü boss korumaları.** Koruma sayısı 8–28 aralığına çıktı, spawn aralığı 0.14 sn'ye sıkılaştı; boss dalgası gerçek bir kuşatmaya dönüştü.
- **Savaş geri bildirimi.** Katmanlı namlu alevi, patlama dumanı, düşman girişinde warp halkası, akın dalgasında hız çizgileri, boss faz 2 geçişinde hit-stop/zoom/sarsıntı ve daha dolgun patlama sesi.
- **Hareketli arka plan.** NASA bölge fotoğrafları hafif overscan ve salınımla kayar; alt karartma perdesi ve yavaş ışık süpürmesi eklendi.

### Değişti

- Normal dalga tabanı `12 + 4.6n`, üst sınır 150 kayıt. Aktif düşman tavanı normalde 72, akında 84, pil tasarrufunda 48; aynı karede en fazla 5 spawn.
- Akın dalgası spawn aralıkları 0.05–0.45 sn'ye indirildi; 50 düşmanlık akın hâlâ tam 50 kayıt ve 4, 9, 14, 19... dalgalarında.
- Dalga arası bekleme 1.05 sn (akında 0.8, yükseltmede 0.85); koşu başlangıcı 0.8 sn.
- Boss her 5, yükseltme her 3, akın her 4. dalgada; ritim değişmedi.
- Sürüm `v9.2` (versionCode 14).

### Düzeltildi

- Sanat yüklenemediğinde oyun prosedürel çizime sorunsuz düşer; 9 bölge, 6 gemi, 16 düşman ve 10 boss varyantı yedek yolda doğrulandı.
- Kalabalık akın dalgasında spawn sayacı ve aktif tavan birlikte çalışır; 50 kayıt eksiksiz spawn edilir.

## [9.0.0] - 2026-10-24

### Görsel yenileme

- **2× çözünürlüklü sahne katmanları.** Galaksi, nebula ve 9 bölge sahnesi 480×720 arka plan tuvaline çizilip ekranda 1:1'e yakın kullanılır; menü arka planı 960×1440 üretilir.
- **Üç katmanlı derinlik.** Oyuncu hareketine tepki veren galaksi parallaksı, dolu kaya/bölge sahnesi ve bölgeye özel ön plan siluetleri (`biomeFG`) eklendi.
- **Doygun bölge gökyüzü.** 9 bölgenin tamamı kendi renk paletine, üç büyük nebula bulutuna ve en az bir gezegene sahip; Nebula, Crimson, Ice, Belt, Dark, Solar, Violet, Emerald ve Void sahneleri referanstaki canlı biome renklerine yaklaştırıldı.
- **Bölge simgeleri.** Her bölgeye kendi dev silueti: enkaz gövdesi, halka istasyonu, buz katedrali, kovan kulesi, boşluk yarığı, güneş paneli ve asteroid platformu.
- **Atmosfer ve ışık.** Hacimsel ışık huzmeleri, kaynak halesi, anamorfik lens çizgileri, lens hayaletleri, bölgesel ışık olayları, ön plan bokeh'i ve yıldız tozu yoğunlaştırıldı.
- **Daha okunaklı mağara/duvar dokusu.** Neon tel kafes görünümü yerine katmanlı kaya kütleleri, yüzey lekeleri, tortu çizgileri ve sınırlı kenar ışığı kullanıldı.
- **Oyuncu gemisi.** `1.56` görsel gövde ölçeği, çift motorlu plazma izi, büyütülmüş motor bloom'u, hıza bağlı egzoz konisi, yatay lens çizgisi ve kanat ucu seyrüsefer ışıkları.
- **Düşmanlar ve boss'lar.** Düşmanlarda `1.26` görsel ölçek, zemin gölgesi, daha güçlü hale, alt/üst kenar ışığı ve uzun motor alevleri; boss'larda `1.12` görsel ölçek, dönen aura halkaları, enerji düğümleri, gövdeye çakan yıldırımlar, zemin gölgesi ve faz 2 enerji yayları. Boss isabet kutusu, AI ve zamanlama değişmez.
- **Mermiler ve ışınlar.** Oyuncu mermileri katmanlı plazma dartı, düşman mermileri sıkılaştırılmış haleli enerji küresi; boss uyarı koridoru, altın raylar, kırmızı uyarı düğümleri, beyaz-sıcak çekirdekli kalın ışın ve çekirdekten taşan dallı yıldırımlar.
- **HUD ve dokunmatik.** Boss canında hasar çipi ve 20 bölmeli bar; dokunmatik tuglalarda altıgen plaka, kapasite halkası, eğim, köşe çentiği, etiket ve bomba pipleri.
- **Menü vitrini.** Daha büyük ana gemi, motor bloom'u, hologram izi, yörünge yayları, parıltılar ve güçlendirilmiş nebula/gezegen aydınlatması.

### Eklendi

- **300 entegre özellik.** Ayrı bir "300 içerik" sekmesi yok; içerik doğrudan oynanışa, hangara, mağazaya, başarımlara ve bonus kampanyaya dağıtıldı.
  - 63 koşu yükseltmesi, 37 düşman (17 temel + 20 varyant), 11 boss (5 temel + 6 varyant), 9 mod, 9 galaksi bölgesi, 64 başarım, 14 güçlendirme, 6 gemi, 10 skin, 3 çip, 7 mağaza ürünü, 3 iz, 2 patlama, 7 rozet, 16 kampanya modifikasyonu, 19 sezon ödülü, 3 zorluk, 9 görev türü ve 8 kampanya hedefi.
- **Çok daha kalabalık dalgalar.** Normal dalga tabanı `10 + 4n` oldu ve 140 kayıtla sınırlandı. Aynı karede en fazla 4 spawn yapılır; aktif düşman tavanı normalde 64, pil tasarrufunda 44'tür. Böylece ekran kalabalıklaşırken mobil FPS korunur.
- **Boss koruma sürüleri.** Boss dalgaları artık 10–22 koruma düşmanıyla gelir. Boss öldükten sonra korumalar temizlenene kadar dalga tamamlanmaz.
- **Daha yoğun asteroid dalgaları.** 18 asteroid ve 6 scout; önceki 12 asteroid + 3 scout'a göre belirgin biçimde daha baskılı.
- **Yeni modlar.** Boss Akını, Tek Can ve Kaos eklendi; mod sayısı 9'a çıktı.
- **Yeni düşman varyantları.** Buz, zehir, altın, kalkan, bölünme, nişancı, bombacı, iyileştirici, faz, hücum ve çağrıcı davranışları.
- **Yeni boss'lar.** Frost Queen, Gold Fortress, Void Spreader, Storm Laser, Venom Missile ve Crimson Guard.
- **33 yeni koşu yükseltmesi.** Sekme, güdümlü mermi, dondurma, yanma, vampir, son direniş, öfke, aşırı öldürme, yörünge, süpernova ve daha fazlası.
- **4 yeni güçlendirme.** Nuke, zaman yavaşlatma, kritik ve altın; toplam 14.
- **300 görevlik bonus kampanya.** 5 halka × 60 görev; her görevin adı, hedefi, modifikasyonları ve yıldız derecesi var. Tüm görevler açık, ödül yalnızca ilk temizlemede.
- **9 galaksi bölgesi.** Nebula, Crimson, Ice, Belt, Dark, Solar, Violet, Emerald ve Void.
- **64 başarım.** Dalga, boss, kombo, kampanya, sezon ve koleksiyon hedefleri.
- **Boss isabet düzeltmesi.** Merkezden atış yapan silahlar boss'a öngörülü nişan alır; boss canı `48 + 11 × dalga`, hızı 62 (faz 2'de 96).

### Değişti

- Ana menüdeki `300 İÇERİK` satırı ve katalog ekranı kaldırıldı. 300 özelliğin tamamı oyun sistemlerinde korunuyor.
- Ana menüde bonus kampanya satırı tam genişliğe alındı.
- Kampanya dili "sefer" yerine "görev" olarak güncellendi: `BONUS KAMPANYA`, `GÖREVE BAŞLA`, `GÖREV HARİTASI`.
- Klasik ritim korunur: boss her 5, yükseltme her 3, 50 düşmanlık akın 4, 9, 14, 19... dalgalarında.
- v8.2 eğitim/sezon/yedekleme, v8.3 görsel katman ve v8.4 50 düşmanlık akın korunur.
- Sürüm `v9.0` (versionCode 13).

### Düzeltildi

- **Boss ölüm kilidi giderildi.** Yenilgi sinematiği sırasında gelen ek isabetler boss'u anında kaldırıp ölüm ekranını ve hasar korumasını kilitleyebiliyordu; artık ölüm animasyonu her koşulda tamamlanıyor.
- Boss'a merkezden atış yapan silahların hasarının uygulanmaması giderildi; `bossDmg` çarpanı artık top mermilerinde de çalışıyor.
- Çok kalabalık dalgalarda aynı karede sınırsız spawn yığılması engellendi; 4 spawn/kare ve aktif düşman tavanı eklendi.
- Kampanya metinlerindeki eski "300 sefer" ifadeleri temizlendi.
- Boss korumaları ve horde dalgası için dalga ilerleme sayacı doğru hesaplanıyor.
- TR/EN geçişinde kampanya, mod ve başarım anahtarları eksiksiz.

## [8.4.0] - 2026-10-20

### Eklendi

- **50 düşmanlık akın dalgası.** 4, 9, 14, 19... dalgalarında tam 50 düşmanlık el yapımı bir set-piece: 15 scout V formasyonu, 8 dalışçı, 4 hücumcu, 6 nişancı, 3 tank, 4 bölünen, 4 kalkanlı, 3 dokuyucu ve 3 fantom. Akın dalgası boss ve yükseltme ritmini bozmaz.
- **Akın sunumu.** Dalga girişinde turuncu `50 DÜŞMANLIK AKIN!` bandı, `DALGA N • HAZIR OL` alt etiketi, HUD'da `50 DÜŞMAN AKINI` rozeti; siren, kısa zoom ve ekran sarsıntısı.
- **Daha yoğun normal dalgalar.** Taban düşman sayısı `6.5 + 2.8n` formülüne çıkarıldı; spawn aralığı sıkılaştırıldı.

### Değişti

- Klasik ritim korunur: boss her 5, yükseltme her 3, 50'lik akın 4, 9, 14, 19... dalgalarında.
- Akın dalgası zorluktan bağımsız olarak tam 50 düşman içerir; easy/normal/hard arasındaki fark can, hız ve hasar çarpanlarından gelir.
- Sürüm `v8.4` (versionCode 12).

### Düzeltildi

- Akın dalgasının spawn kuyruğu `t` değerine göre sıralanır; dalışçı ve hücumcuların aynı anda yığılması engellenir.
- Akın sırasında dalga ilerleme çubuğu 50 düşmanlık hedefi kullanır.

## [8.3.0] - 2026-10-20

### Eklendi

- **Silah ve vuruş efektleri.** Top, drone ve arka silah için ayrı iz, çekirdek parlaması ve isabet animasyonu; kritik vuruşta yıldız parlaması; düşman türüne göre patlama, enkaz ve halka efektleri.
- **Katmanlı galaksi arka planları.** 5 bölge için önbelleklenen prosedürel galaksi, uzak gezegen, nebula ve yıldız kümesi katmanları; hafif parallax ve dalga temelli atmosfer.
- **Boss sunumu.** Uyarı çizgileri ve nişangâhlar, `FAZ I/II` göstergesi, faz 2 ışık halkaları, cana bağlı zırh çatlakları, `ZIRH KIRILDI!` geri bildirimi ve 2.35 saniyelik atlanabilir yenilgi sinematiği.
- **Gemi geri bildirimi.** Hıza ve dash'e bağlı motor alevleri, kalkan isabet dalgası, hasar kıvılcımları/enerji sızıntısı ve daha okunaklı gövde siluetleri.
- **HUD ve menü cilası.** Sağlık/kalkan/dalga göstergeleri, animasyonlu kombo puan bildirimi, boss faz geçişi vurgusu, fareyle gezinen menü imleci ve büyütülmüş dokunmatik hedefler.

### Değişti

- Boss uyarı nişangâhı oyuncunun üzerinde kalacak şekilde hizalandı; `ÖFKE` etiketi çubuğun altına taşındı.
- Kalkan yüzdesi çubuktan ayrıldı; dar ekranlarda okunabilirlik arttırıldı.
- Galaksi katmanları yalnızca ilk kullanımda üretilip önbelleğe alınır.
- Sürüm `v8.3` (versionCode 11).

### Düzeltildi

- Boss yenilgi sinematiği sırasında oyuncunun hasar alması engellendi.
- Dokunmatik hassasiyet alt sınırı belgelerde %70 yazıyordu; gerçek %60 değeriyle eşitlendi.
- Boss yenilgi panelinin okunabilirliği için koyu zemin, kenarlık ve parlama eklendi.

## [8.2.0] - 2026-10-20

### Eklendi

- **Etkileşimli eğitim.** Hareket, otomatik ateş, bomba ve yükseltme seçimini öğreten 4 kısa görev. Eğitim sırasında hasar kapalıdır, öldürmeler ödül üretmez; `ATLA` ile geçilebilir ve menüdeki `?` düğmesinden yeniden açılabilir.
- **Sezonluk ilerleme.** "Neon Şafak" 20 seviye; puan, boss ve günlük/haftalık görevlerden XP. Seviye ödülleri coin, yıldız tozu, 7 rozet ve `Aurora` / `Tutulma` görünümleri.
- **Rozet seçimi.** Kadet, Pilot, As, Nova, Efsane, Mit ve Sonsuz rozetleri sezon ekranından seçilir; seçili rozet ana menüde görünür.
- **Kayıt ve yedekleme.** Profil `YA2.<base64>.<fnv>` kodu olarak panoya kopyalanır ve `.txt` indirilir. JSON yapıştırma ve dosyadan içe aktarma desteklenir; sürüm, uygulama kimliği, sağlama toplamı ve tüm alanlar doğrulanır.
- **Performans sekmesi.** Efekt kalitesi (düşük/orta/yüksek), FPS sınırı (otomatik/30/45/60), pil tasarrufu (30 FPS + azaltılmış parçacık/parlama) ve dokunmatik hassasiyet (%60-160).
- **Veri sekmesi.** Yedekle, panodan geri yükle, dosyadan geri yükle ve profili sıfırla; son yedek tarihi gösterilir.

### Değişti

- Ayarlar `GENEL`, `PERFORMANS` ve `VERİ` olmak üzere üç sekmeye ayrıldı.
- Hangar 10 skini üç satırda gösterir; alt düğmeler taşmayacak şekilde yeniden yerleştirildi.
- Sezon ekranı 5 seviyelik sayfalar, XP çubuğu ve rozet seçimiyle eklendi.
- Kayıt şeması `seasonLv`, `seasonXp`, `seasonClaimed`, `badges`, `badge`, `tutDone`, `lastBackup` alanlarıyla genişletildi.
- Sürüm `v8.2` (versionCode 10).

### Düzeltildi

- İçe aktarılan yedekteki `lastBackup` değerinin 1970'e kırpılması giderildi.
- Eğitimden ana menüye dönüldüğünde eğitim katmanının ekranda kalması engellendi.
- Kilitli sezon görünümleri güvenli varsayılana döner.
- Bozuk/yanlış uygulamaya ait yedekler profil ve ayarları değiştirmeden reddedilir.

## [8.1.0] — 2026-10-20

### Eklendi

- **Phonk esintili yeni müzik motoru.** Prosedürel parçalar artık 808 bas, cowbell melodi, trap davulları, plak cızırtısı ve hafif tape saturasyonu içeriyor.
- 125 BPM, 16'lık grid üzerinde iki barlık döngü; dört akorlu minör ilerleme (Am–F–C–G).
- Bölgeye göre ton değiştiren akor ve melodi yapısı korundu.
- Boss savaşlarında ek kick, hızlı hi-hat ve oktav cowbell katmanı.
- Menüde daha sakin, oyun içinde daha sert miks.
- Master zincirine kompresör, yumuşak saturasyon ve 2.6 kHz vurgu eklendi.

### Değişti

- Müzik zamanlaması 0.27 sn'lik seyrek adımlardan 0.12 sn'lik 16'lık grid'e taşındı.
- Ses seviyeleri telefon hoparlörlerinde duyulacak şekilde yeniden dengelendi.
- Sürüm `v8.1` (versionCode 9).

## [8.0.0] — 2026-10-20

### Eklendi

- **Gemi bazlı yükseltme ağacı.** Her gemi için Motor (3), Gövde (2), Silah (3) ve Çekirdek (3) dallarından oluşan 11 düğümlük kalıcı ağaç.
- **Günlük ve haftalık görevler.** Günde 3, haftada 3 görev; ilerleme otomatik sayılır, ödüller elle alınır. Haftalık set pazartesi yenilenir.
- **Günlük görev mimarisi.** Günün tohumu herkeste aynı görev setini üretir; günde bir kez ödül verilir.
- **Koleksiyon sayfası.** Skinler, izler ve patlama efektleri tek ekranda; kilit koşulları görünür.
- **Kozmetik kilitleri.** 8 skin, 3 iz ve 2 patlama efekti ilerlemeyle açılır.
- **5 galaksi bölgesi.** Nebula, Crimson, Ice, Belt ve Dark; her 5 dalgada tema değişir. Müzik kökü bölgeye göre transpoze edilir.
- **İstatistik paneli.** 12 kart, son 10 koşunun grafiği ve gemi bazlı rekorlar.
- **6 modlu seçim ekranı.** Klasik, Sonsuz, Boss Akını, Günlük Görev, Zaman Yarışı ve Kusursuz tek yerde.
- **Kusursuz mod.** Can kaybı koşuyu bitirir; kalkan emişi serbesttir.
- **Koşu sonu karşılaştırması.** Yeni skor, önceki en iyi skorla birlikte gösterilir.
- **3 yeni başarım.** `tree1`, `week1`, `perfect10`; toplam 31.
- **Hangar iyileştirmeleri.** Dönen tanıtım gemileri, kilitli skinlerde koşul etiketi, etkin hız ve can göstergeleri.

### Değişti

- Sürüm `v8.0` olarak güncellendi.
- Günlük görev havuzuna kusursuz dalga hedefi eklendi.
- Başarım adları ve açıklamaları yeni içerikle uyumlu hale getirildi.
- Kayıt şeması v8 alanlarıyla geriye uyumlu biçimde genişletildi.

### Düzeltildi

- Kilitli skin seçildiğinde güvenli varsayılana dönüş.
- Dokunmatik HUD yerleşimi ve küçük ekran taşmaları.
- Bölge geçişlerinde arka plan ve parçacık sürekliliği.

## [7.0.0] — 2026-10-19

### Eklendi

- 6 gemi ve her gemiye özel aktif yetenek: Overload, Blink, Barrier, Supernova, Phase, Salvo.
- 30 farklı koşu içi yükseltme (perk).
- Yeni düşman davranışları, elit varyantlar ve Fortress boss.
- Zaman Yarışı modu ve süre bonusu.
- Günlük görevler, başarım sistemi ve istatistik altyapısı.
- Dokunmatik kontrol katmanı; sol yarıda sürükleme, sağ altta eylem butonları.

### Düzeltildi

- Mobil HUD'un güvenli alan ve çentikli ekranlarla hizası.
- Arka plana alınan sekmede otomatik duraklama.

## [2.0.0] — 2026-10-17

### Eklendi

- 3 gemi, 3 zorluk, combo ve graze sistemi.
- Dash, bomba, yenilenen kalkan ve ikinci şans.
- Güdümlü füze, lazer, refakat dronu ve mıknatıs.
- Elit düşmanlar, asteroid dalgaları, UFO bonusu ve 2 fazlı boss'lar.
- Coin ekonomisi, mağaza, 16 yükseltme, 12 başarım ve yerel rekor tablosu.
- TR/EN dil desteği, renk körü paleti ve azaltılmış hareket.
- Dokunmatik ve gamepad desteği.

## [1.0.0] — 2026-10-16

### Eklendi

- İlk oynanabilir sürüm: dikey uzay savaşı, dalga sistemi, temel düşmanlar ve boss.
- Klavye/fare kontrolü, skor ve yerel kayıt.
