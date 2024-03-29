---
title: 'Outbound Call Events (SIP ID)'
weight: 4
description: 'Outbound Call Events - параметры уведомлений на URL об исходящих звонках с SIP ID.'
---

## Параметры уведомлений

### Originate

Инициация вызова с SIP ID на номер B-абонента (номер телефона, на который совершается вызов).

| Параметр         |   Тип   | Описание                                                                                             |
| ---------------- | :-----: | ---------------------------------------------------------------------------------------------------- |
| service          | string  | сервис для отправки уведомления                                                                      |
| date_time        | string  | дата события в формате [RFC-3339 / ISO-8601](https://datatracker.ietf.org/doc/html/rfc3339)          |
| number_a         | string  | номер A-абонента (определяемый номер Exolve, привязанный к SIP ID)                                   |
| number_b         | string  | номер B-абонент (номер телефона, на который совершён вызов)                                          |
| call_sid         | string  | уникальный идентификатор вызова                                                                      |
| type             | string  | тип уведомления, значение - o                                                                        |
| sip_id           | string  | SIP ID, с которого совершён звонок                                                                   |
| record_call      | boolean | признак записи разговора. `True`, если разговор записывается. `False`, если разговор не записывается |
| uid              | uint64  | уникальный идентификатор вызова. Одинаковый во всех событиях и запросах в рамках одного вызова       |
| application_uuid | string  | уникальный идентификатор приложения, через которое проходит вызов                                    |
| customer_id      | uint64  | уникальный идентификатор пользователя                                                                |
| direction        | string  | направление звонка - outbound (исходящий)                                                            |
| display_number   | string  | номер, который видит B-абонент                                                                       |

#### Пример

```json
{
	"service": "sip",
	"date_time": "2024-01-05T11:09:29.934881Z",
	"number_a": "79991112233",
	"number_b": "79994445566",
	"call_sid": "call-test-12345",
	"type": "o",
	"sip_id": "883140123456789",
	"record_call": true,
	"uid": 12345678910,
	"application_uuid": "178ec145-6898-4b06-a92a-75f63cb57046",
	"customer_id": 1111,
	"direction": "outbound",
	"display_number": "79991112233"
}
```

### Start

Фактический ответ B-абонента (владелец номера, на который совершается вызов, поднял трубку).

| Параметр         |   Тип   | Описание                                                                                             |
| ---------------- | :-----: | ---------------------------------------------------------------------------------------------------- |
| service          | string  | сервис для отправки уведомления                                                                      |
| date_time        | string  | дата события в формате [RFC-3339 / ISO-8601](https://datatracker.ietf.org/doc/html/rfc3339)          |
| number_a         | string  | номер A-абонента (определяемый номер Exolve, привязанный к SIP ID)                                   |
| number_b         | string  | номер B-абонент (номер телефона, на который совершён вызов)                                          |
| call_sid         | string  | уникальный идентификатор вызова                                                                      |
| type             | string  | тип уведомления, значение - s                                                                        |
| sip_id           | string  | SIP ID, с которого совершён звонок                                                                   |
| record_call      | boolean | признак записи разговора. `True`, если разговор записывается. `False`, если разговор не записывается |
| uid              | uint64  | уникальный идентификатор вызова. Одинаковый во всех событиях и запросах в рамках одного вызова       |
| application_uuid | string  | уникальный идентификатор приложения, через которое проходит вызов                                    |
| customer_id      | uint64  | уникальный идентификатор пользователя                                                                |
| direction        | string  | направление звонка - outbound (исходящий)                                                            |
| display_number   | string  | номер, который видит B-абонент                                                                       |

#### Пример

```json
{
	"service": "sip",
	"date_time": "2024-01-05T11:09:38.579416Z",
	"number_a": "79991112233",
	"number_b": "79994445566",
	"call_sid": "call-test-12345",
	"type": "s",
	"sip_id": "883140123456789",
	"record_call": true,
	"uid": 12345678910,
	"application_uuid": "178ec145-6898-4b06-a92a-75f63cb57046",
	"customer_id": 1111,
	"direction": "outbound",
	"display_number": "79991112233"
}
```

### Hungup

Разъединение/окончание вызова.

| Параметр         |   Тип   | Описание                                                                                             |
| ---------------- | :-----: | ---------------------------------------------------------------------------------------------------- |
| service          | string  | сервис для отправки уведомления                                                                      |
| date_time        | string  | дата события в формате [RFC-3339 / ISO-8601](https://datatracker.ietf.org/doc/html/rfc3339)          |
| number_a         | string  | номер A-абонента (определяемый номер Exolve, привязанный к SIP ID)                                   |
| number_b         | string  | номер B-абонент (номер телефона, на который совершён вызов)                                          |
| call_sid         | string  | уникальный идентификатор вызова                                                                      |
| type             | string  | тип уведомления, значение - h                                                                        |
| sip_id           | string  | SIP ID, с которого совершён звонок                                                                   |
| record_call      | boolean | признак записи разговора. `True`, если разговор записывается. `False`, если разговор не записывается |
| uid              | uint64  | уникальный идентификатор вызова. Одинаковый во всех событиях и запросах в рамках одного вызова       |
| application_uuid | string  | уникальный идентификатор приложения, через которое проходит вызов                                    |
| customer_id      | uint64  | уникальный идентификатор пользователя                                                                |
| direction        | string  | направление звонка - outbound (исходящий)                                                            |
| display_number   | string  | номер, который видит B-абонент                                                                       |

#### Пример

```json
{
	"service": "sip",
	"date_time": "2024-01-05T11:09:42.862513Z",
	"number_a": "79991112233",
	"number_b": "79994445566",
	"call_sid": "call-test-12345",
	"type": "h",
	"sip_id": "883140123456789",
	"record_call": true,
	"uid": 12345678910,
	"application_uuid": "178ec145-6898-4b06-a92a-75f63cb57046",
	"customer_id": 1111,
	"direction": "outbound",
	"display_number": "79991112233"
}
```

### Definition

Окончание вызова с причинами разъединения для каждого из абонентов (SIP ID и номер, на который совершён вызов).

| Параметр         |   Тип   | Описание                                                                                             |
| ---------------- | :-----: | ---------------------------------------------------------------------------------------------------- |
| service          | string  | сервис для отправки уведомления                                                                      |
| date_time        | string  | дата события в формате [RFC-3339 / ISO-8601](https://datatracker.ietf.org/doc/html/rfc3339)          |
| number_a         | string  | номер A-абонента (определяемый номер Exolve, привязанный к SIP ID)                                   |
| number_b         | string  | номер B-абонент (номер телефона, на который совершён вызов)                                          |
| call_sid         | string  | уникальный идентификатор вызова                                                                      |
| type             | string  | тип уведомления, значение - d                                                                        |
| sip_id           | string  | SIP ID, с которого совершён звонок                                                                   |
| setup_time       | uint32  | время ожидания A-абонента до соединения с B-абонентом или отбоя                                      |
| wait_time        | uint32  | время ожидания A-абонента до фактического ответа B-абонента                                          |
| duration         | uint32  | время фактического разговора абонентов в миллисекундах                                               |
| full_duration    | uint32  | время разговора в миллисекундах c учетом проигрывания аудиосообщения B-абоненту                      |
| record_call      | boolean | признак записи разговора. `True`, если разговор записывается. `False`, если разговор не записывается |
| uid              | uint64  | уникальный идентификатор вызова. Одинаковый во всех событиях и запросах в рамках одного вызова       |
| cause_code       | string  | код причины разъединения звонка (Q.850)                                                              |
| application_uuid | string  | уникальный идентификатор приложения, через которое проходит вызов                                    |
| customer_id      | uint64  | уникальный идентификатор пользователя                                                                |
| direction        | string  | направление звонка - outbound (исходящий)                                                            |
| display_number   | string  | номер, который видит B-абонент                                                                       |

#### Пример

```json
{
	"service": "sip",
	"date_time": "2024-01-05T11:09:42.885372Z",
	"number_a": "79991112233",
	"number_b": "79994445566",
	"call_sid": "call-test-12345",
	"type": "d",
	"sip_id": "883140123456789",
	"setup_time": 800,
	"wait_time": 800,
	"duration": 4279,
	"full_duration": 13820,
	"record_call": true,
	"uid": 12345678910,
	"cause_code": "16",
	"application_uuid": "178ec145-6898-4b06-a92a-75f63cb57046",
	"customer_id": 1111,
	"direction": "outbound",
	"display_number": "79991112233"
}
```

### End

Окончание вызова.

| Параметр         |   Тип   | Описание                                                                                             |
| ---------------- | :-----: | ---------------------------------------------------------------------------------------------------- |
| service          | string  | сервис для отправки уведомления                                                                      |
| date_time        | string  | дата события в формате [RFC-3339 / ISO-8601](https://datatracker.ietf.org/doc/html/rfc3339)          |
| number_a         | string  | номер A-абонента (определяемый номер Exolve, привязанный к SIP ID)                                   |
| number_b         | string  | номер B-абонент (номер телефона, на который совершён вызов)                                          |
| call_sid         | string  | уникальный идентификатор вызова                                                                      |
| type             | string  | тип уведомления, значение - e                                                                        |
| sip_id           | string  | SIP ID, с которого совершён звонок                                                                   |
| record_call      | boolean | признак записи разговора. `True`, если разговор записывается. `False`, если разговор не записывается |
| uid              | uint64  | уникальный идентификатор вызова. Одинаковый во всех событиях и запросах в рамках одного вызова       |
| application_uuid | string  | уникальный идентификатор приложения, через которое проходит вызов                                    |
| customer_id      | uint64  | уникальный идентификатор пользователя                                                                |
| direction        | string  | направление звонка - outbound (исходящий)                                                            |
| display_number   | string  | номер, который видит B-абонент                                                                       |

#### Пример

```json
{
	"service": "sip",
	"date_time": "2024-01-05T11:09:42.866477Z",
	"number_a": "79991112233",
	"number_b": "79994445566",
	"call_sid": "call-test-12345",
	"type": "e",
	"sip_id": "883140123456789",
	"record_call": true,
	"uid": 12345678910,
	"application_uuid": "178ec145-6898-4b06-a92a-75f63cb57046",
	"customer_id": 1111,
	"direction": "outbound",
	"display_number": "79991112233"
}
```
