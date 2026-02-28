# LoL Patch Notes Discord Bot (discord.js)

Bu bot, **League of Legends** için en güncel **yama notlarını** takip eder ve:

- Otomatik olarak belirlediğin kanala (ör. `#patch-notes`) yeni yama notunu paylaşır
- Slash komutu `/guncel` ile anlık olarak en güncel yama notunu kanala gönderir

> Not: Riot'un patch notes için resmi bir JSON API'si bulunmadığı için bot, League of Legends sitesindeki "Patch Notes" liste sayfasını **çekip** en yeni yama yazısını bulur (scrape). Bu yöntem site HTML'inde değişiklik olursa güncelleme gerektirebilir.

---

## 1) Kurulum

### Gereksinimler
- Node.js **18+** (önerilir)
- Discord Bot Token

### Dosyaları indir
Bu projeyi klasör olarak aç.

### Paketleri kur
```bash
npm install
```

---

## 2) Discord Developer Portal Ayarları

1. Developer Portal > Applications > Bot
2. **Privileged Gateway Intents**:
   - Bu bot için mesaj okuma niyeti gerekmez. Sadece slash komut ve kanala yazma yeterli.
3. Botu sunucuna davet ederken şu izinler yeter:
   - `Send Messages`
   - `Embed Links`
   - `Read Message History` (opsiyonel)
   - `Use Application Commands`

---

## 3) Yapılandırma (config)

Kök dizinde `config.example.json` dosyasını `config.json` olarak kopyala:

```bash
cp config.example.json config.json
```

Sonra `config.json` içini doldur:

- `token`: Discord bot token
- `clientId`: Uygulama (Application) ID
- `guildId`: Komutları hızlı eklemek için sunucu ID (development için önerilir)
- `channelId`: Yama notlarının atılacağı kanal ID
- `checkIntervalMinutes`: Otomatik kontrol aralığı (dakika)
- `patchNotesListUrl`: Patch notes liste sayfası (TR)

---

## 4) Slash komutlarını kaydet (register)

> Slash komutları bir kere kaydedilir; sonrasında botu çalıştırırsın.

```bash
npm run register
```

---

## 5) Botu çalıştır

```bash
npm start
```

Bot online olunca:
- `/guncel` yaz → en güncel yama notunu kanala atar
- Bot arka planda `checkIntervalMinutes` aralığıyla yeni yama var mı kontrol eder

---

## 6) Sorun giderme

- Bot kanala yazmıyorsa: kanal izinlerini ve `channelId`'yi kontrol et
- `/guncel` görünmüyorsa: `npm run register` çalıştırdığından emin ol, doğru `guildId` yaz
- Site değiştiyse: `src/patchNotes.js` içindeki seçiciler güncellenebilir

---

## Lisans
Kullanım serbest; istersen geliştirebilirsin.
