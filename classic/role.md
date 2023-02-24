# Библиотека Discord-Sempai: Role
Библиотека `discord-sempai` предоставляет множество инструментов для работы с ботами на платформе `Discord`. Одним из таких инструментов является класс `Role`, который предоставляет функции для управления ролями на сервере `Discord`.

## Основные функции
### getRoleInfo(guild, roleId, option)
Получает информацию о роли на сервере `Discord`. Принимает параметры:

- `guild` - сервер Discord, на котором находится роль
- `roleId` - идентификатор роли
- `option` - опция, информацию о которой нужно получить (например, "name", "color", "permissions" и т.д.)

### createRole(guild, options)
Создает новую роль на сервере `Discord`. Принимает параметры:

- `guild` - сервер Discord, на котором нужно создать роль
- `options` - объект с параметрами создаваемой роли (например, "name", "color", "permissions" и т.д.)

### deleteRole(role)
Удаляет роль с сервера `Discord`. Принимает параметры:

- `role` - роль, которую нужно удалить

### updateRole(role, options)
Обновляет информацию о роли на сервере `Discord`. Принимает параметры:

- `role` - роль, которую нужно обновить
options - объект с параметрами, которые нужно обновить (например, "name", "color", "permissions" и т.д.)

### addRole(guild, user, roleId)
Добавляет роль пользователю на сервере `Discord`. Принимает параметры:

- `guild` - сервер Discord, на котором нужно добавить роль пользователю
- `user` - пользователь, которому нужно добавить роль
- `roleId` - идентификатор роли, которую нужно добавить пользователю

### removeRole(guild, user, roleId)
Удаляет роль у пользователя на сервере `Discord`. Принимает параметры:

- `guild` - сервер `Discord`, на котором нужно удалить роль пользователя
- `user` - пользователь, у которого нужно удалить роль
- `roleId` - идентификатор роли, которую нужно удалить у пользователя

### Пример использования
```js
// Пример будет показан на discord.js, а не на discord-sempai 
const { Client } = require('discord.js');
const client = new Client();
const Role = require('discord-sempai').Role;

client.on('ready', () => {
  console.log(`Logged in as ${client.user.tag}!`);
});

client.on('createMessage', async message => {
  if (message.content.startsWith('!addrole')) {
    const roleId = '1234567890'; // id роли, которую нужно добавить пользователю
    const user = message.member;
    const guild = message.guild;

    const Role = new Role();
    const success = await Role.addRole(guild, user, roleId);

    if (success) {
      message.reply(`Роль успешно добавлена!`);
    } else {
      message.reply(Не удалось добавить роль. Проверьте правильность указанного идентификатора роли.);
    }
  }
});
```

```js
// Создать новую роль
const newRole = await Roles.createRole(guild, {
  name: 'New Role',
  color: 'BLUE',
  permissions: ['MANAGE_ROLES']
});

// Обновить роль
await Roles.updateRole(role, {
  name: 'Updated Role',
  color: 'RED'
});

// Удалить роль
await Roles.deleteRole(role);

// Добавьте роль пользователю
await addRole(guiild, user, roleId)

// Забрать роль у пользователя
await removeRole(guild, user, roleId)
```

В данном примере мы создали объект класса `Role`, вызвали функцию `addRole` для добавления роли пользователю на сервере `Discord` и вывели сообщение в чат об успешном или неудачном выполнении операции.

## Заключение
Библиотека `discord-sempai` предоставляет удобный и простой в использовании инструментарий для работы с ботами на платформе `Discord`. Класс `Role` является частью этого инструментария и предоставляет функционал для управления ролями на сервере `Discord`.