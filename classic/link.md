# Библиотеки Discord-Sempai: Link
Библиотека `discord-sempai` - это набор классов и методов для упрощения разработки ботов для `Discord`. Одним из таких классов является `Link`, который предоставляет несколько методов для работы с HTTP-запросами.

## Класс Link
Класс `Link` содержит следующие методы:

### request(url)
Метод request отправляет HTTP-запрос `GET` на указанный URL-адрес и возвращает объект с данными ответа и статусом.

### validLink(url)
Метод `validLink` проверяет, является ли указанный URL-адрес действительным и доступным. Возвращает `true`, если адрес действительный, и `false` в противном случае.

### validImage(url)
Метод `validImage` проверяет, является ли содержимое по указанному URL-адресу изображением. Возвращает `true`, если содержимое является изображением, и `false` в противном случае.

### postRequest(url, data)
Метод `postRequest` отправляет HTTP-запрос `POST` на указанный URL-адрес с указанными данными и возвращает объект с данными ответа и статусом.

### putRequest(url, data)
Метод `putRequest` отправляет HTTP-запрос `PUT` на указанный URL-адрес с указанными данными и возвращает объект с данными ответа и статусом.

### deleteRequest(url)
Метод `deleteRequest` отправляет HTTP-запрос `DELETE` на указанный URL-адрес и возвращает объект с данными ответа и статусом.

## Пример использования класса Link
```javascript
const Link = require('discord-sempai').Link;

async function testLink(url) {
  if (await Link.validLink(url)) {
    const response = await Link.request(url);
    console.log(`Status: ${response.status}`);
    console.log(`Data: ${response.data}`);
  } else {
    console.log(`Invalid URL: ${url}`);
  }
}

testLink('https://jsonplaceholder.typicode.com/todos/1');
```

```js
// Выполнить POST запрос
const postData = { name: "John", age: 30 };
const postResponse = await Link.postRequest(url, postData);

// Выполнить PUT запрос
const putData = { name: "Mike", age: 40 };
const putResponse = await Link.putRequest(url, putData);

// Выполнить DELETE запрос
const deleteResponse = await Link.deleteRequest(url);


```js
bot.command({
  name: 'request',
  code: async (client, message, args) => {
    let text = await Link.request('https://some-random-api.ml/animal/dog');
    let image = new MessageEmbed()
    .setImage(text['image'])
   message.reply({embeds: [image]});
  }
});
```


В этом примере мы импортируем класс `Link` из библиотеки `discord-sempai` и используем его метод `validLink` для проверки указанного URL-адреса. Если адрес действительный, мы отправляем запрос с помощью метода `request` и выводим статус и данные ответа в консоль.