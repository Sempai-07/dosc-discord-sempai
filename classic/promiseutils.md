# PromiseUtils в библиотеке discord-sempai
Класс `PromiseUtils` предоставляет набор статических методов для работы с объектами `Promise` в `JavaScript`. Эти методы позволяют выполнить операции, такие как ожидание выполнения `Promise`, преобразование функций, возвращающих обратный вызов `callback`, в функции, возвращающие `Promise`, и многое другое.

## Методы
### resolve(value)
Принимает значение и возвращает `Promise`, который успешно завершается с этим значением.

### reject(error)
Принимает ошибку и возвращает `Promise`, который завершается с этой ошибкой.

### delay(ms)
Принимает время в миллисекундах и возвращает `Promise`, который успешно завершается после заданной задержки.

### all(promises)
Принимает массив `Promise` и возвращает `Promise`, который успешно завершается, когда все `Promise` в массиве завершаются.

### race(promises)
Принимает массив `Promise` и возвращает `Promise`, который успешно завершается, когда любой `Promise` в массиве завершается.

### allSettled(promises)
Принимает массив `Promise` и возвращает `Promise`, который завершается только после того, как все `Promise` в массиве завершатся (успешно или с ошибкой).

### any(promises)
Принимает массив `Promise` и возвращает `Promise`, который завершается, когда любой `Promise` в массиве завершается успешно.

### try(func)
Принимает функцию и возвращает `Promise`, который завершается успешно с результатом выполнения этой функции.

### promisify(func)
Принимает функцию с обратным вызовом `callback` и возвращает новую функцию, которая возвращает Promise вместо вызова обратного вызова.

### promisifyMethod(object, methodName)
Принимает объект и имя метода, который принимает обратный вызов `callback`, и возвращает новую функцию, которая возвращает `Promise` вместо вызова метода с обратным вызовом.

### callbackify(func)
Принимает функцию, которая возвращает `Promise`, и возвращает новую функцию, которая принимает обратный вызов `callback` вместо возвращения `Promise`.

### callbackifyMethod(object, methodName)
Принимает объект и имя метода, который возвращает `Promise`, и возвращает новую функцию, которая принимает обратный вызов `callback` вместо возвращения `Promise`.

### map(promises, mapper)
Принимает массив `Promise` и функцию-преобразователь `mapper` и возвращает `Promise`, который успешно завершается с массивом результатов, полученных при применении функции-преобразователя к каждому `Promise` в массиве.

### filter(promises, predicate)
Принимает массив `Promise` и функцию-предикат `predicate` и возвращает `Promise`, который успешно завершается с массивом `Promise`, для которых функция-предикат вернула `true`.

### reduce(promises, reducer, initialValue)
Метод принимает массив промисов `promises`, функцию `reducer` и начальное значение `initialValue`. Метод последовательно применяет функцию `reducer` к каждому элементу массива `promises`, начиная с начального значения `initialValue`. В результате получается один промис со значением, которое вернула последняя итерация функции reducer.

### waterfall(tasks, initialValue)
Метод принимает массив функций `tasks` и начальное значение `initialValue`. Метод последовательно вызывает каждую функцию `task`, передавая ей результат выполнения предыдущей функции. В результате получается один промис со значением, которое вернула последняя функция в массиве `tasks`.

### retry(func, options)
Метод принимает функцию `func` и объект `options`, содержащий параметры `maxAttempts` и `delay`. Метод пытается выполнить функцию `func`, повторяя ее выполнение не более `maxAttempts` раз в случае ошибки. Между повторными попытками ожидание происходит в течение `delay` миллисекунд. Если после `maxAttempts` попыток выполнение функции `func` не удалось, метод вернет ошибку.

### timeout(promise, ms)
Метод принимает промис `promise` и время ожидания `ms` в миллисекундах. Метод возвращает новый промис, который будет завершен успешно, если промис `promise` завершится раньше времени `ms`. Если время `ms` истекает до того, как промис `promise` завершится, то возвращается промис, завершенный с ошибкой "Promise timed out".

### sequence(tasks)
Метод принимает массив функций `tasks`. Метод вызывает каждую функцию `task` последовательно, передавая ей результирующий массив предыдущих выполненных функций. В результате получается один промис, который завершается массивом значений, возвращаемых каждой функцией `task`.

## Пример использования
```javascript
const { PromiseUtils } = require('discord-sempai');

// Пример использования метода resolve
const promise1 = PromiseUtils.resolve(42);

// Пример использования метода reject
const promise2 = PromiseUtils.reject(new Error('Something went wrong'));

// Пример использования метода delay
PromiseUtils.delay(1000).then(() => console.log('Delayed message'));

// Пример использования метода all
PromiseUtils.all([promise1, promise2]).then(results => console.log(results));

// Пример использования метода race
PromiseUtils.race([promise1, promise2]).then(result => console.log(result));

// Пример использования метода allSettled
PromiseUtils.allSettled([promise1, promise2]).then(results => console.log(results));

// Пример использования метода any
PromiseUtils.any([promise1, promise2]).then(result => console.log(result));

// Пример использования метода try
PromiseUtils.try(() => {
  // Код, который может вызвать ошибку
}).then(result => console.log(result)).catch(error => console.error(error));

// Пример использования метода promisify
const fs = require('fs');
const readFileAsync = PromiseUtils.promisify(fs.readFile);
readFileAsync('./file.txt').then(data => console.log(data)).catch(error => console.error(error));

// Пример использования метода promisifyMethod
const obj = {
  method(callback) {
    setTimeout(() => {
      callback(null, 'result');
    }, 1000);
  }
};
const methodAsync = PromiseUtils.promisifyMethod(obj, 'method');
methodAsync().then(result => console.log(result)).catch(error => console.error(error));

// Пример использования метода callbackify
const asyncFunction = async () => {
  // Код, который возвращает Promise
};
const callbackFunction = PromiseUtils.callbackify(asyncFunction);
callbackFunction((error, result) => {
  if (error) {
    console.error(error);
  } else {
    console.log(result);
  }
});

// Пример использования метода callbackifyMethod
const obj2 = {
  asyncMethod() {
    // Код, который возвращает Promise
  }
};
const callbackMethod = PromiseUtils.callbackifyMethod(obj2, 'asyncMethod');
callbackMethod((error, result) => {
  if (error) {
    console.error(error);
  } else {
    console.log(result);
  }
});

// Пример использования метода map
const promises = [promise1, promise2];
const mappedPromises = PromiseUtils.map(promises, promise => promise.then(result => result * 2));
mappedPromises.then(results => console.log(results));

// Пример использования метода filter
const filteredPromises = PromiseUtils.filter(promises, promise => promise.then(result => result > 0));
filteredPromises.then(results => console.log(results));

// Пример использования метода reduce
const reducer = (sum, value) => {
  return value.then(result => sum + result);
};
PromiseUtils.reduce(promises, reducer, 0).then(result => console.log(result));

// Пример использования метода waterfall
const tasks = [
  () => Promise.resolve(1),
  result => Promise.resolve(result + 2),
  result => Promise.resolve(result * 3)
];
PromiseUtils.waterfall(tasks, 0).then(result => console.log(result));

// Пример использования метода retry
const func = () => {
  // Код, который может вызвать ошибку
};
PromiseUtils.retry(func, { maxAttempts: 3, delay: 1000 }).then(result => console.log(result))
```