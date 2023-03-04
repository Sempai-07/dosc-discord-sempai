# InteractionReplyOption в библиотеке discord-sempai
Класс `InteractionReplyOption` в библиотеке `discord-sempai` предназначен для упрощения создания и отправки сообщений в ответ на взаимодействия (interaction) в `Discord`. Он содержит методы для установки содержимого сообщения, добавления вложений (embeds), компонентов и упоминаний (mentions), а также для изменения, удаления и отложенной отправки сообщений.

## Использование
Для использования класса `InteractionReplyOption` сначала необходимо создать экземпляр класса и передать ему объект с данными сообщения (content, embeds, allowedMentions, components, tts, flags, reference, ephemeral) в качестве аргумента конструктора. Если объект данных не был передан, то значения по умолчанию будут использоваться.

```javascript
Copy code
const { InteractionReplyOption } = require('discord-sempai');
const replyOption = new InteractionReplyOption({ content: 'Hello, world!' });
```
Далее можно использовать методы класса для установки нужных данных сообщения и отправки его в ответ на взаимодействие. Например, чтобы установить вложения (embeds) в сообщение:

```javascript
Copy code
const { MessageEmbed } = require('discord.js');

const embed = new MessageEmbed()
  .setTitle('My Title')
  .setDescription('My Description')
  .setColor('#0099ff');

replyOption.setEmbeds([embed]);
```
Чтобы отправить сообщение, необходимо вызвать метод send() на объекте Interaction:

```javascript
interaction.reply(replyOption);
```

## Методы
constructor(data)
Создает новый объект `InteractionReplyOption` с заданными данными сообщения (content, embeds, allowedMentions, components, tts, flags, reference, ephemeral).

### setContent(content)
Устанавливает содержимое сообщения.

### setEmbeds(embeds)
Устанавливает вложения (embeds) в сообщение.

### setAllowedMentions(allowedMentions)
Устанавливает упоминания (mentions) в сообщении.

### addComponents(components)
Добавляет компоненты в сообщение.

### setContentWithFormat(format, ...args)
Устанавливает содержимое сообщения с помощью форматирования строк.

### addEmbed(embed)
Добавляет одно вложение (embed) в сообщение.

### setComponents(components)
Устанавливает компоненты сообщения.

### setEmbed(embedIndex, embed)
Устанавливает вложение (embed) по указанному индексу.

### removeEmbed(embedIndex)
Удаляет вложение (embed) по указанному индексу.

### clearEmbeds()
Удаляет все вложения (embeds) из сообщения.

### setTTS(tts)
Устанавливает опцию TTS (text-to-speech) для сообщения.

### setFlags(flags)
Устанавливает флаги сообщения.

### setReference(message, failIfNotExists)
Устанавливает ссылку на сообщение (message) в качестве ответа на него.

### setReference(message, failIfNotExists)
Устанавливает ссылку на сообщение, которое было отправлено в ответ на запрос пользователя. Флаг `failIfNotExists` позволяет указать, следует ли выбрасывать ошибку, если сообщение не найдено.

### setEphemeral(ephemeral)
Устанавливает флаг видимости сообщения. Если установлен в `true`, сообщение будет видно только автору запроса.

### defer(ephemeral)
Задерживает ответ на запрос и возвращает `Promise`, который можно использовать для дальнейшей работы с сообщением.

### editOriginal(options)
Изменяет содержимое отправленного сообщения.

### deleteOriginal()
Удаляет отправленное сообщение.

### toJSON()
Возвращает объект с данными, которые будут отправлены в Discord API.