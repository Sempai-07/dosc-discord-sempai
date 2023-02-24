# Введение в текстовые команды (Text Commands)
Text Commands, или текстовые команды, это метод для добавления взаимодействия с пользователями в вашем приложении или библиотеке, который позволяет им взаимодействовать с вашим приложением, используя текстовые сообщения.

В библиотеке discord-sempai (discord.js), текстовые команды могут быть использованы для обработки сообщений, которые пользователи отправляют в текстовые каналы. Это позволяет разработчикам создавать интерактивные боты, которые могут отвечать на запросы пользователей и выполнять различные задачи.

## Как использовать текстовые команды в discord-sempai

Чтобы использовать текстовые команды в библиотеке `discord-sempai`, необходимо создать экземпляр клиента Discord и зарегистрировать обработчик событий `createMessage`. Затем вы можете проверять сообщения, которые получает ваш бот, и реагировать на них соответствующим образом.

Пример:

```
const { Bot } = require('discord.js');
const bot = new Bot({
    prefix: ["?", "!"]
});

bot.createEvent({
  name: 'ready',
  once: false,
  code: (client) => {
   console.log(`Бот запущен ${client.user.tag}!`);
  }
});

bot.createEvent({
  name: 'createMessage',
  once: false,
  code: (message) => {
  // Проверяем, что сообщение начинается с символа "!" и что его автор не бот
  if (!message.content.startsWith('!') || message.author.bot) return;

  // Обрабатываем текстовую команду
  const args = message.content.slice(1).trim().split(/ +/);
  const command = args.shift().toLowerCase();
  
  if (command === 'ping') {
    message.reply('Pong!');
  } else if (command === 'hello') {
    message.channel.send(`Hello, ${message.author}!`);
    }
   }
});

// Или же можно использовать
bot.command({
   name: 'ping',
   code: (client, message, args) => {
       message.reply("Pong!")
   }
})

client.login('DISCORD_BOT_TOKEN');
```

В этом примере мы регистрируем обработчик события message, который будет вызываться каждый раз, когда ваш бот получает сообщение. Мы проверяем, что сообщение начинается с символа "!", чтобы определить, является ли оно текстовой командой. Затем мы извлекаем имя команды и аргументы из сообщения и выполняем соответствующие действия.

## Заключение
Текстовые команды - это удобный способ добавления взаимодействия с пользователями в ваше приложение или библиотеку. В библиотеке `discord-sempai` вы можете использовать текстовые команды для создания интерактивных ботов, которые могут отвечать на запросы пользователей и выполнять различные задачи.