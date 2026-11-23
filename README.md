# NFC Kopyalayıcı

Android telefonla NFC kartları/etiketleri okuyup kaydeden ve başka bir karta yazan tek sayfalık web uygulaması.
Kurulum gerektirmez; Chrome'da açılır. Veriler sadece telefonun tarayıcısında saklanır, hiçbir sunucuya gönderilmez.

## Neler yapar

- **Oku:** Kartın UID'sini ve içindeki NDEF kayıtlarını (link, metin, Wi‑Fi, vCard, mime vb.) gösterir.
- **Kaydet:** Okunan kartı isim vererek listeye ekler.
- **Kopyala:** Kayıtlı ya da az önce okunan kartın içeriğini başka bir etikete yazar.
- **Elle yaz:** Link, metin veya Wi‑Fi bilgisi yazar.
- **Yedekle:** Tüm kayıtları JSON olarak dışa/içe aktarır (telefon değiştirirken işe yarar).

## Sınırlar (önemli)

Web NFC sadece **NDEF** verisiyle çalışır. Bu yüzden:

- Kartın **UID'si kopyalanamaz** (hedef kart kendi UID'sini korur). UID'ye bakan sistemler kopyayı tanımaz.
- Şifreli kartlar (MIFARE Classic bina/otel kartları, İstanbulkart gibi ulaşım kartları, banka kartları) okunamaz.
- Hedef etiket NDEF destekli ve yeterli kapasitede olmalı (NTAG213/215/216 gibi).

## Kullanım

- **Web:** https://deenizacar.github.io/nfc-card/ — Android telefonda Chrome ile aç.
- **APK:** https://deenizacar.github.io/nfc-card/apk/ — Android uygulaması olarak kur.

Web NFC yalnızca **Android + Chrome** ve **https** üzerinde çalışır. APK, siteyi Chrome üzerinden
açan bir Trusted Web Activity'dir; telefonda Chrome yüklü olmalı.

## Yayınlama

`main`e her push'ta `.github/workflows/pages.yml` `android/` projesinden imzalı APK derler ve
siteyi APK ile birlikte (`/apk/nfc-kopyalayici.apk`) GitHub Pages'e yükler.

İmzalama için repo secret'ları: `KEYSTORE_BASE64`, `KEYSTORE_PASSWORD`, `KEY_ALIAS`.
Keystore repoda değil; kaybolursa yeni APK eskisinin üzerine kurulamaz (önce kaldırmak gerekir).
