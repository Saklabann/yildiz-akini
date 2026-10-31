# Teknik Dokümantasyon

## Genel bakış

Yıldız Akını, tek bir HTML dosyası içinde çalışan dikey bir uzay savaşı oyunudur. Harici kütüphane, derleme adımı veya çalışma anında indirilen görsel/ses dosyası yoktur. Gemi, düşman, boss ve bölge sanatı HTML'e gömülü WebP verisidir; tüm sesler Web Audio API ile çalışma anında üretilir.

| | |
|---|---|
| Dosya | `yildiz-akini.html` |
| Boyut | ~1.4 MB (gömülü WebP sanat dahil) |
| Dil | JavaScript (ES2017+), HTML, CSS |
| Çözünürlük | 480 × 720 mantıksal; DPR'ye duyarlı |
| Kayıt | `localStorage` |
| Ağ | Yok |
| Bağımlılık | Yok |

## Çalışma akışı

Kod tek bir IIFE içinde kapsüllenmiştir. Kabaca sıra şöyledir:

1. **Sabitler ve yardımcılar** — `W`, `H`, `TAU`, matematik ve biçimlendirme fonksiyonları.
2. **Yerel depolama sarmalayıcı** — `LS.get` / `LS.set`; bozuk JSON'a karşı korumalı.
3. **Veri tabloları** — gemiler, yetenekler, skinler, ağaç, perkler, mağaza, modlar, bölgeler, başarımlar, görev havuzları, düşman/boss varyantları, füzyonlar, metinler.
4. **Kalıcı durum** — `P` profili (coin, rekorlar, açılanlar, istatistikler) ve `S` ayarları.
5. **Çalışma durumu** — `state` (dalga, düşmanlar, mermiler, süre, mod, ısı, zincir).
6. **Girdi katmanı** — klavye, fare, dokunma, gamepad; tek bir hareket vektörüne indirgenir.
7. **Ses motoru** — prosedürel osilatörler, gürültü ve filtrelere dayalı müzik/efekt.
8. **Oyun döngüsü** — `requestAnimationFrame`; sabitlenmiş delta ile güncelleme ve çizim.
9. **Arayüz** — menü, hangar, ağaç, koleksiyon, görevler, istatistik, füzyon, düello, bonus kampanya ve oyun sonu ekranları.
10. **Kayıt** — profil ve ayarlar değiştiğinde `localStorage`'a yazılır.

## Koordinat sistemi

Oyun 480 × 720 mantıksal alanda tasarlanır. Canvas, cihaz piksel oranına göre ölçeklenir; fiziksel çıktı tipik olarak 600 × 900'dür. Tüm çarpışma ve yerleşim hesapları mantıksal koordinatlarda yapılır. Bu sayede aynı kod farklı ekranlarda tutarlı davranır.

- Gemi çarpışma yarıçapı: 11–15 px (gemiye göre)
- Mermi hızları: ~590–700 px/s
- Gemi hızları: ~245–400 px/s
- Kare deltası `Math.max(0, Math.min(dt, 0.033))` ile sınırlanır; negatif veya aşırı delta fizik ve sayaçları bozamaz.

## Önemli veri tabloları

| Tablo | İçerik |
|---|---|
| `SHIPS` | 6 gemi; hız, ateş bekleme, can, hitbox, bomba, dash ve yetenek |
| `ABIL` | 6 aktif yetenek; bekleme, süre ve renk |
| `SKINS` | 10 görsel palet (2 sezon ödülü) |
| `TREE` | Gemi başına 4 dal, 11 düğüm ve artan coin maliyeti |
| `PERKS` | 63 koşu içi yükseltme |
| `SHOP` | 7 kalıcı mağaza ürünü |
| `GMODES` | 10 oyun modu (9 çekirdek + Haftalık Akın) |
| `REGIONS` | 9 bölge paleti |
| `DIFF` | 3 zorluk |
| `ACHS` | 70 başarım |
| `EVOLUTIONS` | 3 silah evrimi yolu × 3 kademe = 9 kademe |
| `ENEMY_BASE` + `ENEMY_VARIANTS` | 17 temel + 20 varyant = 37 düşman |
| `BOSS_BASE` + `BOSS_VARIANTS` | 5 temel + 6 varyant = 11 boss |
| `POWER_CATALOG` | 15 güçlendirme (altın ışın dahil) |
| `FUSIONS` | 15 gemi füzyonu; C(6,2) eşleşmeleri |
| `MISS_POOL` / `WPOOL` | 9 görev türü; günlük ve haftalık görev havuzları |
| `CAMP_GOALS` / `CAMP_MOD_GROUPS` | 8 kampanya hedefi, 16 modifikasyon |

## 300+ özellik

v9.9'da 300+ özellik ayrı bir katalog sekmesinde değil, doğrudan oyun sistemlerinde yaşar. Ayrı `300 İÇERİK` satırı, sayfası ve katalog kodu yoktur. Özellik dağılımı:

