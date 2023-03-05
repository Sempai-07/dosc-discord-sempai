## 0.3.3

- исправил ошибку в `interactionCreate`, `loaderSlashCmd`, вы не могли просто создать кмд без опций

## 0.3.0

- Добавлены новые классы: `Cache`, `GuildEmoji`, `GuildManager`, `MessageReaction`, `GuildRole`, `GuildWebhook`, `GuildInvite`, `PermissionChecker`, `GuildVoice`, `MessageCollection`, `MessageReplyOption`, `Paginator`, `Randomizer`, `TextFormatter`, `Verification`, `FileManager`, `ErrorHandler`, `AsyncHandler`, `SlashCommandManager`, `SlashCommandOption`, `ContextMenuManager`.
- Добавлен параметр `prototype` в `interactionCreate` и `loaderComponent`, это замена параметра `type`.
- Добавлен параметр `contextmenu` в `interactionCreate` и `loaderComponent`.
- Добавлены новые функции в класс Music: `isMusicPlaying`, i`sTrackPaused`, `isTrackLooping`, `isQueueLooping`, `getLoopType`, `getCurrentVolume`, `queueLength`, `skipTrack`, `loopMusic`, `queueSongs`.
- В `createEvent` и `loaderEvent` первым параметром теперь является `client`.
- В `interactionCreate` и `loaderComponent`(slash) был  третий параметр `args`.
- Для подключения бота к `Discord` теперь необходимо использовать метод `bot.connect("token")`.
- В методах `bot.loaderEvent`, `bot.loaderTextCmd` и `bot.loaderSlashCmd` теперь можно указывать только имя папки, где находятся команды.
- Добавлена поддержка `{field:name:description:inline}` в парсере сообщений.
- Теперь в кнопках можно использовать 5 стиль (ссылку).

Удалено:
- Все функции, которые не относятся к классам.
- Класс `Util` был удален.


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