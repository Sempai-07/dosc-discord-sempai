# Использование загрузчика в библиотеке Discord-Sempai

## Введение
`Discord-Sempai` - это библиотека для `discord.js`, которая облегчает создание и управление ботами Discord. В этом файле мы рассмотрим использование загрузчиков в библиотеке Discord-Sempai.

## Что такое загрузчик?
Загрузчик - это набор функций в `discord-sempai`, которые позволяют создавать и обрабатывать события команд (slash-команд, textCmd, events) в Discord.

`Slash-команды` - это новый тип команд в Discord, который позволяет пользователям выполнять действия, нажимая на кнопки в интерфейсе пользователя. Команды, созданные с помощью загрузчика, могут быть легко обработаны вашим ботом, и пользователи могут легко взаимодействовать с вашим ботом.

## Как использовать загрузчик?
Для использования загрузчика в `discord-sempai` вам нужно выполнить следующие шаги:

- Установите `библиотеку discord-sempai`: npm install discord-sempai.
- Подключите `discord-sempai` в свой проект:

```javascript
const { Bot } = require('discord-sempai');
const bot = new Bot({
    prefix: ["?"]
});

bot.loaderTextCmd("./cmd/")
// Загрузчик текстовых команд
bot.loaderSlashCmd("./slash/")
// Загрузчик слэш команд
bot.loaderComponent("./component/")
// Загрузчик кнопок, модального окна, селектор меню
bot.loaderEvent("./events/")
// Загрузчик событие

bot.connect('DISCORD_BOT_TOKEN');
```

##### Slash => ./slash/info/ping.js
```javascript
const { MessageEmbed } = require('discord-sempai');
module.exports = {
    name: "command",
    description: "Привет мир!",
    code(client, interaction) {
        const test = new MessageEmbed()
        .setTitle('Мир')
        .setDescription(`Hello 👋`)
        .setTimestamp()
        .setColor('#00ccff')
        .setFooter({text: interactdis.author.tag});
        return interaction.reply({embeds: [test]});
    }
};
```

##### TextCmd => ./cmd/info/ping.js
```javascript
const { MessageEmbed } = require('discord-sempai');
module.exports = {
    name: "command",
    code(client, message, args) {
        const test = new MessageEmbed()
        .setTitle('Мир')
        .setDescription(`Hello 👋`)
        .setTimestamp()
        .setColor('#00ccff')
        .setFooter({text: message.author.tag});
        return message.reply({embeds: [test]});
    }
};
```

##### Events => ./events/info/messageCreate.js
```javascript
module.exports = {
  name: 'messageCreate',
  once: false,
  code: async(client, message) => {
    message.reply(`У ${client.user.tag   + client.ws.ping}  пинга`)
  }
}
```

##### Component => ./components/info/select_test.js
```javascript
const { MessageEmbed } = require('discord-sempai');
module.exports = {
    id: 'select_test',
    prototype: 'select', // button/select/modal/contextmenu
    code: (client, interaction, args) => {
        const info = new MessageEmbed()
        .setTitle('Информация')
        .setDescription('Привет 💩😈')
        .setFooter({text: interaction.user.tag})
        .setTimestamp();
        return interaction.reply({embeds: [info]});
    }
};
```

## Заключение
`Загрузчик` - это мощный инструмент для создания и обработки slash-команд, текстовых команд и событий в Discord. Библиотека `discord-sempai` облегчает создание и управление ботами Discord, используя эти функции. Надеемся, что эта статья помогла вам начать использовать `загрузчик` в вашем проекте 