| Kategori | Adet |
|---|---:|
| Koşu yükseltmeleri (`PERKS`) | 63 |
| Düşmanlar (17 temel + 20 varyant) | 37 |
| Boss'lar (5 temel + 6 varyant) | 11 |
| Oyun modları (`GMODES`) | 10 |
| Galaksi bölgeleri (`REGIONS`) | 9 |
| Başarımlar (`ACHS`) | 70 |
| Güçlendirmeler (`POWER_CATALOG`) | 15 |
| Gemiler (`SHIPS`) | 6 |
| Füzyonlar (`FUSIONS`) | 15 |
| Skinler (`SKINS`) | 16 |
| Çipler | 3 |
| Mağaza ürünleri (`SHOP`) | 7 |
| İzler (`TRAILS`) | 3 |
| Patlamalar (`BOOMS`) | 2 |
| Rozetler (`BADGES`) | 7 |
| Kampanya modifikasyonları | 16 |
| Sezon ödülleri (`SEASON_REW`) | 19 |
| Zorluklar (`DIFF`) | 3 |
| Görev türleri (`MISS_POOL`) | 9 |
| Kampanya hedefleri (`CAMP_GOALS`) | 8 |
| Silah evrimi kademeleri (`EVO_TIERS`) | 9 |
| Can damlası | 1 |
| **Toplam** | **339** |

Bu sayım test köprüsünde dizilerin uzunlukları üzerinden doğrulanır; içerik sekmesi olmadığı için çalışma zamanında ayrı bir katalog nesnesi tutulmaz. Belgede ve pazarlama metinlerinde güvenli alt sınır olarak "300+" kullanılır.

## Aksiyon ısısı (v9.5)

`state.heat` 0–100 arasında bir metre tutar. `HEAT_TIERS` beş kademe tanımlar:

| Kademe | Eşik | Anahtar | Renk |
|---|---:|---|---|
| SOĞUK | 0 | `heat_0` | `#8fd8ff` |
| ISINIYOR | 24 | `heat_1` | `#7df0c0` |
| HIZLI | 46 | `heat_2` | `#ffd166` |
| ÖFKELİ | 68 | `heat_3` | `#ff9a5c` |
| KAOS | 86 | `heat_4` | `#ff5fa8` |

- **Etki.** `heatFireMul()` ateş beklemesini `1 − ısı × 0.0022` ile çarpar (100 ısıda ≈ %22 daha hızlı). `heatDmgMul()` hasarı `1 + ısı × 0.002` ile çarpar (100 ısıda %20 daha güçlü).
- **Besleme.** `chainKill()` öldürme başına 3.2, tank 5, koruma 9, boss 26 ısı ekler. Isı yalnızca `state.mode === 'playing'` iken dolar.
- **Soğuma.** Zincir açıkken 1.7/sn, zincir boşken 3.4/sn azalır. Hasar almak 30 ısı düşürür ve zinciri sıfırlar.
- **Geri bildirim.** Kademe atlayışında `heatPulse`, ekran bandı (`callout`), halka ve `sfx.rank()` çalışır. HUD'daki ince çubuk kademe rengini ve doluluk oranını gösterir.

## Öldürme zinciri, şarapnel ve nova (v9.5)

- `state.chainT` 2.4 saniyelik bir penceredir; her öldürme `state.chain` değerini artırıp pencereyi yeniler. Pencere dolarsa zincir sıfırlanır.
- **Şarapnel.** Zincir 6'ya ulaştığında her öldürme 2, 12'de 3, 20'de 4 adet delici şarapnel mermisi saçar. Mermi hasarı `max(0.5, 0.5 + dalga × 0.03) × st.dmg`; `bullets` dizisi 320 kaydı aşarsa üretim durur.
- **Nova.** Her 10 zincirde 92–172 px yarıçaplı bir nova patlar. Hasar `min(9, 1.2 + dalga × 0.3 + zincir × 0.06) × st.dmg`. Boss ve korumalar nova hasarından muaftır; `novaDepth` sayacı en fazla 2 iç içe tetiklemeye izin verir, böylece zincir kendi kendini sonsuz beslemez.
- **Görsel.** Şarapnel `fxBurst(..., 'star')`, nova iki halka ve 14 parça patlama üretir. `fxLevel() === 0` iken şarapnel sayısı %45 düşer.

## Bloom tamponu (v9.5)

`bloomBegin()` her karede 120 × 180 çözünürlüklü ikinci bir tuvale `0.25` ölçekle, `lighter` karışımla ışık lekeleri çizer; `drawBloom()` bu tamponu ekrana gerilerek bindirir.

- En fazla 48 ışık lekesi (`bloomN > 48` koruması) ve ekran dışı eleme vardır.
- `fxLevel() === 0` veya azaltılmış harekette tampon tamamen atlanır.
- Tampon 1/4 ölçekte olduğu için maliyet düşüktür; mobilde pil tasarrufu açıkken ek maliyet oluşturmaz.

## Gemi pasifleri ve zincir ödülleri (v9.6)

- `baseStats()` füzyonlardan sonra gemi pasifini uygular: `std` Overdrive kazancı ×1.15; `speed` atılma beklemesi ×0.85, ateş beklemesi ×0.92; `tank` +3 kalkan ve +0.6 sn dokunulmazlık; `nova` ısı kazancı ×1.2; `ghost` sıyırma yarıçapı +8 ve coin ×1.1; `titan` boss hasarı ×1.12 ve +1 bomba.
- `addOverdrive()` `st.odMul`, `addHeat()` `st.heatMul`, hasar sonrası dokunulmazlık `st.invBonus` çarpanlarını kullanır.
- 15/30/50 zincirde `dropPowerup()` güçlendirme bırakır ve `ZİNCİR ÖDÜLÜ ×n` bildirimi çıkar.
- Boss modülü yıkımı 12 ısı ve 0.05 Overdrive; zırh kırılması ek 0.12 Overdrive ekler.

## Oynanış 2.0 (v9.8)

