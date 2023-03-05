# GuildEmoji в библиотеке discord-sempai

Класс `GuildEmoji` в библиотеке `discord-sempai` предназначен для облегчения доступа к информации о серверных эмодзи `Discord`. Он содержит методы для получения различных свойств эмодзи, таких как его `ID`, дату создания, автора, сервер, на котором он находится, и т.д. Также в этом классе есть методы для проверки доступности эмодзи на сервере или для пользователя, для получения количества реакций и пользователей, которые поставили реакцию на эмодзи, а также для получения строкового представления эмодзи.

Для использования, вы должны импортировать его из библиотеки, используя ключевое слово `require`:

```javascript
const { GuildEmoji } = require('discord-sempai');
```
Затем вы можете создать экземпляр класса, передавая объект `emoji`, полученный из `discord.js`:

```javascript
const emoji = new GuildEmoji(message.guild.emojis.cache.first());
```
Теперь вы можете использовать методы класса для получения нужной информации об эмодзи:

```javascript
console.log(`ID: ${emoji.getId()}`);
console.log(`Создан: ${emoji.getCreatedAt()}`);
console.log(`Автор: ${emoji.getAuthorUsername()} (${emoji.getAuthorLink()})`);
console.log(`Сервер: ${emoji.getServerName()} (${emoji.getServerLink()})`);
console.log(`Доступен ролям: ${emoji.getRoles().join(', ')}`);
console.log(`Доступен пользователям: ${emoji.getUsers().join(', ')}`);
console.log(`Анимированный: ${emoji.isAnimated()}`);
console.log(`Доступен на сервере ${guildId}: ${emoji.isAvailableInGuild(guildId)}`);
console.log(`Доступен пользователю ${userId}: ${emoji.isAvailableForUser(userId)}`);
console.log(`Количество реакций: ${emoji.getReactionCount()}`);
console.log(`Пользователи, поставившие реакцию: ${emoji.getReactionUsers().join(', ')}`);
console.log(`Количество уникальных пользователей, поставивших реакцию: ${emoji.getReactionUserCount()}`);
console.log(`Строковое представление: ${emoji.toString()}`);
```