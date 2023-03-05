# MessageReplyOption в библиотеке discord-sempai
Класс `MessageReplyOption` является частью библиотеки `discord-sempai`, использующей `discord.js v14`, и представляет собой объект, содержащий опции ответа на сообщение в `Discord`.

## Методы
### setContent(content)
Устанавливает текстовое содержимое ответа.

### setEmbeds(embeds)
Устанавливает массив Embed-объектов, которые будут включены в ответ.

### addEmbed(embed)
Добавляет Embed-объект в массив вложений.

### addEmbeds(embeds)
Добавляет массив Embed-объектов в массив вложений.

### setComponents(components)
Устанавливает массив MessageActionRow-объектов, которые будут включены в ответ.

### addComponent(component)
Добавляет MessageActionRow-объект в массив компонентов.

### addComponents(components)
Добавляет массив MessageActionRow-объектов в массив компонентов.

### setEphemeral(ephemeral)
Устанавливает флаг "эфемерность", который делает ответ видимым только для автора и никого больше.

### setTTS(tts)
Устанавливает флаг TTS (Text-to-Speech), который делает содержимое ответа звучащим.

### setAllowedMentions(allowedMentions)
Устанавливает параметры упоминаний (Mentions) для ответа.

### setReply(reference)
Устанавливает ссылку на сообщение, на которое данный ответ является ответом.

### async send(channel)
Отправляет ответ в заданный канал и возвращает объект сообщения Message. В случае, если установлен флаг "эфемерности", сообщение будет удалено через короткое время после отправки.

### static create(options)
Создает новый объект `MessageReplyOption` на основе заданных опций.

### static embed(data)
Создает новый объект `EmbedBuilder` на основе заданных данных.