- **Odak modu.** `state.touchFocus`, `state.padFocus` ve klavye `Space` aynı `player.focusOn` bayrağını besler. Odak açıkken hız `×0.52`, yayılım `×0.45`, hasar `×1.12` ve mermi hızı `×1.18` olur. `player.focus` 2.2 saniyede dolar; dolduğunda `fireWeapon()` otomatik olarak `w: 'lance'` mermisi üretir: `4.2×` hasar, `pierce: 8`, `r: 6.5`, `vy ≈ −1246`. Ateşleme sonrası şarj sıfırlanır ve `focusShots` sayacı artar.
- **Haftalık Akın.** `GMODES` onuncu kaydı `weekly`'dir; `CORE_MODES` dokuz çekirdek modu tutar ve `modes9` başarımı yalnızca bunları ister. `startGame()` haftalık modda `Math.random`'ı `mulberry32((weekIdx() * 7919 + 17) >>> 0)` ile değiştirir. `WEEK_MUTATORS` on kayıt içerir: `swarm`, `armor`, `rapid`, `sniper`, `gold`, `elite`, `meteor`, `frenzy`, `glass`, `titan`. `weekMutator()` hafta indeksine göre deterministik seçim yapar; `P.weeklyBest` ve `P.weeklyWeek` ayrı saklanır, hafta değişince rekor sıfırlanır.
- **Asistan paketi.** `S.asBomb`, `S.asAim`, `S.asSlow`, `S.asLife` dört isteğe bağlı yardımı açar. `assistCount()` ve `assistScoreMul()` skor çarpanını `max(0.8, 1 − 0.05 × n)` olarak hesaplar. Oto bomba ölümcül hasarda bombayı harcar ve 1.5 sn dokunulmazlık verir; nişan yardımı mermilere `homing: 0.6`, `turn: 2.4` ekler; yavaş mermi düşman mermisi hızını `×0.85` yapar; yedek can başlangıç canını +1 artırır. Ayarların beşinci sekmesi `game` bu dört anahtarı ve "Tümünü Kapat" eylemini gösterir.
- **Başarımlar.** `focus1` (ilk mızrak) ve `weekly1` (haftalık akında 5. dalga) eklendi; toplam 68.

## Silah evrimleri (v9.9)

`EVOLUTIONS` üç yolu tanımlar: `storm` (Fırtına), `rail` (Ray) ve `nova` (Nova). Her yolun `max: 3` kademesi vardır; `EVO_TIERS` toplamı 9'dur. Koşu durumu yalnızca `state.evo = { id, tier }` ile tutulur ve `resetRun()` tarafından temizlenir; kalıcı profile yazılmaz.

- **Zorunlu seçim.** `rollUpgradeOptions()` dalga 6'da `state.evo` boşsa slot 0–2'yi üç yolun 1. kademe kartlarıyla doldurur. Oyuncu atlarsa sonraki yükseltme ekranlarında dönen tek yol kartı slot 0'a gelir.
- **Kademe zamanları.** 2. kademe dalga ≥ 12, 3. kademe dalga ≥ 18 olduğunda sunulur; evrim kartı yine slot 0'ı alır. `chooseUpgrade()` `p.evo` dalını `p.fusion` dalından önce işler; seçim `evo1`, 3. kademe `evo3` başarımını açar.
- **Fırtına.** İsabette `stormChain(x, y, dmg, skip)` en yakın 2/3/4 düşmana sıçrar; hasar ve menzil kademeyle artar. 0.14 sn bekleme ve vurulan düşmanı atlama koruması vardır. 3. kademede `stormNova()` her 10 öldürmede yıldırım novası tetikler; iç içe tetikleme `state.evoStormDepth` ile sınırlanır.
- **Ray.** Atış sayacı her 5/4/3 salvoda bir tam delici ray üretir: 2.2×/3.0×/3.6× hasar, 7/10/13 delme. 3. kademe çift ray çizer. Ray görseli beyaz-sıcak çekirdek ve renkli halo ile çizilir.
- **Nova.** Mermi çarpması 44/58/72 px yarıçaplı patlama üretir; 3. kademede yanma hasarı eklenir. Patlama `evoNovaBlast()` içinde `state.evoNovaDepth` ile korunur.
- **Geri bildirim.** HUD'da evrim rozeti (yol rengi + kademe pipleri), duraklatma ekranında yapı çipi bulunur. Fırtına zincirleri renkli, ray ve nova patlamaları kademeye göre parlaklık kazanır. Tüm efektler `fxLevel()` ve parçacık bütçesine uyar.
- **Başarımlar.** `evo1` (ilk evrim) ve `evo3` (3. kademe) eklendi; toplam 70, özellik defteri 339.

## Can damlası (v9.9)

- **Düşmanlar.** Öldürülen her normal düşman için taban `%2.5` can damlası şansı vardır; tanklarda `+%3.5`, healer'larda `+%5`, elitlerde `+%15` eklenir. Şans `st.luckMul` ile çarpılır.
- **Korumalar ve boss'lar.** Koruma düşmanları `%30` şansla, her boss ölümü garantili olarak bir can damlası bırakır.
- **Sınır.** Can 6'daysa damla üretilmez. Damla `kind: 'life'` güçlendirmesidir; toplandığında `state.lives` en fazla 6 olacak şekilde +1 artar ve `p_life` bildirimi çıkar.
- **Görsel.** Kalp ikonlu, pembe (`CC.life`) halkalı standart güçlendirme damlası; mıknatıs ve manyetik çekim kurallarına uyar.

## Arayüz 6.0 (v9.7)

