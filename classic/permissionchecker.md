# PermissionChecker в библиотеке discord-sempai
Класс `PermissionChecker` представляет собой инструмент для проверки прав доступа для объектов в `Discord API`, таких как каналы, гильдии, роли и боты.

## Конструктор
```js
constructor(entity)
```
`entity` - объект, для которого будут проверяться права доступа.

## Методы
### has(permission)
Проверяет, имеет ли объект entity заданное разрешение.

- `permission` - разрешение, которое нужно проверить.


### hasAny(permissions)
Проверяет, имеет ли объект entity хотя бы одно из заданных разрешений.

- `permissions` - массив разрешений, которые нужно проверить.


### hasAll(permissions)
Проверяет, имеет ли объект `entity` все заданные разрешения.

- `permissions` - массив разрешений, которые нужно проверить.

### isAdmin()
Проверяет, является ли объект `entity` администратором.

### canManageChannel(channel)
Проверяет, имеет ли объект `entity` разрешение на управление заданным каналом.

- `channel` - канал, для которого нужно проверить разрешение.

### canManageGuild(guild)
Проверяет, имеет ли объект `entity` разрешение на управление заданной гильдией.

`guild` - гильдия, для которой нужно проверить разрешение.

### hasRole(role)
Проверяет, имеет ли объект `entity` заданную роль.

- `role` - роль или ID роли, которую нужно проверить.

### hasBot(bot)
Проверяет, находится ли объект `bot` в списке пользователей клиента бота.

- `bot` - бот или ID бота, которого нужно проверить.