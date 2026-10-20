# Katkı Rehberi

Yıldız Akını kişisel ve özel bir projedir. Depo herkese açık olmadığı için katkılar davetle ve önceden konuşularak alınır.

## Bir sorun bildirmeden önce

- Aynı sorunun daha önce bildirilip bildirilmediğini kontrol et.
- Sürümü, platformu (Android/Windows/macOS/Linux), tarayıcıyı ve oyun modunu belirt.
- Konsol hatası varsa tam metni ekle.
- Ekran görüntüsü veya kısa ekran kaydı ekle.

## Geliştirme ilkeleri

- Oyun tek bir HTML dosyası olarak kalmalıdır; harici bağımlılık eklenmemelidir.
- Türkçe ve İngilizce metinler aynı anda güncellenmelidir.
- Yeni kayıt alanları geriye uyumlu olmalı; eski `localStorage` verisi bozulmamalıdır.
- Mobil öncelikli düzen korunmalı; 360 px genişlikte taşma olmamalıdır.
- Görsel ve işitsel varlıklar prosedürel üretilmeli, depoya ikili dosya eklenmemelidir.
- Performans hedefi: orta seviye telefonda 60 FPS.

## Değişiklik kontrol listesi

- [ ] Altı mod da açılıyor ve oynanabiliyor.
- [ ] Altı gemi ve altı yetenek çalışıyor.
- [ ] Yeni metinlerin TR/EN karşılıkları var.
- [ ] Kayıt/yükleme eski profilleri bozmuyor.
- [ ] Dokunmatik HUD küçük ekranda taşmıyor.
- [ ] Konsolda hata yok.
- [ ] `CHANGELOG.md` güncellendi.

## Commit mesajları

Kısa, emir kipinde ve kapsam belirten mesajlar kullan:

```
ekle: haftalık mutatör modu
düzelt: kilitli skin geri dönüşü
güncelle: v9 sürüm notları
```