- **Ana menü.** `renderMenu()` komuta güvertesi düzenini çizer: `menuProfile()` sezon şeridi, `drawMenuHero()` gemi vitrini, üç `menuChip()` (gemi/mod/zorluk), büyük CTA ve 3×3 `menuTile()` ızgarası. `menuDaily()` günlük operasyon kartını üretir. Sayfa geçişleri `state.pageFade` ile karartılır; `S.uiAnim` kapalıyken atlanır.
- **Hangar 2.0.** `state.hangarSel` karusel seçimini, `state.skinPage` 8'li skin sayfasını tutar. `renderHangar()` gemi istatistik çubuklarını `baseStats()` üzerinden hesaplar; pasif kartı `pas_<gemi>` metnini gösterir. Skin açma koşulları `SKIN_RQ`/`SKIN_OPEN`, satın alma `P.skinsUsed` üzerinden yürür.
- **Yükseltme 2.0.** `rollUpgradeOptions()` üç kart üretir; `perkRarity()` ve `perkIcon()` kart görünümünü belirler. `rerollUpgrades()` 30 coin karşılığında seçenekleri yeniler (dalga başına bir kez), `skipUpgrades()` +20 coin verip koşuya döner. Eğitimde iki eylem de kapalıdır.
- **Duraklatma ve sonuç.** `renderPause()` dalga/kill/zincir özeti, `state.progs` tabanlı donanım çipleri ve günlük hedef ilerlemesini çizer. `runGrade()` skor, dalga, kombo ve isabetten S–D derecesi üretir; `GRADE_COL` renkleri `renderOver()` halkasında kullanılır. `state.seasonGain` sonuç ekranındaki XP dökümünü besler.
- **ARAYÜZ ayarları.** `S.lefty` dokunmatik tuşları, joystick yarısını ve bomba/can göstergelerini aynalar. `S.hudMin` güç rozetlerini gizler, `S.aimLine` `drawAimGuide()` dikey kılavuzunu açar, `S.uiAnim` sayfa karartmasını denetler.
- **Skinler.** `SKINS` 16 kayda çıktı; yeni `void`, `reactor`, `prism`, `wraith`, `chrono`, `zenith` koşulları `SKIN_RQ`/`SKIN_OPEN` içinde tanımlıdır.

## Füzyonlar ve kanat filosu (v9.4)

- `FUSIONS` altı geminin tüm ikili eşleşmelerini içerir: C(6,2) = **15** kayıt. Her kayıt `a`, `b`, renk, ikon ve `apply(st)` fonksiyonu taşır.
- Füzyon kartı yalnızca 6. dalgadan sonra yükseltme ekranında çıkar ve yalnızca uçulan gemiyle eşleşen, henüz açılmamış kayıtlar arasından seçilir.
- Seçim `P.fusions[id] = true` olarak kalıcılaşır; aynı koşuda can/bomba/kalkan farkı anında uygulanır. Etki, çiftteki iki gemiden biriyle uçarken geçerlidir.
- **Kanat filosu.** `wingStars()` açılan füzyon sayısını 0–5 aralığına sıkıştırır; `wingCount()` 1/3/5 eşiklerinde 1/2/3 eskort döndürür. `updateWings()` en yakın düşmanı 560 px içinde arar ve `max(0.36, 0.78 − yıldız × 0.06)` aralığında ateş eder. Eskort hasarı `(0.9 + (dmg−1) × 0.35 + yıldız × 0.28)`, Overdrive sırasında ×1.35'tir.
- **Arayüz.** `menuPage = 'fusion'` sayfası 15 kartı üçerli sayfalar hâlinde gösterir; açık/kilitli durumu ve toplam ilerleme (`x/15 füzyon`) görünür.

## Çevrimdışı düello (v9.4)

- `startVersus()` 60 saniyelik bir koşu kurar: `state.versus = { active, t, pKills, rKills, pScore, rScore, rival }`.
- Rakip yapay zekâ `rivalKill` işaretli düşmanları avlar; bu öldürmeler oyuncunun skoruna, kombo zincirine veya görev ilerlemesine yazılmaz.
- Rakip gemi kendi nişan sistemiyle ateş eder, hasar alınca sarsılır ve yeniden konumlanır.
- Süre bitince `endVersus()` sonucu belirler: `win`, `lose` veya `draw`. Galibiyet `30 + 2 × av` coin, 1 toz ve 5. galibiyette `duelist` başarımı verir.
- `P.vsBest`, `P.vsPlayed` ve `P.vsWins` profilde saklanır; `renderVersusEnd()` sonuç ekranını çizer.

## Altın ışın (v9.4)

`p_beam` güçlendirmesi `player.beamT = 2.6` kurar. `updatePlayer()` her karede ışının kolonundaki düşmanlara ve boss modüllerine DPS uygular; `drawBeams()` beyaz-sıcak çekirdek, paralel altın raylar ve dallı yıldırımlarla çizer. HUD `beam_hud_fmt` ile kalan saniyeyi gösterir. Işın delici olduğu için aynı kolondaki tüm hedefleri biçer.

## Kanatlı kombo bildirimleri (v9.4)

`drawCallout()` kombo eşiklerinde `İYİ!`, `HARİKA!`, `MÜKEMMEL!`, `İNANILMAZ!`, `EFSANE!` yazılarını çizer. Bildirim iki yana açılan dört tüylü altın enerji kanadı, arkasında renkli radyal patlama ve ölçek animasyonu taşır. `S.rmotion` veya `fxLevel() === 0` iken kanatlar ve patlama atlanır, yalnızca metin gösterilir.

