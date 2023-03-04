# Cache в библиотеки discord-sempai

Класс `Cache` является частью библиотеки `discord-sempai` и используется для хранения и управления кешем в Discord.js v14.

Конструктор
```javascript
const { Cache } = require('discord-sempai')

const cache = new Cache()
```
Создает новый экземпляр класса `Cache`. Инициализирует cache как новую `Map`, и events как объект со свойствами `update`, `delete` и `clear`, содержащими массивы обработчиков событий.

## Методы
### set(key, value, lifetime = 0)
Устанавливает значение в кеш.

- `key` - ключ кеша.
- `value` - значение кеша.
- `lifetime` - время жизни значения в секундах.

### get(key)
Возвращает значение кеша или undefined, если ключ не найден или значение просрочено.

### delete(key)
Удаляет значение из кеша по ключу.

### clear()
Очищает весь кеш.

### size()
Возвращает количество элементов в кеше.

### getKeys()
Возвращает массив всех ключей в кеше.

### getValues()
Возвращает массив всех значений в кеше.

### has(key)
Возвращает true, если ключ присутствует в кеше, и false в противном случае.

### getExpiration(key)
Возвращает время жизни значения в кеше по ключу.

### getCreatedAt(key)
Возвращает дату и время создания значения в кеше по ключу.

### getExpiresAt(key)
Возвращает дату и время истечения срока действия значения в кеше по ключу.

### getOldestKey()
Возвращает ключ самого старого значения в кеше.

### getNewestKey()
Возвращает ключ самого нового значения в кеше.

## События

```javascript
cache.on('update', (newValue, oldValue) => {
   console.log(newValue)
   console.log(oldValue)
})

cache.on('delete', (oldValue) => {
   console.log(oldValue)
})

cache.on('clear', (oldValue) => {
   console.log(oldValue)
})

cache.set('name', 35, 56)

cache.off('update', (newValue, oldValue) => {
   console.log(newValue)
   console.log(oldValue)
})
```

Вызывать события нужно первым делом