# 

# Описание базы данных и ее использование в discord-sempai

База данных (англ. "database") - это специальное программное обеспечение, которое позволяет хранить и организовывать информацию. `discord-sempai`, база данных может быть использована для хранения информации о пользователях, каналах, серверах и других объектах Discord.

## Использование базы данных в discord-sempai
В `discord-sempai` для работы с базой данных можно использовать различные модули и библиотеки, такие как `mongodb`, `mysql` и `sqlite`, а также встроенный модуль `Database `


## Пример использования встроенного модуля
```js
const { Database } = require('discord-sempai');
const db = new Database({
  path: "./database",
  tables: ["main"],
  key: "test",
  // Для шифрования текста
});

// Добавление значения
db.add('table', 'key', 'value', 'encryption?');

// Изменение значения
db.set('table', 'key', 'value', 'encryption?');

// Получение значения
db.get('table', 'key', 'encryption?');

// Получение всего содержимого таблицы
db.all('table');

// Удаление переменную
db.delete('table', 'key', 'oldValue?');

// Удаление всего содержимого таблицы
db.deleteAll('table');

// Проверка наличия переменной
db.has('table', 'key');

// Получение информации о таблице
db.info('table', 'type?');

// Проверка существования таблицы
db.isTable('table');

// Подключение к базе данных
db.connect();
```
Это локальная база данных которая использует `database-sempai`

## Пример использования модуля sqlite
Для примера мы будем использовать модуль `sqlite`, который позволяет работать с базой данных `SQLite`.

Сначала нужно установить пакет sqlite с помощью команды npm install sqlite.

Затем необходимо создать базу данных и таблицы. Для этого можно использовать программу для работы с базой данных `SQLite`, например, `DB Browser for SQLite`.

В качестве примера, давайте создадим базу данных `discord.db` с таблицей `users`, которая будет содержать информацию о пользователях Discord. Таблица будет иметь три поля: `id`, `username` и `discriminator`.

```sql
CREATE TABLE users (
    id TEXT PRIMARY KEY,
    username TEXT,
    discriminator TEXT
);
```
Теперь можно подключить базу данных к нашему `discord-sempai` боту и использовать ее для хранения информации. Для подключения базы данных `SQLite` в `discord-sempai` необходимо использовать модуль `sqlite3`.

### Пример использования модуля sqlite3:
```js
const sqlite3 = require('sqlite3').verbose();

let db = new sqlite3.Database('./discord.db', sqlite3.OPEN_READWRITE, (err) => {
  if (err) {
    console.error(err.message);
  }
  console.log('Connected to the discord database.');
});

db.serialize(() => {
  db.run(`INSERT INTO users(id, username, discriminator) VALUES(?,?,?)`, ['123456789', 'User123', '1234'], function(err) {
    if (err) {
      return console.error(err.message);
    }
    console.log(`A row has been inserted with rowid ${this.lastID}`);
  });
});

db.close((err) => {
  if (err) {
    console.error(err.message);
  }
  console.log('Closed the discord database connection.');
});
```

В приведенном выше примере мы подключаем базу данных, добавляем пользователя в таблицу users и закрываем подключение.

## Заключение
В `discord-sempai` база данных может быть использована для хранения информации о пользователях, каналах, серверах и других объектах Discord. Для работы с базой данных можно использовать различные модули и библиотеки, такие как `mongodb`, `mysql` и `sqlite`. В данном примере мы использовали модуль `sqlite` для работы с базой данных SQLite.