## Overdrive ve boss modülleri (v9.3)

- **Overdrive.** `state.od` 0–1 arası dolar; graze, kill ve modül yıkımı besler. `state.odT` 6.5 saniye sürer; ateş hızı yaklaşık iki katına çıkar, öne üç ek mermi ve arkaya kuyruk atışı eklenir. Aktifken tekrar tetiklenemez.
- **Boss modülleri.** Her boss `e.mods` dizisinde iki yörünge taret taşır (`orb: 74 + i × 9`, `r: 10.5`). Modüller oyuncuya nişan alan yay ateşi açar, gövdeden ayrı vurulur ve yıkıldıklarında coin, güçlendirme ve Overdrive bırakır.
- **Hasar çarpanı.** Modüllerden biri hayattayken boss hasarı `×0.72`; ikisi de yıkılınca `×1.12` zırh kırılması uygulanır. `damageBossModule()` son modülü de yıktığında `bossArmorBreak()` çağrılır.
- **HUD.** Modül çubukları boss can barının altında ayrı ayrı izlenir; `MODÜL İMHA` ve `ÇEKİRDEK ZIRHI KIRILDI` bildirimleri çıkar.

## Kayıt şeması

İki anahtar kullanılır:

- `ya_profile` — kalıcı ilerleme: coin, toz, rekorlar, haftalık rekor (`weeklyBest`/`weeklyWeek`), oynanan gemiler, açılan skinler, başarımlar, gemi ağaçları, görev durumu, istatistikler, bonus kampanya yıldızları, füzyonlar, düello sayacı.
- `ya_settings` — dil, ses, sarsıntı, parçacık/efekt kalitesi, renk körü modu, azaltılmış hareket, FPS sayacı, FPS sınırı, pil tasarrufu, dokunmatik hassasiyet, sol el düzeni, sade HUD, nişan çizgisi, arayüz animasyonu ve dört oynanış asistanı (`asBomb`, `asAim`, `asSlow`, `asLife`).

Şema yüklenirken eksik alanlar varsayılanlarla tamamlanır. Bu, eski sürümlerden gelen profillerin bozulmadan açılmasını sağlar.

Yedek kodu `YA2.<base64-json>.<fnv1a>` biçimindedir. İçe aktarmada uygulama kimliği, sürüm aralığı ve FNV sağlama toplamı doğrulanır; ardından tüm sayısal alanlar sınırlanır, bilinmeyen anahtarlar atılır ve yalnızca tanımlı başarım/rozet/kozmetik/füzyon kimlikleri kabul edilir.

## Görev üretimi

- **Günlük görev:** tarih (`YYYY-M-D`) tohum olarak kullanılır; aynı gün herkeste aynı üç görev üretilir.
- **Haftalık görev:** haftanın pazartesi tarihi anahtarı FNV-1a ile karıştırılıp tohum yapılır.
- Görevler `pickTasks` ile havuzdan seçilir; hedef aralıkları sabittir.
- İlerleme olay tabanlıdır (`missAdd`); ödül talebi ayrı bir kullanıcı eylemidir.

## Eğitim ve sezon

- **Eğitim:** `startTutorial()` dört adımlı bir durum makinesi kurar (`state.tut`). Hareket, hedef temizleme, bomba ve yükseltme adımları tamamlanınca `tutorialFinish()` çalışır. Eğitim sırasında hasar kapalıdır ve öldürmeler normal ödül/mission ilerlemesi üretmez.
- **Sezon:** `seasonNeed(lv)` artan XP eşiği üretir; `seasonAddXp()` seviye atlamalarını ve `SEASON_REW` ödüllerini işler. `seasonGrant()` coin/toz/rozet/görünüm verir, `badges` ve `badge` profil alanlarında saklanır.

## Bölgeler ve müzik

`regionIdx()` dalga numarasından bölgeyi hesaplar: `floor((wave - 1) / 5) % 9`. Bölge; arka plan renklerini, yıldız tonunu, sis katmanını ve müziğin kök sesini değiştirir. 9 bölge: Nebula, Crimson, Ice, Belt, Dark, Solar, Violet, Emerald ve Void.

Müzik motoru phonk esintili, tamamen prosedüreldir:

- 125 BPM, 16'lık notalardan oluşan 32 adımlık döngü
- Am–F–C–G minör akor ilerlemesi
- 808 bas (pitch glide + waveshaper), cowbell melodi, kick/snare/hi-hat
- Plak cızırtısı, tape saturasyonu ve kompresörlü master zinciri
- Boss savaşlarında ek perküsyon ve oktav katmanları
- Bölgeye göre kök ses transpozisyonu

Tüm sesler Web Audio osilatörleri ve gürültü tamponlarıyla üretilir; harici dosya yoktur.

## Görsel efekt katmanı

