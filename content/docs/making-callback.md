---
title: 'MakeCallBack'
weight: 6
description: 'Метод MakeCallBack - примените этот метод для совершения обратного звонка. Для этого выполните POST запрос с входными параметрами к точке подключения, указанными ниже. Точка подключения: POST: https://api.exolve.ru/call/v1/MakeCallback'
---

## Метод MakeCallBack

Примените этот метод для совершения обратного звонка. Для этого выполните POST запрос с входными параметрами к точке подключения, указанными ниже.

**Точка подключения**:

```html
POST: https://api.exolve.ru/call/v1/MakeCallback
```

### Авторизация

Передайте следующие Заголовки HTTP для успешной авторизации.

| Имя               |  Тип   | Описание                                                                                                                                                        |
| ----------------- | :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Authorization** | string | [API-ключ приложения](/docs/ru/instructions/getting-api-key) с `Bearer` перед ним. Пример: `Bearer e***s0`, где `e***s0` замените на API-ключ вашего приложения |

### Входные параметры

Передайте следующие параметры в теле запроса в JSON формате. Параметры, отмеченные жирным шрифтом, являются обязательными.

| Параметр                 |        Тип        | Описание                                                                                                                                                                                |
| ------------------------ | :---------------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| request_description      |      string       | идентификатор запроса со стороны клиента                                                                                                                                                |
| **number_code**          |      uint64       | номер для использования услуги обратного звонка                                                                                                                                         |
| **callback_resource_id** |      uint64       | уникальный идентификатор ресурса обратного звонка. Чтобы получить идентификатор, [создайте ресурс обратного звонка](/docs/ru/api-reference/callback-api/creating-callback) в приложении |
| duration                 |      uint32       | максимальная длительность соединенного вызова двух абонентов в секундах: от 300 до 3600 (по умолчанию: 1800)                                                                            |
| **line_1**               | [Line_x](#line_x) | настройки первого плеча                                                                                                                                                                 |
| **line_2**               | [Line_x](#line_x) | настройки второго плеча                                                                                                                                                                 |

#### Line_x

| Параметр         |             Тип             | Описание                                                                                                               |
| ---------------- | :-------------------------: | ---------------------------------------------------------------------------------------------------------------------- |
| **destinations** | [Destination](#destination) | Список абонентов плеча Х (до 10 на каждом)                                                                             |
| ring_logic       |            enum             | Принцип обзвона. Значение `1` для последовательного обзвона, значение `2` для параллельного. Значение `1` по умолчанию |
| display_number   |           string            | отображаемый номер первого плеча                                                                                       |
| audio            |    oneof [Audio](#audio)    | аудиосообщение для абонента плеча Х                                                                                    |

#### Destination

| Параметр   |  Тип   | Описание                                                                                               |
| ---------- | :----: | ------------------------------------------------------------------------------------------------------ |
| **number** | string | номер или SIP-URI абонента                                                                             |
| timeout    | uint32 | максимальное время дозвона до абонента от инициации вызова в секундах: от 10 до 600 (по умолчанию: 30) |

#### Audio

| Параметр          |     Тип     | Описание                                                                  |
| ----------------- | :---------: | ------------------------------------------------------------------------- |
| media_resource_id |   uint64    | уникальный идентификатор медиаресурса для аудиосообщения абоненту плеча Х |
| tts               | [Tts](#tts) | параметры синтеза речи для аудиосообщения абоненту плеча Х                |

#### Tts

| Параметр |           Тип            | Описание                                                      |
| -------- | :----------------------: | ------------------------------------------------------------- |
| **text** |          string          | текст для синтеза речи (максимальная длительность 24 секунды) |
| voice    |   enum [Voice](#voice)   | голос для синтеза                                             |
| lang     |    enum [Lang](#lang)    | язык синтеза речи (русский по умолчанию)                      |
| volume   |          int32           | нормализация громкости ( от -149 до 0, по умолчанию: -19 )    |
| speed    |          double          | темп речи от 0.1 до 3.0 (по умолчанию: 1.0)                   |
| emotion  | enum [Emotion](#emotion) | амплуа, в зависимости от выбранного голоса (по умолчанию: 1)  |
| provider |          string          | поставщик TTS (1 - yandex)                                    |

#### Voice

| Параметр | Тип  | Описание |
| -------- | :--: | -------- |
| 1        | enum | Алёна    |
| 2        | enum | Ермиль   |
| 3        | enum | Джейн    |
| 4        | enum | Омаж     |
| 5        | enum | Захар    |

#### Lang

| Параметр | Тип  | Описание   |
| -------- | :--: | ---------- |
| 1        | enum | русский    |
| 2        | enum | английский |

#### Emotion

| Параметр | Тип  | Описание         |
| -------- | :--: | ---------------- |
| 1        | enum | нейтральная      |
| 2        | enum | доброжелательная |
| 3        | enum | озлобленная      |

### Выходные параметры

| Параметр |  Тип   | Описание                                               |
| -------- | :----: | ------------------------------------------------------ |
| call_id  | string | уникальный идентификатор совершенного обратного звонка |

### Возможные ошибки

| Код |    Статус    | Пример сообщения                                                         | Описание                                                                                                |
| --- | :----------: | ------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------- |
| 401 | Unauthorized | malformed token                                                          | не указан / не правильно указан API-ключ приложения                                                     |
| 404 |  Not Found   |                                                                          | не валидный URL запроса                                                                                 |
| 403 |  Forbidden   | customer not active                                                      | нет доступа к услуге обратного звонка из-за статуса аккаунта пользователя (не активирован/заблокирован) |
| 400 | Bad Request  | invalid MakeCallbackRequest.Line_1: embedded message failed validation   | невалидный запрос                                                                                       |
| 400 | Bad Request  | Application [app_id] does not own resource [number/callback_resource_id] | номер/ресурс обратного звонка не принадлежит приложению                                                 |

### Примеры

Входные параметры:

```json
{
	"request_description": "test",
	"callback_resource_id": 1221,
	"number_code": 74999999999,
	"line_1": {
		"destinations": [
			{
				"number": "78129999999"
			},
			{
				"number": "74959999999"
			}
		],
		"ring_logic": 1,
		"audio": {
			"media_resource_id": 685
		}
	},
	"line_2": {
		"destinations": [
			{
				"number": "79599999999"
			},
			{
				"number": "79999999999"
			}
		],
		"ring_logic": 2,
		"audio": {
			"tts": {
				"text": "Обратный звонок с сайта",
				"voice": 3,
				"lang": 1,
				"speed": 1.5,
				"emotion": 1,
				"provider": 1
			}
		}
	}
}
```

Выходные параметры:

```json
{
	"call_id": "cal71bd36ce-2f5c-4d25-8319-406214596b72"
}
```
