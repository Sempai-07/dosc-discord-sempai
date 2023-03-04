# Randomizer в библиотеке discord-sempai

Класс `Randomizer` в библиотеке `discord-sempai` предоставляет методы для генерации случайных чисел, строк, элементов массивов, объектов, дат, `IP-адресов`, цветов, координат, телефонных номеров, электронных адресов, паролей и т.д.

Этот класс может быть использован для различных задач в `Discord.js`, например, для генерации случайного имени пользователя или пароля, для генерации случайного цвета для эмбедов, для генерации случайных координат и телефонных номеров, для генерации случайного времени и даты для сообщений и т.д.

Пример использования класса:
```javascript
const user = {
  id: Randomizer.generateRandomString(6),
  firstName: Randomizer.generateRandomString(8),
  lastName: Randomizer.generateRandomString(10),
  email: Randomizer.generateRandomEmail(),
  phone: Randomizer.generateRandomPhoneNumber(),
  age: Randomizer.generateRandomNumber(18, 60),
  gender: Randomizer.generateRandomElement(['Male', 'Female']),
  address: {
    city: Randomizer.generateRandomString(10),
    state: Randomizer.generateRandomString(6),
    country: Randomizer.generateRandomString(8)
  }
};

console.log(user)
```