- **Silah ve isabet.** `impactFx` mermi tipine göre iz, çekirdek ve kısa ömürlü parçacık üretir. `fxBurst` yıldız/halka patlamalarını `bursts` dizisinde tutar; `enemyDeathFx` düşman tipine göre ayrı renk, enkaz ve halka kombinasyonu seçer. `bossArmorBreak` zırh çatlağı, halka ve ekran sarsıntısını tetikler.
- **Galaksi katmanları.** `buildGalaxy(idx)` her bölge için 240 × 360 çözünürlükte galaksi, gezegen, nebula ve yıldız kümesi içeren bir tuval üretir. Sonuç `galC` içinde önbelleklenir; çizim sırasında yalnızca ölçeklenip hafif parallax ile kaydırılır. `fxLevel() === 0` iken bu katman atlanır.
- **Boss anlatımı.** `drawBossWarnings` uyarı çizgisini ve oyuncuya kilitlenen nişangâhı çizer; `b.phaseT` faz geçişini, `b.breakT` zırh kırılmasını, `e.phase === 2` ise faz 2 ışık halkalarını yönetir. Yeni aura ve halkalar `fxLevel() > 0 && !S.rmotion` koşuluna bağlıdır.
- **Yenilgi sinematiği.** Boss canı bittiğinde `startBossDeath` `state.bossDeath` durumunu kurar; `updateBossDeath` 2.35 saniyelik kısa bir sekans oynatır, ardından normal `killEnemy` akışını çalıştırır. Dokunma, tıklama, boşluk veya Enter `skipBossDeath` ile sekansı kısaltır. Sinematik sırasında `damagePlayer` erken döner. `filterDead` sahipsiz kalan `state.bossDeath` durumunu temizleyerek ekranın veya hasar korumasının kilitlenmesini engeller.
- **Oyuncu ve HUD.** Motor alevleri `moveMag` ve `dashFx` değerlerine, kalkan dalgası `shieldHit` değerine bağlıdır. HUD'da sağlık/kalkan çubukları ayrıştırılmış, kombo bildirimi `scorePulse`/`comboPulse` ile animasyonlanmıştır.
- **Bütçe.** Tüm parçacıklar `pushP`/`budget()` üzerinden ilerler; `fxLevel`, pil tasarrufu, `fpsCap` ve `S.rmotion` mevcut ayarlarla uyumludur.

## Sanat paketi

- **Gömülü WebP.** `window.YA_ART` tek satırda 6 gemi, 12 düşman sprite'ı, 8 boss montajı ve 9 bölge arka planı taşır; paket sürümü `9.3`. Çalışma anında hiçbir dosya indirilmez; `file://` ve APK `assets` yolu aynı şekilde çalışır.
- **Tembel görsel çözme.** `artImage(entry)` her veri URL'si için bir `Image` nesnesini ilk kullanımda oluşturur; `onload` olana kadar prosedürel çizim yolu kullanılır. Bu yüzden sanat hazır olmadan da kare düşmez.
- **Renk tonlama önbelleği.** `artTint(entry, color)` görseli bir tuvale kopyalayıp `source-atop` ile renklendirir; sonuç `WeakMap` içinde tutulur. Vuruş parlaması ve varyant tonları her karede yeniden üretilmez.
- **Boss montajı.** Boss görselleri `dw/dh/ax/ay` çapa değerleriyle parçalardan birleştirilir; `drawBossBody` gövde, aura ve silah katmanlarını aynı çapa sistemine göre çizer.
- **Geri dönüş.** `ART` yoksa veya görsel yüklenemezse `artEntry`/`artBg`/`artEnemy` `null` döner ve prosedürel çizim yolu devreye girer.
- **Lisans.** Kaynaklar ve lisanslar [CREDITS.md](../CREDITS.md) içinde; Kenney ve ambientCG CC0, NASA fotoğrafları kamu malı.

## Görsel yenileme

- **Çözünürlük ve önbellek.** `buildBiome()` bölge sahnelerini `480 × 720`, `buildGalaxy()` galaksi katmanını `240 × 360`, ön plan siluetlerini `240 × 360` ve menü arka planını `960 × 1440` tuvalde üretir. Sonuçlar bölge başına bir kez önbelleklenir; kare içinde yalnızca ölçekleme ve parallax yapılır.
- **Doygun bölge paletleri.** `REGIONS` içindeki `bg`, `star` ve `tint` değerleri bölge başına canlı biome renklerine göre ayarlandı. `buildGalaxy()` her bölge için üç büyük nebula bulutu ve en az bir gezegen çizer.
- **Üç katmanlı parallax.** Arka planda galaksi/nebula, ortada bölge gövdesi ve `biomeFG` ön plan silueti oyuncunun konumuna göre farklı hızlarda kayar. `fxLevel() === 0` veya `S.rmotion` açıkken ek katmanlar sadeleşir.
- **Bölge simgeleri.** `biomeLandmark()` bölgeye özel dev siluet çizer (enkaz gövdesi, halka istasyonu, buz katedrali, kovan kulesi, boşluk yarığı, güneş paneli, asteroid platformu).
- **Atmosfer.** Hacimsel ışık huzmeleri, kaynak halesi, anamorfik lens çizgileri, lens hayaletleri, bölgesel ışık olayları, ön plan bokeh'i ve yıldız tozu; hepsi `fxLevel()` ve parçacık bütçesine bağlı.
- **Oyuncu.** `drawShip()` gövde ölçeği `B = 1.56`; çift motorlu kısa ömürlü plazma izi `shipTrail` ile çizilir, büyütülmüş motor bloom'u, hıza bağlı egzoz konisi, yatay lens çizgisi ve kanat ucu seyrüsefer ışıkları eklenir.
- **Düşman ve boss.** Normal düşmanlar `1.26` görsel ölçekle, zemin gölgesi, güçlü hale ve kenar ışığıyla çizilir; hale `fxLevel() > 0` koşuluna bağlıdır. Boss'lar `1.12` görsel ölçekle, dönen aura halkaları, enerji düğümleri, gövdeye çakan dallı yıldırımlar, zemin gölgesi ve faz 2 enerji yaylarıyla çizilir; boss isabet kutusu, AI ve zamanlama değişmez.
- **Mermi ve ışın.** Oyuncu mermileri katmanlı plazma dartı, düşman mermileri sıkılaştırılmış dış haleli enerji küresidir. Boss uyarı koridoru altın raylar ve kırmızı uyarı düğümleri taşır; ateşlenen ışın beyaz-sıcak çekirdek, paralel altın raylar, enerji düğümleri ve çekirdekten taşan dallı yıldırımlarla çizilir.
- **HUD ve dokunmatik.** Boss can barında hasar çipi ve 20 bölmeli segment yapısı; dokunmatik tuşlarda altıgen plaka, kapasite halkası, eğim, köşe çentiği, etiket ve bomba pipleri kullanılır. v9.5'te ısı çubuğu ve zincir rozeti bu düzene eklendi.

