# Библиотека discord-Sempai: Invite
Библиотека `discord-sempai` предоставляет различные инструменты для создания и управления ботами на платформе `discord`. Один из таких инструментов - это класс `Invite`, который предоставляет функции для работы с инвайтами на сервере `discord`.

## Основные функции
### getInviteInfo
Функция `getInviteInfo` используется для получения информации о конкретном инвайте на сервере `discord`. Принимает следующие параметры:

- `client` - объект `Client` из `discord.js`
- `code` - код инвайта
- `option` - опция, информацию о которой нужно получить (например, "code", "inviter", "channel" и т.д.)

Возвращает значение опции.

### getInviteLink
Функция `getInviteLink` используется для создания нового инвайта на сервере `discord`. Принимает следующие параметры:

- `guildId` - идентификатор сервера `discord`
- `options` - объект с параметрами создаваемого инвайта (например, "maxAge", "maxUses", "temporary" и т.д.)

Возвращает новый инвайт.

### getInviteList
Функция `getInviteList` используется для получения списка всех инвайтов на сервере `discord`. Принимает следующие параметры:

- `client` - объект Client из `discord.js`
- `guildId` - идентификатор сервера `discord`

Возвращает список всех инвайтов на сервере.

### deleteInvite
Функция `deleteInvite` используется для удаления конкретного инвайта на сервере `discord`. Принимает следующие параметры:

- `client` - объект `Client` из `discord.js`
- `code` - код инвайта, который нужно удалить


### hasInvite
Функция `hasInvite` используется для проверки, существования инвайта на сервере `discord`. Принимает следующие параметры:


- `guildId` - идентификатор сервера `discord`
- `code` - код инвайта, который нужно проверить

Возвращает `true` или же `false`

## Пример использования
```js
const { Client } = require('discord.js');
const client = new Client();
const invites = require('discord-sempai').Invite;

client.on('ready', () => {
  console.log(`Logged in as ${client.user.tag}!`);
});

client.on('message', async message => {
  if (message.content.startsWith('!createinvite')) {
    const guildId = message.guild.id;
    const options = {
      maxAge: 86400,
      maxUses: 1,
      unique: true,
      reason: 'Inviting a friend'
    };

    const invite = await invites.getInviteLink(guildId, options);

    message.channel.send(`New invite link created: ${invite.url}`);
  } else if (message.content.startsWith('!deleteinvite')) {
    const code = 'ABCDEF'; // инвайт-код, который нужно удалить

    const invites = new Invites();
    await invites.deleteInvite(client, code);

    message.channel.send(`Invite with code ${code} has been deleted.`);
  }
});
```

В этом примере мы создаем новый инвайт на сервере `discord` с использованием функции `getInviteLink` и удаляем конкретный инвайт с использованием функции `deleteInvite`.