# ContextMenuManager в библиотеке discord-sempai
`ContextMenuManager` - это класс, который позволяет создавать контекстные меню для Discord ботов, используя библиотеку discord.js версии 14.

Импорт класса
```javascript
const { ContextMenuManager, GuildMember, ApplicationCommandType } = require('discord-sempai');
```
Создание экземпляра класса
```javascript
const myContextMenu = new ContextMenuManager(options);
```
`options` - это объект, который содержит следующие свойства:

- `type` - тип контекстного меню: 'USER' (для пользователей) или 'MESSAGE' (для сообщений).
- `name` - имя контекстного меню (строка).
- `isGlobal` - флаг, указывающий, является ли контекстное меню глобальным. По умолчанию `true`.
- `guildId` - идентификатор сервера (строка), на котором нужно зарегистрировать локальное контекстное меню. По умолчанию null.
- `handler` - функция-обработчик для контекстного меню.
Методы класса
setHandler(handler)
Метод для установки функции-обработчика для контекстного меню.

```javascript
myContextMenu.setHandler((interaction) => {
  // код для обработки контекстного меню
});
setGlobal(boolean)
```
Метод для установки флага, указывающего, является ли контекстное меню глобальным.

```javascript
myContextMenu.setGlobal(true);
```
Метод для установки идентификатора сервера, на котором нужно зарегистрировать локальное контекстное меню.

```javascript
myContextMenu.setGuild('1234567890');
```
Метод для установки описания контекстного меню.

```javascript
myContextMenu.setDescription('Меню для быстрого доступа к функциям бота');
register(bot)
```
Метод для регистрации контекстного меню на сервере.

```javascript
myContextMenu.register(bot);
```
`client` - это экземпляр Client, который используется для управления ботом.

### setPermission(permission)
Метод для установки прав доступа к контекстному меню.

```javascript
myContextMenu.setPermission([
  {
    id: '1234567890',
    type: 'USER',
    permission: true,
  },
  {
    id: '0987654321',
    type: 'ROLE',
    permission: false,
  },
]);
```
`permission` - это массив объектов, каждый из которых содержит следующие свойства:

`id` - идентификатор пользователя или роли (строка).
`type` - тип идентификатора: 'USER' или 'ROLE'.
`permission` - булевое значение

### update(client)
Функция `update` используется для обновления прав доступа к контекстному меню. Она получает `client` - объект клиента `Discord.js` и обходит все серверы, на которых зарегистрировано контекстное меню. Для каждого сервера она получает все команды и находит нужную команду по имени и типу (USER или MESSAGE). Если команда найдена, то ей устанавливаются новые права доступа (`permissions`).

### getUserFromInteraction(interaction)
Метод `getUserFromInteraction` используется для получения пользователя из объекта `interaction`. Он принимает `interaction` - объект взаимодействия с контекстным меню и возвращает объект `targetUser` - пользователя, на которого было сделано контекстное меню.

### getMessageFromInteraction(interaction)
Метод `getMessageFromInteraction` используется для получения `ID` сообщения из объекта `interaction`. Он принимает `interaction` - объект взаимодействия с контекстным меню и возвращает `ID` `targetId` - сообщения, для которого было сделано контекстное меню.

### checkPermissions(member, permissions)
Метод `checkPermissions` используется для проверки разрешений на выполнение команды для участника сервера. Он принимает `member` - объект участника сервера и `permissions` - права доступа, необходимые для выполнения команды. Если `member` не является объектом `GuildMember`, то метод возвращает `false`. В противном случае метод проверяет, есть ли у участника все необходимые права доступа. Если некоторые права отсутствуют, метод возвращает строку со списком недостающих прав доступа. В противном случае метод возвращает `true`.

## Пример
### Вариант 1
```javascript
const { ApplicationCommandType, ContextMenuManager } = require('discord-sempai');

const manager = new ContextMenuManager({
  type: ApplicationCommandType.User,
  name: 'Приветствие',
});

manager.setHandler((interaction) => {
  const user = ContextMenuManager.getUserFromInteraction(interaction);
  if (user) {
    const message = `Привет, ${user.username}! Добро пожаловать на сервер.`;
    interaction.reply(message);
  }
});

bot.on('ready', () => {
   manager.register(bot);
})
```

### Вариант 2
```javascript
bot.createInteraction({
  name: 'hello',
  type: ApplicationCommandType.User,
  prototype: 'contextmenu',
  code: (client, interaction) => {
    interaction.reply("Hello")
  }
})
```