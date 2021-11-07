# eay-hesapmakinesi
NodeJS için hesap makinesi modülüdür.

## Nasıl indirilir?
```
npm i eay-hesapmakinesi
```

## Kullanımı
1. İki sayıyı toplamak için `topla()` kullanılır.
2. İki sayıyı çıkarmak için `çıkar()` kullanılır.
3. İki sayıyı çarpmak için `çarp()` kullanılır.
4. İki sayıyı bölmek için `böl()` kullanılır.

### Örnek Kod Bloğu
```js
const Discord = require("discord.js")
const client = new Discord.Client()
const { prefix } = require("./ayarlar.json")
const hesapMakinesi = require("eay-hesapmakinesi")

client.on("message", message => {
  if (!message.guild || message.author.bot) return;
  
  const args = message.content.slice(prefix.length).trim().split(/ +/g);
  const command = args.shift().toLowerCase();
  
  if (command === "topla") {
    var sayi1 = args[0],
        sayi2 = args[1];
    if (!sayi1) return message.channel.send(`Lütfen toplanacak sayıları yaz.`);
    if (!sayi2) return message.channel.send(`Lütfen ${args[0]} ile toplanacak ikinci sayıyı yaz.`);
    message.channel.send(`${sayi1}+${sayi2} = ${hesapMakinesi.topla(sayi1, sayi2)}`)
  }
})

client.login(...)
```