## Akın dalgası

- `buildWave(n)` önce Boss Akını ve boss dalgası kontrollerini yapar. `n >= 4 && n % 5 === 4` koşulunda `state.mod = 'horde'` kurulur ve normal rastgele dalga üretimi atlanır.
- Akın kuyruğu tam **50** spawn kaydı içerir: 3 V formasyonu (15 scout), 8 dalışçı, 4 hücumcu, 6 nişancı, 3 tank (biri elit), 4 bölünen, 4 kalkanlı (ikisi elit), 3 dokuyucu ve 3 fantom. Bölünenlerin alt parçaları ve bombacı mayınları bu 50'ye ek olarak doğabilir.
- Kayıtlar `t` zaman damgasına göre sıralanır; spawn aralıkları 0.05–0.45 sn olduğu için pencere yaklaşık 5.7 saniyedir.
- `state.waveTotal` ve HUD dalga ilerlemesi 50 hedefini kullanır. Dalga temizlendiğinde normal `waveClear()` akışı çalışır; boss ve yükseltme ritmi değişmez.

## Daha kalabalık dalgalar

- **Normal dalga tabanı:** `Math.min(150, Math.round((12 + n * 4.6) * dm.cnt * danger * campDensity))`.
- **Spawn aralığı:** Tek düşmanlar için `max(0.08, rand(0.17, 0.42) - n * 0.02)`; V formasyonu, dalışçı ve hücumcu paketlerinin araları da sıkıdır.
- **Dalga ortası takviye:** Ana dizilimden sonra `3 + min(5, floor(n / 3))` düşmanlık kısa bir takviye kuyruğu eklenir; `t` değeri ana dalganın %58'ine yerleştirilir.
- **Aktif düşman tavanı:** `activeCap()` normalde 72, horde dalgasında 84, pil tasarrufunda 48 döndürür.
- **Kare başına spawn bütçesi:** Aynı karede en fazla 5 spawn yapılır.
- **Boss korumaları:** Boss dalgasına `8 + min(20, floor(n * 0.9))` koruma eklenir; kampanya `sik/seyrek` modifikasyonu bu sayıyı ölçekler. Boss ölse bile korumalar temizlenene kadar dalga bitmez.
- **Asteroid dalgası:** 22 asteroid + 8 scout üretir.
- **Horde istisnası:** 50 düşmanlık akın tam 50 kalır; yeni tavan yalnızca normal ve boss dalgalarını etkiler.

## Boss isabet düzeltmesi

- `bossLeadPoint()` oyuncunun hızını ve mermi hızını kullanarak boss'un öngörülü merkez noktasını hesaplar.
- Merkezden atış yapan top mermileri `st.bossDmg` çarpanını boss'a uygular.
- Boss canı `(48 + dalga × 11) × dm.hp × bossTipi × varyant`; temel yatay hız 62, faz 2'de 96'dır.
- Boss varyantları `state.bossIdx++ % 10` sırasıyla seçilir; 0–4 temel, 5–9 varyanttır.

## Bonus kampanya

- 5 halka × 60 görev = 300 görev. Tüm görevler baştan açıktır.
- `campMission(i)` deterministik ad, hedef, modifikasyon, ödül ve yıldız eşikleri üretir.
- 8 hedef türü: dalga, kill, boss, puan, kombo, süre, hasarsız dalga ve para.
- 16 modifikasyon: hızlı/yavaş, sık/seyrek, güçlü/zayıf boss, tek/bol can, hızlı ateş, büyük mermi, kritik, kalkan, meteor, elit, altın ve dar hedef.
- İlk temizlemede ödül verilir; tekrar oynayışta ödül yoktur. Daha düşük yıldız, kayıtlı en iyi yıldızın üzerine yazmaz.
- `state.menuPage = 'camp'` görev haritasını, `'campinfo'` görev detayını açar. Ana menüdeki `BONUS KAMPANYA` satırı tam genişliktedir.

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
| Sürüm | 9.9 (versionCode 20) |
| minSdk | 21 (Android 5.0) |
| targetSdk | 29 |
| İzinler | Yok |
| İmza | Debug (sideload) |
| APK boyutu | ~0.8 MB |

## Geliştirme

Tarayıcıda açmak yeterlidir:

```powershell
start yildiz-akini.html
```

Yerel sunucu ile test etmek için:

```powershell
python -m http.server 8127 --bind 127.0.0.1
```

Ardından `http://127.0.0.1:8127/yildiz-akini.html` adresini aç.

## Test kontrol listesi

Otomatik Playwright paketi 91 kontrol içerir; son çalıştırmada **91/91** geçti.

