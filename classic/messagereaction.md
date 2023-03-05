# MessageReaction в библиотеки discord-sempai
Класс `MessageReaction` используется для работы с реакциями на сообщения Discord в библиотеке `discord-sempai`. Он представляет собой обертку над объектом `MessageReaction` из библиотеки `discord.js` версии 14.

## Конструктор
Создает объект класса `MessageReaction` на основе объекта `MessageReaction`.

#### Параметры:

- `reaction` - объект `MessageReaction`.


## Методы
### getId()
Возвращает идентификатор реакции.

### getName()
Возвращает название реакции.

### getUsersCount(): number
Возвращает количество пользователей, которые нажали на данную реакцию.

### async getUsers()
Возвращает массив пользователей, которые нажали на данную реакцию.

## Пример
```javascript
const { Reaction } = require('discord-sempai');

const reaction = new Reaction(someMessageReaction);

console.log(reaction.getName()); // выводит название реакции
console.log(reaction.getUsersCount()); // выводит количество пользователей, которые нажали на данную реакцию

reaction.getUsers().then(users => {
  console.log(users); // выводит массив пользователей, которые нажали на данную реакцию
});

bot.on('messageReactionAdd', (reaction, user) => {
  const r = new Reaction(reaction);
  console.log(`${user.tag} нажал на реакцию "${r.getName()}"`);
});
```