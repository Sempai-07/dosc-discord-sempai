## 0.3.0@beta

- Теперь для подключения бота к Discord необходимо использовать метод `bot.connect("token")`.
- В методах `bot.loaderEvent`, `bot.loaderTextCmd` и `bot.loaderSlashCmd` теперь можно указывать только имя папки, где находятся команды. Это упрощает загрузку команд в случае, когда в папке находится много подпапок с командами.
- Добавлены методы `queueLength` и `hasMusicPlaying`, которые позволяют получить текущую длину очереди и информацию о том, играет ли музыка в данный момент.
- Добавлена поддержка `{field:name:description:inline}` в парсере сообщений.
- Теперь в кнопках можно использовать 5 стиль (ссылку).


## 0.2.0

- Теперь в функции `playSong` необходимо указывать все параметры в объекте

## 0.1.5

Добавлены следующие функции:
- `playSong` - для проигрывания музыкальной композиции
- `loopMusic` - для повторного проигрывания музыкального списка
- `progressBar` - для отображения текущего прогресса проигрывания
- `skipSong` - для перехода к следующей композиции в списке
- `stopQueue` - для остановки проигрывания списка
- `clearQueue` - для очистки списка
- `shuffleQueue` - для перемешивания композиции в списке
- `setVolume` - для установки громкости проигрывания
- `resumeQueue` - для возобновления проигрывания
- `pauseQueue` для приостановки проигрывания

Также были добавлены следующие события:
- `channelEmpty` - для оповещения о том, что канал пуст
- `clientDisconnect` - для оповещения об отключении клиента
- `clientUndeafen` - для оповещения о том, что клиент больше не приглушен
- `error` - для оповещения об ошибке
- `playlistAdd` - для оповещения о добавлении новой композиции в список
- `queueDestroyed` - для оповещения об удалении списка
- `queueEnd` - для оповещения о завершении списка
- `songAdd` для оповещения о добавлении новой композиции в списоо
- `songChanged` - для оповещения о смене композиции в списке
- `songFirst` - для оповещения о том, что проигрывается первая композиция в списке
- `songMoved` - для оповещения о перемещении композиции в списке.

## О 1.0.0 и ниже, я забыл(