- Menü açılışı, 480 × 720 mantıksal alan ve canvas backing store doğru.
- 15 füzyon, 15 benzersiz gemi çifti, 3 evrim yolu, 9 evrim kademesi ve 70 başarım sayımı tutarlı.
- TR/EN anahtar ve yer tutucu pariteleri tam.
- Boss tam olarak her 5. dalgada; akın 4, 9, 14, 19, 24. dalgalarda ve tam 50 düşmanla geliyor.
- Boss dalgaları koruma taşıyor; yükseltme her 3. dalgada açılıyor; tüm dalga kuyrukları dolu.
- Overdrive kısmi dolum, 6.5 saniyelik tetikleme, aktifken engelleme ve süre bitişi doğru.
- Boss modülleri: iki modül, ×0.72 hasar azaltımı, modül yıkımında zırh kırılması ve ×1.12 bonus.
- Her geminin 5 füzyon seçeneği var; tüm füzyonlar sonlu istatistik üretiyor; kart seçimi oyunu sürdürüyor ve profile yazılıyor.
- Düello 60 saniyede başlıyor, süre bitince sonuç veriyor, rakip kill sayacı işliyor.
- Altın ışın kolondaki düşmanlara hasar veriyor ve süresi bitince kapanıyor.
- Isı: kademe ve tamponlar (ateş hızı < 1, hasar > 1), kademe bildirimi, zamanla soğuma, hasarda 30 puan düşüş ve zincir sıfırlama.
- Zincir: 10 öldürmede zincir ve en iyi değer, şarapnel mermisi, nova darbesi ve bildirimi, pencere bitince sıfırlanma.
- Evrim: dalga 6'da üç yol kartı, seçim sonrası `state.evo`, dalga 12/18 kademe teklifleri, Fırtına zinciri, Ray delme sayısı ve Nova patlama yarıçapı doğru; `evo1`/`evo3` başarımları açılıyor.
- Can damlası: boss ölümünde ve düşman öldürmede `life` damlası üretiliyor; toplandığında can +1 ve 6 üst sınırı korunuyor.
- Azaltılmış hareket + `fx0` + pil tasarrufunda çizim hatasız.
- Dokunmatik derlemede joystick, dash ve yetenek tuşları çalışıyor; 360 px genişlikte HUD taşmıyor.
- Komuta güvertesi kutucukları, hangar karuseli ve skin sayfası, yükseltme yenileme/atlama, duraklatma ve sonuç ekranı hatasız çiziliyor.
- Sol el modunda dokunmatik tuşlar ve HUD aynalanıyor; sade HUD güç rozetlerini gizliyor; nişan çizgisi yalnızca oyun sırasında görünüyor.
- Günlük/haftalık görev ilerlemesi ve ödül talebi doğru; ağaç satın alımları coin düşürüyor.
- Kilitli skin/iz/patlama seçilemiyor; eski kayıt güvenli varsayılana dönüyor.
- Oyun sonu ekranı önceki rekorla karşılaştırma yapıyor; eğitim dört adımda tamamlanıyor ve atlanabiliyor.
- Sezon XP, seviye ödülleri, rozet seçimi ve kilitli görünümler doğru.
- Geçerli yedek geri yükleniyor; bozuk hash, yanlış uygulama ve sınır dışı değerler reddediliyor/temizleniyor.
- 30/45/60 FPS ve pil tasarrufu modlarında çizim hatasız.
- `300 İÇERİK` sekmesi yok; özellik dizileri hâlâ tam.
- Konsolda hata veya uyarı yok.
- Odak modu: hız ≈×0.52, şarj 2.2 sn, mızrak 4.2× hasar ve 8 delme; bırakınca şarj sıfırlanıyor.
- Haftalık Akın: tohum ve mutatör deterministik, haftalık rekor ayrı, hafta değişince sıfırlanıyor; `modes9` yalnızca 9 çekirdek modu istiyor.
- Asistanlar: skor çarpanı 1/0.95/0.80, yedek can +1, nişan yardımı, yavaş mermi, oto bomba ve ayarların OYNANIŞ sekmesi doğru.
- Dokunmatik ODAK tuşu basılı tutunca şarj ediyor, bırakınca temizleniyor; gamepad LT/RT aynı davranışı veriyor.

## Performans notları

- Parçacık ve efekt yoğunluğu ayarlardan düşürülebilir; pil tasarrufu parçacık bütçesini, nebula katmanlarını ve parlamayı azaltır.
- FPS sınırı `requestAnimationFrame` döngüsünde uygulanır; pil tasarrufu 30 FPS'e sabitler.
- Bloom tamponu 1/4 ölçekte ve en fazla 48 ışık lekesiyle çalışır; `fxLevel() === 0` iken tamamen atlanır.
- Şarapnel üretimi `bullets` dizisi 320 kaydı aşınca durur; nova en fazla iki kez iç içe tetiklenir.
- Ekran sarsıntısı ve azaltılmış hareket bağımsız kapatılabilir.
- Arka plana alınan sekmede oyun otomatik duraklar.
- Galaksi katmanları önbelleklendiği için kare başına yeniden üretim yapılmaz.
- Normal dalgalarda kuyruk 150 kayda kadar çıkabilir; aktif tavan ve 5 spawn/kare sayesinde ekranda aynı anda tutulan düşman sayısı sınırlı kalır.
- Çizim tek canvas üzerinde yapılır; DOM katmanı yalnızca HUD için kullanılır.
- 240 saniyelik otopilot koşusu: dalga 21, 1.166 kill, 6 yükseltme, 15 Overdrive, 0 NaN, 0 konsol hatası; başsız ortalama kare süresi ~46.5 ms.
