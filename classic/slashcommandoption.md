# SlashCommandOption в библиотеке,discord-sempai

Класс `SlashCommandOption` представляет собой дополнительную опцию для `SlashCommandBuilder` в `Discord.js v14`. Он наследуется от класса `SlashCommandStringOption` и позволяет создавать строковые опции для взаимодействия пользователя с командами.

## Использование
Для использования класса `SlashCommandOption` необходимо установить `discord.js` версии 14 и импортировать его в свою программу:

```js
const { SlashCommandOption } = require('discord-sempai');
```
Затем можно создать экземпляр класса, передав ему необходимые параметры:

```js
const option = new SlashCommandOption({
  name: 'имя_опции',
  description: 'описание опции',
  required: true, // по умолчанию false
});
```
`SlashCommandOption` принимает следующие параметры:

- `name` (обязательный): имя опции;
- `description` (обязательный): описание опции;
- `required` (необязательный): является ли опция обязательной, по умолчанию `false`.

## Наследование
Класс `SlashCommandOption` наследуется от `SlashCommandStringOption` и имеет те же методы и свойства. Вы можете использовать любой метод, доступный в `SlashCommandStringOption`, в `SlashCommandOption`.

## Пример
```js
const { SlashCommandOption } = require('discord-sempai');
const { SlashCommandBuilder } = require('discord.js');

const command = new SlashCommandBuilder()
  .setName('test')
  .setDescription('Тестовая команда')
  .addStringOption(option => option
    .setName('опция')
    .setDescription('Тестовая опция')
    .setRequired(true)
  );
  
// Использование SlashCommandOption вместе с SlashCommandBuilder:
const customOption = new SlashCommandOption({
  name: 'новая_опция',
  description: 'Описание новой опции',
  required: true,
});
command.addStringOption(customOption);
```