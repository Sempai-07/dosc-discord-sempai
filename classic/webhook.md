# Библиотеки Discord-Sempai: Webhook
Библиотека `discord-sempai` - это набор классов и методов для упрощения разработки ботов для `Discord`. Одним из таких классов является `Webhook`. этот класс позволяет отправлять сообщения на `Discord` через вебхуки.

Для использования класса `Webhook`, необходимо сначала установить библиотеку `discord-sempai` в ваш проект. Это можно сделать, выполнив команду `npm install discord.js` в командной строке вашего проекта.

После установки библиотеки `discord-sempai` вы можете использовать класс `Webhook` следующим образом:

```js
const { Webhook } = require('discord-sempai);

// Создаем новый объект Webhook
const webhook = new Webhook('URL_вашего_вебхука');

// Устанавливаем имя и аватар для вебхука (опционально)
webhook.setUsername('MyWebhook');
webhook.setAvatarURL('https://example.com/avatar.png');

// Создаем сообщение с текстом и/или вложениями
const message = {
  content: 'Привет, мир!',
  embeds: [
    {
      title: 'Заголовок вложения',
      description: 'Описание вложения',
      url: 'https://example.com',
      color: '#00ff00',
    },
  ],
  files: [
    'путь/к/файлу.png',
    'путь/к/другому/файлу.jpg',
  ],
};

// Отправляем сообщение через вебхук
webhook.send(message);
```

Вы также можете использовать опциональные параметры, чтобы установить имя и аватар для вебхука при отправке сообщения:

```js
// Отправляем сообщение с опциональными параметрами
webhook.send('Привет, мир!', {
  username: 'MyWebhook',
  avatarURL: 'https://example.com/avatar.png',
});
```
Кроме того, вы можете использовать метод `delete` для удаления вебхука:

```js
// Удаляем вебхук
webhook.delete();
```

Для использования функций `addEmbed`, `addEmbeds`, `addFile`, и `addFiles` в классе `Webhook`, вы можете создать экземпляр класса `Webhook` и затем вызвать одну из этих функций для добавления вложений или файлов к сообщению, которое будет отправлено через вебхук.

Например, чтобы добавить один встроенный объект (embed) к сообщению через вебхук, можно вызвать функцию `addEmbed` на экземпляре класса `Webhook`, передавая ей объект встроенного сообщения в качестве параметра:

```javascript
const { Webhook } = require('discord-sempai');

const webhookURL = 'https://discord.com/api/webhooks/123456789012345678/abcdefghijk';
const webhook = new Webhook(webhookURL);

const embed = {
  title: 'This is a title',
  description: 'This is a description',
  color: 0xff0000,
};

webhook.addEmbed(embed);
```
Аналогичным образом, чтобы добавить несколько объектов встроенных сообщений, можно вызвать функцию `addEmbeds`, передав ей массив встроенных объектов сообщений в качестве параметра:

```js
const { Webhook } = require('discord-sempai);

const webhookURL = 'https://discord.com/api/webhooks/123456789012345678/abcdefghijk';
const webhook = new Webhook(webhookURL);

const embeds = [
  {
    title: 'This is the first title',
    description: 'This is the first description',
    color: 0xff0000,
  },
  {
    title: 'This is the second title',
    description: 'This is the second description',
    color: 0x00ff00,
  },
];

webhook.addEmbeds(embeds);
```
Чтобы добавить один файл к сообщению через вебхук, можно вызвать функцию `addFile` на экземпляре класса `Webhook`, передав ей путь к файлу в качестве параметра:

```javascript
const { Webhook } = require('discord-sempai');

const webhookURL = 'https://discord.com/api/webhooks/123456789012345678/abcdefghijk';
const webhook = new Webhook(webhookURL);

const filePath = './image.png';

webhook.addFile(filePath);
```
Аналогичным образом, чтобы добавить несколько файлов, можно вызвать функцию `addFiles`, передав ей массив путей к файлам в качестве параметра:

```javascript
const { Webhook } = require('discord-sempai');

const webhookURL = 'https://discord.com/api/webhooks/123456789012345678/abcdefghijk';
const webhook = new Webhook(webhookURL);

const filePaths = ['./image1.png', './image2.png', './image3.png'];

webhook.addFiles(filePaths);
```

Затем можно вызвать функцию `send` на экземпляре класса `Webhook`, передав текст сообщения (если есть) и параметры (имя пользователя, `URL` аватара, встроенные сообщения и/или файлы), которые будут отправлены через вебхук:


```javascript
Copy code
const { Webhook } = require('./Webhook');

const webhookURL = 'https://discord.com/api/webhooks/123456789012345678/abcdefghijk';
const webhook = new Webhook(webhookURL);

const message = 'Hello, world!';
const embeds = [{
    title: 'This is a title',
    description: 'This is a description',
    color: 0xff0000,
}];

const files = ['./image.png'];

webhook.addEmbeds(embeds);
webhook.addFiles(files);

const username = 'Webhook Bot';
const avatarURL = 'https://example.com/avatar.png';

webhook.send(message, {
    username,
    avatarURL,
});
```

Обратите внимание, что параметры `username` и `avatarURL` не являются обязательными, и если они не указаны, то вебхук будет использовать имя пользователя и аватар по умолчанию. Кроме того, параметры `message`, `embeds` и `files` могут быть опущены, если вы не хотите отправлять сообщение или вложения. Например, если вы хотите отправить только файлы, то код может выглядеть так:

```javascript
const { Webhook } = require('discord-sempai');

const webhookURL = 'https://discord.com/api/webhooks/123456789012345678/abcdefghijk';
const webhook = new Webhook(webhookURL);

const files = ['./image1.png', './image2.png'];

webhook.addFiles(files);

webhook.send(webhook);
```