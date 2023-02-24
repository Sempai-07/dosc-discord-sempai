# Введение в парсеры
Парсеры в программировании относятся к инструментам, которые принимают входные данные в определенном формате и преобразуют их в структурированный объект. В контексте библиотеки `discord-sempai`, парсеры используются для создания и управления встроенными сообщениями Discord.

## Библиотека discord-sempai
`discord-sempai` - это библиотека для Discord.js, которая обеспечивает множество удобных функций для управления сообщениями, серверами и пользователями на Discord.

## Использование парсеров в discord-sempai
Парсеры в `discord-sempai` используются для создания эмбедов, которые являются структурированными сообщениями с различными элементами, такими как заголовки, описания, изображения и т.д.

В `discord-sempai` используется класс Parser для создания эмбедов. Давайте рассмотрим два примера, которые показывают, как использовать `Parser`:

```js
bot.command({
  name: 'parser_1',
  code: (client, message, args) => {
    const parser = new Parser({
      content: '{newEmbed:{author:hello author:https://cdn.discordapp.com/avatars/1033726409455181884/879bedd4f17a0bd95237e97f20d3ce9d.webp?size=4096}{thumbnail:https://cdn.discordapp.com/avatars/1033726409455181884/879bedd4f17a0bd95237e97f20d3ce9d.webp?size=4096}{image:https://cdn.discordapp.com/avatars/1033726409455181884/879bedd4f17a0bd95237e97f20d3ce9d.webp?size=4096}{color:#00ff00}{description:Hello description}{authorURL:https://cdn.discordapp.com/avatars/1033726409455181884/879bedd4f17a0bd95237e97f20d3ce9d.webp?size=4096}{timestamp:ms}{footer:Sempai:https://cdn.discordapp.com/avatars/1033726409455181884/879bedd4f17a0bd95237e97f20d3ce9d.webp?size=4096}}'
    });
    message.reply({embeds: [parser]});
  }
});

bot.command({
  name: 'parser_2',
  code: (client, message, args) => {
    const parser = new Parser({
      embeds: {
        author: {name: 'hello author', iconURL: 'https://cdn.discordapp.com/avatars/1033726409455181884/879bedd4f17a0bd95237e97f20d3ce9d.webp?size=4096'},
        thumbnail: 'https://cdn.discordapp.com/avatars/1033726409455181884/879bedd4f17a0bd95237e97f20d3ce9d.webp?size=4096',
        image: 'https://cdn.discordapp.com/avatars/1033726409455181884/879bedd4f17a0bd95237e97f20d3ce9d.webp?size=4096',
        color: '#00ff00',
        description: 'Hello description',
        authorURL: 'https://cdn.discordapp.com/avatars/1033726409455181884/879bedd4f17a0bd95237e97f20d3ce9d.webp?size=4096',
        timestamp: 'ms',
        footer: {text: 'Sempai', iconURL: 'https://cdn.discordapp.com/avatars/1033726409455181884/879bedd4f17a0bd95237e97f20d3ce9d.webp?size=4096'}
      }
    });
   message.reply({embeds: [parser]});
  }
});
```

В первом примере мы создаем объект парсера с помощью конструктора класса `Parser` и передаем ему строку с определенной структурой, которая задает различные свойства для эмбеда. Затем мы отправляем созданный эмбед в качестве ответа на сообщение пользователя.

Во втором примере мы создаем объект парсера, используя более привычный синтаксис объекта `JavaScript`. В этом случае мы передаем объект, содержащий свойства для эмбеда, в конструктор класса `Parser`. Затем мы также отправляем созданный эмбед в качестве ответа на сообщение пользователя.

Парсеры являются очень удобным инструментом для создания и управления структурированными сообщениями на Discord. Благодаря библиотеке `discord-sempai`, создание эмбедов становится еще проще и удобнее.


### Доступно

`{author:text:url?}` - автор эмбеда

`{authorURL:url}`- устанавливает гиперссылку для автора

`{title:text}`- заголовок

`{thumbnail:url}`- URL миниатюры изображения для встраивания

`{url:link}`- устанавливает гиперссылку для заголовка

`{footer:text:url?}` - нижний колонтитул

`{description:text}` - описание

`{color:hex} `- устанавливает цвет эмбеда

`{timestamp:ms}` - вставляет отметку времени

`{image:url}` - изображение

`{field:name:description:inline}` - добавляет поле с названием, описанием и указанием, должно ли поле отображаться в строку или в столбец.

Все эти параметры необходимо указывать в `{newEmbed:...}`. На данный момент в одном объекте класса Parser можно создать только один эмбед.