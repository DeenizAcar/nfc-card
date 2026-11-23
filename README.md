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

Web NFC yalnızca **Android + Chrome** ve **https** üzerinde çalışır. En kolay yol GitHub Pages:

1. Repo → **Settings → Pages** → Source: `Deploy from a branch`, Branch: `main` / `(root)`.
2. Birkaç dakika sonra `https://<kullanıcı-adın>.github.io/nfc-card/` adresini telefonda Chrome ile aç.
3. Chrome menüsünden **Ana ekrana ekle** ile uygulama gibi kullanabilirsin.

> Not: Özel (private) repoda GitHub Pages için GitHub Pro gerekir. Kodda kişisel veri olmadığı için repo herkese açık
> olsa da kayıtların görünmez — onlar sadece telefonunda durur.

Yerel test için bilgisayarda `npx serve` vb. çalıştırıp telefondan açmak işe yaramaz (http olduğu için); Pages ya da başka bir https barındırma kullan.
