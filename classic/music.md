# Music
Музыкальные функции Discord позволяют ботам играть музыку в голосовых каналах. Для этого вам нужно использовать библиотеку для работы с музыкой, такую как `discord-music-players`, то есть встроенный модуль `Music`

## Установка
Перед использованием музыкальных функций в `discord-sempai`, убедитесь, что вы установили `discord-music-players` и `Node.js` на ваш компьютер. Вы можете скачать `Node.js` с официального сайта: https://nodejs.org/

После установки `Node.js` выполните команду для установки `discord-music-players`:

```sh
npm install discord-music-players
npm install @discordjs/opus
npm install isomorphic-unfetch
```

## Использование
Чтобы использовать музыкальные функции в discord-sempai, сначала вам нужно импортировать класс Music из `discord-sempai` в свой код:

```js
const { Bot, Music } = require('discord-sempai');

const bot = new Bot({
  prefix: ["!"]
});

bot.createEvent({
  name: 'ready',
  once: false,
  code: (client) => {
   console.log(`Бот запущен ${client.user.tag}!`);
  }
});

bot.music = new Music(bot, {
  defeanOnJoin: true,
  leaveOnEnd: true,
  leaveOnEmpty: false
})

bot.music.on('songAdd', (queue, song) => {
  queue.data.queueInitMessage.channel.send(`**${song}** был добавлен в очередь.`);
})

bot.music.on('queueEnd', (queue) => {
  queue.data.queueInitMessage.channel.send(`Очередь закончилась, играть не во что.`);
})

bot.music.on('queueDestroyed', (queue) => {
  queue.data.queueInitMessage.channel.send(`Воспроизведение закончилось.`);
})

bot.connect('DISCORD_BOT_TOKEN');
```

## Функции

`playTrack(options)` - проигрывает указанный трек на сервере, добавляя его в очередь. Функция принимает параметры, такие как идентификатор голосового канала, имя трека и т. д.

```js
bot.command({
   name: 'play',
   code: (client, message, args) => {
   
   const queueLength =    client.music.queueLength(message.guild.id);
   
   if (!message.member.voice.channel) {
   return message.reply('Вы не находитесь в голосовом канале');
   }
   
   if (!args[0]) {
   return message.reply('Введите название песни или ссылку');
   }
   
   let queue = client.music.createQueue(message.guild.id, {
   data: {
   queueInitMessage: message
   }
  });
  
  const songInfo = await client.music.playSong({
   queue: queue,
   songName: args.join(" "),
   voiceChannelId: message.member.voice.channel,
   requestedBy: message.author.tag,
   guildId: message.guild.id,
   message: message
  });
  
  const songEmbed = new MessageEmbed()
      .setTitle(queueLength === 0 ? 'Музыка запущена' : 'Музыка добавлена')
      .addFields(
        { name: 'Название:', value: songInfo.name, inline: true },
        { name: 'Автор:', value: songInfo.author, inline: true },
        { name: 'Длина:', value: songInfo.duration, inline: true }
      )
      .setColor('#303136')
    
    message.channel.send({ embeds: [songEmbed] });
   }
})
```

`queueSongs(guildId, messageFormat = "{position}: Автор: {author} - {name}, добавил: {useradd}", numSongs = 10)`` - возвращает список из указанного количества песен из очереди.

```js
const music = client.music.queueSongs(message.guild.id, "{position}: Автор: {author} - {name}, добавил: {useradd}");

let messageText = "Список песен в очереди:\n";
messageText += music.join('\n');
message.reply(messsageText)
```

`{author}` - автор
`{name}` - название песни
`{useradd}` - тот кто добавил трек
`{position}` - позиция песни
`{url}` - сыллка на песню 
`{thumbnail}` - изображение 
`{duration}` - время
`{first}` - песня стоит на первой позиции?
`{live}` - песня в прямом эфире?
`{seektime}` - час поиска песни

`loopMusic(guildId, types)` - изменяет режим повтора треков. Принимает один из следующих параметров: `off` / `0` (повтор выключен), `song` / `track` / `1` (повтор текущего трека), `queue` / `2` (повтор всей очереди

```js
const loop = client.music.loopMusic(message.guild.id, 'song')
if (!loop) {
  message.reply('Произошла ошибка')
}
```

`progressBar(guildId, arrow, block, size)` - возвращает строку состояния проигрывания в виде прогресс-бара, отображающего текущую позицию в треке. Параметры `arrow`, `block` и `size` могут быть изменены.

`skipTrack(guildId, numberSkip)` - пропускает указанное количество треков в очереди (по умолчанию одну).

`stopQueue(guildId)` - останавливает воспроизведение музыки и очищает очередь.

`setVolume(guildId, volume)` - устанавливает громкость проигрывания для указанного сервера.

`clearQueue(guildId)` - удаляет все треки из очереди на указанном сервере.

`shuffleQueue(guildId)` - перемешивает очередь на указанном сервере.

`pauseQueue(guildId)` - приостанавливает воспроизведение музыки на указанном сервере.

`resumeQueue(guildId)` - возобновляет воспроизведение музыки на указанном сервере.

`joinVC(guildId, channelId)` - подключается к голосовому каналу на указанном сервере.

`leaveVC(guildId)` - отключается от голосового канала на указанном сервере.

`gueueLength(guildId)` - возвращает количество треков в очереди на указанном сервере.

`getCurrentVolume(guildId)` - возвращает текущую громкость для указанного сервера.

`getLoopType(guildId)` - возвращает тип режима повтора для указанного сервера: `off`, `song` или `queue`.

`isQueueLooping(guildId, type = 'all')` -  Функция проверяет, повторяется ли текущая музыкальная очередь в заданном сервере (guildId). Параметр `type` определяет тип повторения: 'all' - повторять все треки в очереди, 'track / song / 1' - повторять текущий трек, 'queue / 2' - повторять всю очередь. Возвращает `true`, если музыкальная очередь повторяется, и `false` в противном случае.

`isTrackLooping(guildId)` - Функция проверяет, повторяется ли текущий трек в заданном сервере (guildId). Возвращает `true`, если трек повторяется, и `false` в противном случае.

`isTrackPaused(guildId)` - Функция проверяет, приостановлен ли текущий трек в заданном сервере (guildId). Возвращает `true`, если трек приостановлен, и `false` в противном случае.

`isMusicPlaying(guildId)` - Функция проверяет, играет ли в данный момент музыка на заданном сервере (guildId). Возвращает `true`, если музыка играет, и `false` в противном случае. Если сервер не найден или произошла ошибка, функция вернет `false`.

Если в функиях произошла ошибка они вернут `undefined` / `null`