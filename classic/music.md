# Music
Музыкальные функции Discord позволяют ботам играть музыку в голосовых каналах. Для этого вам нужно использовать библиотеку для работы с музыкой, такую как `discord-music-players`, то есть встроенный модуль `Music`

## Установка
Перед использованием музыкальных функций в `discord-sempai`, убедитесь, что вы установили `discord-music-players` и `Node.js` на ваш компьютер. Вы можете скачать `Node.js` с официального сайта: https://nodejs.org/

После установки `Node.js` выполните команду для установки `discord-music-players`:

```sh
npm install discord-music-players
npm install @discordjs/opus
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


bot.command({
   name: 'play',
   code: (client, message, args) => {
   const queueLength = client.music.queueLength(message.guild.id);
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

bot.connect('DISCORD_BOT_TOKEN');
```

## Дополнительные функции
```js
await music.playSong({
        queue: queue,
        songName: args.join(" "),
        voiceChannelId: message.member.voice.channel,
        requestedBy: message.author.tag,
        guildId: message.guild.id
      })
// Добавляет песню в очередь

music.joinVC(guildId, channelId)
// Присоединиться к голосовому каналу

music.leaveVC(guildId)
// Покинуть голосовой канал

music.queueSongs(guildId)
// Очередь

music.loopMusic(type, guildId)
// type - 'OFF' | 'QUEUE' | 'SONG'
// Зацикливать очередь/песню

music.progressBar(guildId, arrow, block, size)
// Выдает прогресс бар

music.skipSong(guildId)
// Пропускает песню

music.stopQueue(guildId)
// Останавливает очередь

music.setVolume(guildId, volume) 
// Устанавливает громкость музыки

music.clearQueue(guildId) 
// Очищает очередь

music.shuffleQueue(guildId)
// Перемешивает очередь

music.pauseQueue(guildId) 
// Останавливаеь очередь

music.resumeQueue(guildId) 
// Возобновляет очередь
```

Это пример кода, который добавляет музыкальную функциональность в ваш `discord-sempai` бот, используя `discord-music-players` и `Node.js`. Он позволяет играть музыку из ссылок на видео, полученных в сообщениях и добавлять их в очередь в текущем голосовом канале. Вы можете настроить этот пример кода для вашего бота и изменить его, чтобы удовлетворить свои потребности.