# Güvenlik Politikası

## Desteklenen sürümler

| Sürüm | Destek |
|---|---|
| 8.x | Aktif |
| 7.x ve öncesi | Desteklenmiyor |

## Açık bildirimi

Güvenlikle ilgili bir sorun bulduysan lütfen **herkese açık bir issue açma**. Bunun yerine:

1. Deponun **Security** sekmesine git.
2. **Report a vulnerability** seçeneğini kullan.
3. Sorunu, etkilenen sürümü ve mümkünse yeniden üretme adımlarını ekle.

Depo özel olduğu için GitHub Güvenlik Danışmanlığı üzerinden özel bildirim yapılabilir. Bildirimler en kısa sürede, iyi niyet çerçevesinde değerlendirilir.

## Kapsam

Yıldız Akını bilerek ağ erişimi kullanmaz:

- HTML sürümü harici kaynak yüklemez.
- APK, `INTERNET` izni istemez.
- Hiçbir analitik, reklam veya uzak kayıt servisi yoktur.
- Tüm veriler cihazdaki `localStorage` alanında tutulur.

Bu nedenle öncelikli inceleme alanları; HTML enjeksiyonu, yerel depolama taşmaları, WebView yapılandırması ve APK imzalama sürecidir.

## Kötüye kullanım

Oyunun kopyalarını dağıtan, sahte APK yayan veya markayı izinsiz kullanan kaynakları lütfen aynı kanaldan bildir.
