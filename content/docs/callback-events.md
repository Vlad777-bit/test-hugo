---
title: "Callback Call Events"
weight: 5
description: "Callback Call Events - параметры уведомлений на URL об обратных звонках"
---

## Параметры уведомлений

### Originate

Инициация обратного звонка для одного из абонентов.

Параметр         | Тип              | Описание |
| ------------- |:------------------:| -----|
| service | string | сервис для отправки уведомления |
| date_time | string | дата события в формате [RFC-3339 / ISO-8601](https://datatracker.ietf.org/doc/html/rfc3339) |
| call_sid | string | уникальный идентификатор вызова |
| number | string | номер вызываемого абонента |
| type | string | тип уведомления, значение - o |
| uid | uint64 | уникальный идентификатор вызова. Одинаковый во всех событиях и запросах в рамках одного вызова |
| application_uuid | string | уникальный идентификатор приложения, через которое проходит вызов |
| customer_id | uint64 | уникальный идентификатор пользователя |
| event_side | string | к какому абоненту относится уведомление (A-абонент или B-абонент ) |
| record_call | boolean | признак записи разговора. `True`, если разговор записывается. `False`, если разговор не записывается |

#### Пример

```json
// Инициация звонка с первым абонентом (A-абонент)
{
    "service": "callback",
    "date_time": "2024-01-07T10:54:01.957366Z",
    "call_sid": "call-test-12345",
    "number": "79991112233",
    "type": "o",
    "uid": 12345678910,
    "application_uuid": "178ec145-6898-4b06-a92a-75f63cb57046",
    "customer_id": 1111,
    "event_side": "A",
    "record_call": true,
}

// Инициация звонка со вторым абонентом (B-абонент).
{
    "service": "callback",
    "date_time": "2024-01-07T10:54:13.493309Z",
    "call_sid": "call-test-12345",
    "number": "79994445566",
    "type": "o",
    "uid": 12345678910,
    "application_uuid": "178ec145-6898-4b06-a92a-75f63cb57046",
    "customer_id": 1111,
    "event_side": "B",
    "record_call": true,
}
```

### Start

Фактический ответ одного из абонентов (владелец номера, на который совершается вызов, поднял трубку).

Параметр         | Тип              | Описание |
| ------------- |:------------------:| -----|
| service | string | сервис для отправки уведомления |
| date_time | string | дата события в формате [RFC-3339 / ISO-8601](https://datatracker.ietf.org/doc/html/rfc3339) |
| call_sid | string | уникальный идентификатор вызова |
| number | string | номер вызываемого абонента |
| type | string | тип уведомления, значение - s |
| uid | uint64 | уникальный идентификатор вызова. Одинаковый во всех событиях и запросах в рамках одного вызова |
| application_uuid | string | уникальный идентификатор приложения, через которое проходит вызов |
| customer_id | uint64 | уникальный идентификатор пользователя |
| event_side | string | к какому абоненту относится уведомление (A-абонент или B-абонент ) |
| record_call | boolean | признак записи разговора. `True`, если разговор записывается. `False`, если разговор не записывается |

#### Пример

```json
// Первый абонент (A-абонент) ответил на звонок
{
    "service": "callback",
    "date_time": "2024-01-07T10:54:11.418221Z",
    "call_sid": "call-test-12345",
    "number": "79991112233",
    "type": "s",
    "uid": 12345678910,
    "application_uuid": "178ec145-6898-4b06-a92a-75f63cb57046",
    "customer_id": 1111,
    "event_side": "A",
    "record_call": true,
}

// Второй абонент (B-абонент) ответил на звонок
{
    "service": "callback",
    "date_time": "2024-01-07T10:54:36.548487Z",
    "call_sid": "call-test-12345",
    "number": "79994445566",
    "type": "s",
    "uid": 12345678910,
    "application_uuid": "178ec145-6898-4b06-a92a-75f63cb57046",
    "customer_id": 1111,
    "event_side": "B",
    "record_call": true,
}
```

### Hungup

Разъединение/окончание вызова с одним из абонентов.

Параметр         | Тип              | Описание |
| ------------- |:------------------:| -----|
| service | string | сервис для отправки уведомления |
| date_time | string | дата события в формате [RFC-3339 / ISO-8601](https://datatracker.ietf.org/doc/html/rfc3339) |
| call_sid | string | уникальный идентификатор вызова |
| number | string | номер вызываемого абонента |
| type | string | тип уведомления, значение - h |
| uid | uint64 | уникальный идентификатор вызова. Одинаковый во всех событиях и запросах в рамках одного вызова |
| application_uuid | string | уникальный идентификатор приложения, через которое проходит вызов |
| customer_id | uint64 | уникальный идентификатор пользователя |
| event_side | string | к какому абоненту относится уведомление (A-абонент или B-абонент ) |
| record_call | boolean | признак записи разговора. `True`, если разговор записывается. `False`, если разговор не записывается |

#### Пример

```json
// Первый абонент (A-абонент) ответил на звонок
{
    "service": "callback",
    "date_time": "2024-01-07T10:54:57.002096Z",
    "call_sid": "call-test-12345",
    "number": "79991112233",
    "type": "h",
    "uid": 12345678910,
    "application_uuid": "178ec145-6898-4b06-a92a-75f63cb57046",
    "customer_id": 1111,
    "event_side": "A",
    "record_call": true,
}

// Второй абонент (B-абонент) ответил на звонок
{
    "service": "callback",
    "date_time": "2024-01-07T10:54:57.007305Z",
    "call_sid": "call-test-12345",
    "number": "79994445566",
    "type": "h",
    "uid": 12345678910,
    "application_uuid": "178ec145-6898-4b06-a92a-75f63cb57046",
    "customer_id": 1111,
    "event_side": "B",
    "record_call": true,
}
```

### Definition

Окончание вызова с причиной разъединения с одним из абонентов.

Параметр         | Тип              | Описание |
| ------------- |:------------------:| -----|
| service | string | сервис для отправки уведомления |
| date_time | string | дата события в формате [RFC-3339 / ISO-8601](https://datatracker.ietf.org/doc/html/rfc3339) |
| call_sid | string | уникальный идентификатор вызова |
| number | string | номер вызываемого абонента |
| type | string | тип уведомления, значение - d |
| uid | uint64 | уникальный идентификатор вызова. Одинаковый во всех событиях и запросах в рамках одного вызова |
| application_uuid | string | уникальный идентификатор приложения, через которое проходит вызов |
| customer_id | uint64 | уникальный идентификатор пользователя |
| started | string | дата начала звонка с абонентом [RFC-3339 / ISO-8601](https://datatracker.ietf.org/doc/html/rfc3339) |
| ended | string | дата окончания звонка с абонентом [RFC-3339 / ISO-8601](https://datatracker.ietf.org/doc/html/rfc3339) |
| hangup_cause | string | причина разъединения звонка |
| cause | string | код причины разъединения звонка (Q.850) |
| called_number | string | номер Exolve, на которой совершён вызов |
| calling_number | string | номер Exolve, с которого совершён вызов на номер переадресации |
| setup_time | uint32 | время ожидания A-абонента до соединения с B-абонентом или отбоя |
| wait_time | uint32 | время ожидания A-абонента до фактического ответа B-абонента |
| duration | uint32 | время фактического разговора абонентов в миллисекундах |
| full_duration | uint32 | время разговора в миллисекундах c учетом проигрывания аудиосообщения B-абоненту |
| event_side | string | к какому абоненту относится уведомление (A-абонент или B-абонент ) |
| record_call | boolean | признак записи разговора. `True`, если разговор записывается. `False`, если разговор не записывается |

#### Пример

```json
// Окончание вызова с первым абонентом (A-абонент)
{
  "service": "callback",
  "date_time": "2024-01-07T10:54:57.009979Z",
  "call_sid": "cala188947f-3ba8-4fe6-b291-12fda2f90079",
  "number": "79991112233",
  "type": "d",
  "uid": 7149714791827935000,
  "application_uuid": "178ec145-6898-4b06-a92a-75f63cb57046",
  "customer_id": 25513,
  "started": "2024-01-07T10:54:11.385017Z",
  "ended": "2024-01-07T10:54:56.965018Z",
  "hangup_cause": "NORMAL_CLEARING",
  "cause": "16",
  "calling_number": "78000009988",
  "called_number": "79991112233",
  "setup_time": 10385,
  "wait_time": 10385,
  "duration": 45580,
  "full_duration": 55965,
  "event_side": "A",
  "record_call": true
}

// Окончание вызова со вторым абонентом (B-абонент)
{
  "service": "callback",
  "date_time": "2024-01-07T10:54:57.017228Z",
  "call_sid": "cala188947f-3ba8-4fe6-b291-12fda2f90079",
  "number": "79994445566",
  "type": "d",
  "uid": 7149714791827935000,
  "application_uuid": "178ec145-6898-4b06-a92a-75f63cb57046",
  "customer_id": 25513,
  "started": "2024-01-07T10:54:36.505022Z",
  "ended": "2024-01-07T10:54:56.965018Z",
  "hangup_cause": "NORMAL_CLEARING",
  "cause": "16",
  "calling_number": "78000009988",
  "called_number": "79994445566",
  "setup_time": 35505,
  "wait_time": 35505,
  "duration": 20459,
  "full_duration": 55965,
  "event_side": "B",
  "record_call": true
}
```

### End

Окончание вызова с одним из абонентов.

Параметр         | Тип              | Описание |
| ------------- |:------------------:| -----|
| service | string | сервис для отправки уведомления |
| date_time | string | дата события в формате [RFC-3339 / ISO-8601](https://datatracker.ietf.org/doc/html/rfc3339) |
| call_sid | string | уникальный идентификатор вызова |
| number | string | номер вызываемого абонента |
| type | string | тип уведомления, значение - e |
| uid | uint64 | уникальный идентификатор вызова. Одинаковый во всех событиях и запросах в рамках одного вызова |
| application_uuid | string | уникальный идентификатор приложения, через которое проходит вызов |
| customer_id | uint64 | уникальный идентификатор пользователя |
| event_side | string | к какому абоненту относится уведомление (A-абонент или B-абонент ) |
| record_call | boolean | признак записи разговора. `True`, если разговор записывается. `False`, если разговор не записывается |

#### Пример

```json
// Окончание вызова с первым абонентом (A-абонент)
{
    "service": "callback",
    "date_time": "2024-01-07T10:54:57.007305Z",
    "call_sid": "call-test-12345",
    "number": "79991112233",
    "type": "e",
    "uid": 12345678910,
    "application_uuid": "178ec145-6898-4b06-a92a-75f63cb57046",
    "customer_id": 1111,
    "event_side": "A",
    "record_call": true,
}

// Окончание вызова с первым абонентом (A-абонент)
{
    "service": "callback",
    "date_time": "2024-01-07T10:54:57.007305Z",
    "call_sid": "call-test-12345",
    "number": "79994445566",
    "type": "e",
    "uid": 12345678910,
    "application_uuid": "178ec145-6898-4b06-a92a-75f63cb57046",
    "customer_id": 1111,
    "event_side": "B",
    "record_call": true,
}
```
