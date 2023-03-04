# Events в Discord.js и их использование в библиотеке discord-sempai

В библиотеке `discord.js`, события (events) являются основой для многих действий, которые происходят в вашем Discord-боте. События могут быть что угодно, от сообщений в чате до изменений состояния голосовых каналов. Они представляют собой просто JavaScript-функции, которые вызываются, когда происходит определенное действие.

## Список событий
Вот некоторые из наиболее распространенных событий, которые вы можете использовать в своей библиотеке `discord-sempai`:

- `createMessage`: вызывается, когда в канале появляется новое сообщение
- ready: вызывается, когда ваш бот готов к использованию
- `guildMemberAdd`: вызывается, когда новый пользователь присоединяется к серверу
- `guildMemberRemove`: вызывается, когда пользователь покидает сервер
- `voiceStateUpdate`: вызывается, когда состояние голосового канала изменяется
Полный список событий можно найти в документации <a href="https://discord.js.org/#/docs/discord.js/main/class/Client?scrollTo=e-applicationCommandPermissionsUpdate">discord.js</a>.

## Использование событий в discord-sempai
В библиотеке `discord-sempai`, вы можете использовать события для обработки действий, происходящих в вашем боте. Для этого нужно зарегистрировать функцию-обработчик для каждого события, которое вы хотите обрабатывать.

Вариант 1:
```js
const { Bot } = require('discord-sempai');
const bot = new Bot({
    prefix: ["?"]
});

// обработчик события ready
bot.on('ready', () => {
  console.log(`Logged in as ${client.user.tag}!`);
});

// обработчик события message
bot.on('createMessage', message => {
  if (message.content === 'ping') {
    message.reply('Pong!');
  }
});

bot.connect('DISCORD_BOT_TOKEN');
```

Вариант 2:
```js
const { Bot } = require('discord-sempai');
const bot = new Bot({
    prefix: ["?"]
});

// обработчик события ready
bot.createEvent({
  name: 'ready',
  code: (client) => {
   console.log(`Logged in as ${client.user.tag}!`);
  }
});

// обработчик события message
bot.createEvent({
  name: 'createMessage',
  code: (client, message) => {
  if (message.content === 'ping') {
    message.reply('Pong!');
   }
  }
});

bot.connect('DISCORD_BOT_TOKEN');
```

В этом примере мы зарегистрировали две функции-обработчика событий: одну для события `ready` и другую для события message. При запуске бота, функция-обработчик для события ready вызовется один раз, а функция-обработчик для события message будет вызываться каждый раз, когда пользователь отправляет сообщение с содержанием "ping".

## Заключение
События - это важная часть `discord.js` и могут быть мощным инструментом для создания вашего `discord-бота`. В библиотеке `discord-sempai` вы можете использовать события для обработки различных действий, происходящих в вашем боте. Надеемся, что эта статья помогла вам лучше понять, что такое события 