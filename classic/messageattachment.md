# Библиотека discord-Sempai: MessageAttachment
Библиотека `discord-sempai` предоставляет различные инструменты для создания и управления ботами на платформе `discord`. Один из таких инструментов - это класс `MessageAttachment`, который предоставляет функции для работы с файлами на сервере `discord`.

## Основное

Конструктор класса `MessageAttachment` принимает объект `options`, который может содержать следующие свойства:

- `attachment` (обязательно): путь к файлу, который нужно прикрепить к сообщению.
- `name`: имя файла, которое будет отображаться в `discord`.
- `data`: содержимое файла в виде буфера или строки.
- `url`: ссылка на файл, который нужно прикрепить к сообщению.

Если свойство `attachment` отсутствует, то будет выведено сообщение об ошибке.

Для использования данного класса, вы можете создать новый экземпляр класса, передав объект options в конструктор, как показано ниже:

```javascript
const { MessageAttachment } = require('discord-sempai');

const attachmentOptions = {
  attachment: './path/to/file.png',
  name: 'file.png'
};

const attachment = new MessageAttachment(attachmentOptions);
```
Вы можете затем использовать созданный объект attachment вместе с методом send или reply вашего объекта Message для прикрепления файла к сообщению, как показано ниже:

```javascript
message.channel.send({content: 'Вот ваш файл:', files: [attachment]});
```

Важно помнить, что размер вложения не должен превышать максимально допустимый размер для `Discord`. Рекомендуется также проверять, что файлы, которые вы прикрепляете, имеют допустимое расширение и тип `MIME`.