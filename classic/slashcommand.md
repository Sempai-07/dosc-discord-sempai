# SlashCommandManager в библиотеки discord-sempai
Класс `SlashCommandManager` предоставляет удобный интерфейс для работы с глобальными и локальными (для конкретного сервера) командами `Slash` (/) в `Discord`. Класс использует библиотеку `discord.js` версии 14.

## Использование
Создание экземпляра класса
```javascript
Copy code
const { SlashCommandManager } = require('discord-sempai');

const myCommand = new SlashCommandManager({
  name: 'my-command',
  description: 'Описание моей команды',
  options: [
    {
      name: 'option-1',
      description: 'Описание опции 1',
      required: true,
      choices: [
        {
          name: 'вариант 1',
          value: 'value-1'
        },
        {
          name: 'вариант 2',
          value: 'value-2'
        }
      ]
    },
    {
      name: 'option-2',
      description: 'Описание опции 2',
      required: false
    }
  ],
  isGlobal: true, // Глобальная команда (по умолчанию)
  handler: interaction => {
    // Обработчик команды
    console.log(interaction.options);
  }
});
```
Установка обработчика команды

```javascript
myCommand.setHandler(interaction => {
  // Обработчик команды
  console.log(interaction.options);
});
```

Установка прав доступа к команде
```javascript
const permission = [
  {
    id: '1234567890', // ID роли или пользователя
    type: 'ROLE', // Тип объекта (роль или пользователь)
    permission: true // Разрешение или запрет
  }
];

myCommand.setPermission(permission);
```

Обновление команды
```javascript
myCommand.update(client);
```

Регистрация команды
```javascript
myCommand.register(client);
```

## Описание методов
`constructor(options)``
Конструктор класса `SlashCommandManager`. Принимает объект со следующими параметрами:

- `name` (строка, обязательный) - название команды
- `description` (строка, обязательный) - описание команды
- `options` (массив, необязательный) - массив объектов опций команды. Каждый объект должен содержать следующие поля:
name (строка, обязательный) - название опции
- `description` (строка, обязательный) - описание опции
- `required` (булево значение, необязательный) - является ли опция обязательной (по умолчанию false)
- `choices` (массив, необязательный) - массив объектов значений опции. Каждый объект должен содержать следующие поля:
  - `name` (строка, обязательный) - название значения
  - `value` (строка, обязательный) - значение, которое будет передано в обэкт


## Внимание 
`choices` можно добавить только через функцию: `addChoiceToOption`