# Введение в команды типа "slash" в Discord
Discord имеет два типа команд: текстовые команды и команды типа "slash". Текстовые команды работают посредством сообщений, в которых пользователь отправляет текстовую команду и бот отвечает текстом. Команды типа "slash" работают с помощью интерфейса команд, встроенного в клиент Discord.

Команды типа "slash" являются относительно новым типом команд, введенным Discord в 2020 году. Они представляют собой нативные команды, которые могут быть вызваны через специальный интерфейс команд. Команды типа "slash" позволяют пользователям быстро и легко вызывать команды без необходимости запоминания текстовых команд и ключевых слов.

## Использование команд типа "slash" в Discord с помощью discord-sempai
discord-sempai - это библиотека для Node.js, которая упрощает написание ботов для Discord, используя Discord.js. Библиотека предоставляет ряд методов для создания и обработки команд типа "slash".

Вот пример, который демонстрирует, как использовать команды типа "slash" в discord-sempai:

```js
const { Bot } = require('discord-sempai');

const bot = new Bot();

bot.createEvent({
  name: 'ready',
  once: false,
  code: (client) => {
  console.log('Бот запущен');
});

bot.createEvent({
  name: 'interactionCreate',
  once: false,
  code: async (client, interaction) => {
  if (!interaction.isCommand()) return;
  if (interaction.commandName === 'ping') {
    await interaction.reply('Pong!');
  }
});

client.connect('DISCORD_BOT_TOKEN');
```

В этом примере мы создаем экземпляр клиента `discord-sempai` и затем создаем обработчик события "interactionCreate". Метод `isCommand()` используется для определения, является ли взаимодействие командой типа "slash". Если это так, мы можем обработать команду, используя `interaction.commandName` и ответить пользователю с помощью метода `interaction.reply()`. Также есть ещё один вариант создания слэш команд

```js
const { Bot } = require('discord-sempai');

const bot = new Bot();

bot.createEvent({
  name: 'ready',
  once: false,
  code: (client) => {
  console.log('Бот запущен');
});

bot.slashCommand({
   name: 'ping',
   description: 'Задержка бота',
   code: (client, interaction ) => {
      interaction.reply('Пинг ' + client.ws.ping)
   }
})

client.connect('DISCORD_BOT_TOKEN');
```

Команды типа "slash" обеспечивают более прямую и интуитивно понятную пользовательскую опыт, чем текстовые команды, и могут улучшить взаимодействие пользователей с вашим ботом Discord.