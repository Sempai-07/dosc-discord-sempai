# Библиотека discord-Sempai: ActionComponent
Библиотека `discord-sempai` предоставляет различные инструменты для создания и управления ботами на платформе `discord`. Один из таких инструментов - это класс `ActionComponent`, который предоставляет функции для работы с интерактивных компонентами на сервере `discord`.

## addButton
Конструктор класса не принимает аргументов и создает новый экземпляр класса.

Для добавления кнопок в компонент, можно использовать метод `addButton(button)`, который принимает объект `button` с следующими свойствами:

- `label` (обязательно): текст на кнопке.
- `style` (обязательно): стиль кнопки, может быть `PRIMARY`, `SECONDARY` или `DANGER`.
- `customId`: идентификатор кнопки, который будет использоваться при обработке взаимодействия.
- `disabled`: логическое значение, указывающее, будет ли кнопка недоступна для нажатия.
- `emoji`: объект `emoji`, который будет отображаться на кнопке (опционально).
- `url`: ссылка, на которую будет перенаправлен пользователь при нажатии на кнопку (опционально).


## Пример использования метода `addButton()`:

```javascript
const { ActionComponent } = require('discord-sempai');

const button = {
  label: 'Нажми меня!',
  style: 'PRIMARY',
  customId: 'button-1'
};

const action = new ActionComponent()
  .addButton(button);
  
bot.command({
  name: 'button',
  code: (client, message, args) => {
     message.reply({content: 'Button', components: [action]})
    }
 })
 
bot.interactionCreate({
  id: 'button-1',
  type: 'button',
  code: (client, interaction) => {
    return interaction.reply('Button click!')
  }
})
```

## addSelectMenu
Для добавления меню выбора в компонент, можно использовать метод `addSelectMenu(menu)`, который принимает объект menu со следующими свойствами:

- `customId` (обязательно): идентификатор меню выбора, который будет использоваться при обработке взаимодействия.
- `placeholder` (обязательно): текст, который будет отображаться в меню выбора, пока пользователь не выберет ни одного пункта.
- `minValue`: минимальное количество выбранных пользователем пунктов.
- `maxValue`: максимальное количество выбранных пользователем пунктов.
- `options` (обязательно): массив объектов option со следующими свойствами:
   - `label` (обязательно): текст для отображения пункта в меню выбора.
   - `value` (обязательно): уникальное значение, которое будет возвращено при выборе пользователем этого пункта.
   - `description`: описание пункта, которое будет отображаться при наведении на него.

## Пример использования метода addSelectMenu():

```javascript
const { ActionComponent } = require('discord-sempai');

const selectMenu = {
  customId: 'menu-1',
  placeholder: 'Выберите один пункт',
  options: [
    {
      label: 'Пункт 1',
      value: 'option-1'
    },
    {
      label: 'Пункт 2',
      value: 'option-2',
      description: 'Описание для пункта 2'
    }
  ]
};

const action = new ActionComponent()
  .addSelectMenu(selectMenu)
  
bot.command({
  name: 'select',
  code: (client, message, args) => {
     message.reply({content: 'Select menu', components: [action]})
    }
 })
 
bot.interactionCreate({
  id: 'option-1',
  type: 'select',
  code: (client, interaction) => {
    return interaction.reply('Select menu, options 1!')
  }
})
```