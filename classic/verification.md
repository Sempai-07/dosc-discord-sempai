# Verification в библиотеке discord-sempai

Класс `Verification` содержит методы для проверки различных условий в `Discord.js v14` Эти методы могут быть использованы для проверки различных параметров пользователей, сообщений, каналов и ролей.

## Методы
### isNumber
```javascript
Verification.isNumber(str)
```
Проверяет, является ли переданная строка str числом.

### isPositiveNumber
``` javascript
Verification.isPositiveNumber(str)
```
Проверяет, является ли переданная строка str положительным числом.

### isNegativeNumber
```javascript
Verification.isNegativeNumber(str)
```
Проверяет, является ли переданная строка str отрицательным числом.

### isDecimalNumber
```javascript
Verification.isDecimalNumber(str)
```
Проверяет, является ли переданная строка str десятичным числом.

### isAdministrator
```javascript
Verification.isAdministrator(member)
```
Проверяет, является ли переданный объект member администратором на сервере.

### isOwner
```javascript
Verification.isOwner(member)
```
Проверяет, является ли переданный объект member владельцем сервера.

### isBot
```javascript
Verification.isBot(user)
```
Проверяет, является ли переданный объект user ботом.

### isVoiceChannel
```javascript
Verification.isVoiceChannel(channel)
```
Проверяет, является ли переданный объект channel голосовым каналом.

### isTextChannel
```javascript
Verification.isTextChannel(channel)
```
Проверяет, является ли переданный объект channel текстовым каналом.

### isCategoryChannel
```javascript
Verification.isCategoryChannel(channel)
```
Проверяет, является ли переданный объект channel категорией.

### isReply
```javascript
Verification.isReply(message)
```
Проверяет, является ли переданный объект message ответом на другое сообщение.

### isEphemeral
```javascript
Verification.isEphemeral(message)
```
Проверяет, является ли переданный объект message эфемерным (удаляется через некоторое время).

### mentionsEveryone
```javascript
Verification.mentionsEveryone(message)
```
Проверяет, содержит ли переданный объект message упоминание всех участников сервера.

### mentionsUser
```javascript
Verification.mentionsUser(message, user)
```
Проверяет, содержит ли переданный объект message упоминание конкретного пользователя, переданного в user.

### mentionsRole
```javascript
Verification.mentionsRole(message, role)
```
Проверяет, содержит ли переданный объект message упоминание конкретной роли, переданной в role.

### isRoleAbove
```javascript
Verification.isRoleAbove(role, targetRole)
```
Проверяет, является ли роль role выше указанной роли targetRole в иерархии

### isRoleBelow
```javascript 
Verification.isRoleBelow(role, targetRole)
```
Проверка, является ли роль ниже указанной роли в иерархии

### isMessageAuthor
```javascript
Verification.isMessageAuthor(message, user)
```
Проверка, является ли пользователь создателем сообщения

### isBotOwner
```javascript
Verification.isBotOwner(user, botOwnerId)
```
Проверка, является ли пользователь владельцем бота