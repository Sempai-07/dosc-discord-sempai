# GuildInvite в библиотеке discord-sempai
Класс `GuildInvite` предназначен для работы с инвайтами на сервере `Discord` при использовании библиотеки `discord.js`. Он предоставляет несколько методов для работы с инвайтами:

## Основные методы
### getInviteInfo
Метод `getInviteInfo` используется для получения информации о конкретном инвайте на сервере `Discord`. Он принимает следующие параметры:

- `client` - объект `Client` из `discord.js`
- `code` - код инвайта
- `option` - опция, информацию о которой нужно получить (например, "code", "inviter", "channel" и т.д.)
Метод возвращает значение опции.

### getInviteLink
Метод `getInviteLink` используется для создания нового инвайта на сервере `Discord`. Он принимает следующие параметры:

- `client` - объект Client из discord.js
- `guildId` - идентификатор сервера Discord
- `channelId` - идентификатор канала, в котором будет создан инвайт
- `options` - объект с параметрами создаваемого инвайта (например, "maxAge", "maxUses", "temporary" и т.д.)
Метод возвращает новый инвайт.

### getInviteList
Метод `getInviteList` используется для получения списка всех инвайтов на сервере `Discord`. Он принимает следующие параметры:

- `client` - объект `Client` из - `discord.js`
`guildId` - идентификатор сервера Discord
Метод возвращает список всех инвайтов на сервере.

### deleteInvite
Метод `deleteInvite` используется для удаления конкретного инвайта на сервере `Discord`. Он принимает следующие параметры:

`client` - объект `Client` из `discord.js`
`code` - код инвайта, который нужно удалить

## Дополнительные методы
### hasInvite
Метод `hasInvite` используется для проверки существования инвайта на сервере `Discord`. Он принимает следующие параметры:

- `guild` - объект `Guild` из `discord.js`
- `code` - код инвайта, который нужно проверить
Метод возвращает `true`, если инвайт существует на сервере, и `false` в противном случае.

## Пример
```javascript
client.on('creteMessage', async message => {
  if (message.content.startsWith('!deleteinvite')) {
    const code = message.content.split(' ')[1];
    await GuildInvite.deleteInvite(client, code);
    message.channel.send(`Invite ${code} has been deleted.`);
  }
});

client.on('createMessage', async message => {
  if (message.content.startsWith('!invitelist')) {
    const guildId = message.guild.id;
    const invites = await GuildInvite.getInviteList(client, guildId);

    const inviteList = invites.map((invite) => {
      return `${invite.code}: ${invite.url}`;
    }).join('\n');

    message.channel.send(`Invite list:\n${inviteList}`);
  }
});


client.on('createMessage', async message => {
  if (message.content.startsWith('!invitelist')) {
    const guildId = message.guild.id;
    const invites = await GuildInvite.getInviteList(client, guildId);

    const inviteList = invites.map((invite) => {
      return `${invite.code}: ${invite.url}`;
    }).join('\n');

    message.channel.send(`Invite list:\n${inviteList}`);
  }
});

```