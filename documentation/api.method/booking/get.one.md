**Заявки на бронирования**
----------------------------------------------------------

> Метод позволяет получить полную информацию по заявке

**URL:** `/bookings/:id/`

**HTTP метод:** `GET`

**Параметры запроса:**


| Название | Тип   | Значения  | Обязательный | Описание                      |
|----------|-------|-----------|--------------|-------------------------------|
| :id      | `Int` | от 1 до N | да           | числовой идентификатор заявки |

<br />

**Успешный ответ: `Code: 200`**

[Общие параметры ответа](../main.response.md)

Описание полей ответа метода: `message -> data`


| Название                | Тип        | Значения  | Описание                     |
|-------------------------|------------|-----------|------------------------------|
| id                      | `Int`      | от 1 до N | числовой идентификатор       |
| number                  | `String`   |           | номер заявки в системе       |
| status                  | `String`   |           | символьный код статуса       |
| dateCreate              | `DateTime` |           | дата и время создания заявки |
| dateFrom                | `DateTime` |           | дата начала пребывания       |
| dateTo                  | `DateTime` |           | дата окончания пребывания    |
| dayCount                | `Int`      | от 1 до N | кол-во дней                  |
| guestCount              | `Int`      | от 1 до N | кол-во гостей                |
| roomCount               | `Int`      | от 1 до N | кол-во номеров               |
| totalSum                | `Int`      | от 1 до N | сумма                        |
| totalSumFormat          | `Int`      |           | сумма в формате валюты       |
| currencyCode            | `String`   |           | символьный код валюты        |
| voucherUrl              | `String`   |           | ваучер в формате pdf         |
| comment                 | `String`   |           | комментарий клиента          |
| [userPayer](#userPayer) | `Object`   |           | информация о плательщике     |
| [rooms](#rooms)         | `Object`   |           | информация о номерах         |

<br />

##### <a name="userPayer"></a>Описание объекта `userPayer`


| Название | Тип   | Описание            |
| ------------------ | ---------- | ----------------------------- |
| name             | `String` | имя                      |
| lastName         | `String` | фамилия              |
| secondName       | `String` | отчество            |
| fullName         | `String` | полное имя         |
| phone            | `String` | номер телефона |
| email            | `String` | e-mail                      |

<br />

##### <a name="rooms"></a>Описание объекта `rooms`


| Название           | Тип   | Описание                                                                                                                                |
|--------------------| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| categoryId         | `Int`    | числовой идентификатор категории                                                                                  |
| totalSum           | `String` | сумма за номер                                                                                                                      |
| accommodationSum   | `String` | сумма проживания                                                                                                                 |
| serviceSum         | `String` | сумма за дополнительные услуги                                                                                       |
| foodSum            | `String` | сумма за питание                                                                                                                  |
| foodServicesSum    | `String` | сумма за питание как дополнительные услуги                                                                 |
| guestTypeCountInfo | `Object` | информация по типу и кол-ву гостей<br />  `adult`- кол-во взрослых <br />  `child` - вол детей |
| [places](#places)        | `Object` | информация по занятым местам                                                                                           |

<br />

##### <a name="places"></a>Описание объекта `places`


| Название                | Тип      | Описание                                                               |
|-------------------------|----------|------------------------------------------------------------------------|
| type                    | `String` | тип места<br /> `main` - основное <br /> `additional` - дополнительное |
| typeNumber              | `Int`    | порядковый номер                                                       |
| guestType               | `String` | тип гостя<br /> `adult` - взрослый <br /> `child` - ребенок            |
| [userGuest](#userGuest) | `Object` | информация о госте                                                     |

<br />

##### <a name="userGuest"></a>Описание объекта `userGuest`


| Название | Тип   | Описание                                              |
| ------------------ | ---------- | --------------------------------------------------------------- |
| name             | `String` | имя                                                        |
| lastName         | `String` | фамилия                                                |
| secondName       | `String` | отчество                                              |
| fullName         | `String` | полное имя                                           |
| gender           | `String` | пол<br /> `M` - мужской <br /> `F` - женский |
| dateBirtday      | `Date`   | дата рождения                                     |

<br />

_Пример:_

```json
    {
      "code": 200,
      "status": "success",
      "message": {
        "id": 9343,
        "number": "191767-021021",
        "status": "not_confirmed",
        "dateCreate": "2021-10-02T19:22:47+0300",
        "dateFrom": "2021-10-14T07:20:00+0300",
        "dateTo": "2021-10-21T07:20:00+0300",
        "dayCount": 7,
        "guestCount": 9,
        "roomCount": 3,
        "totalSum": 129920,
        "totalSumFormat": "129’920.00 ₽",
        "currencyCode": "RUB",
        "voucherUrl": "<host>/system/pdf/voucher/191767-021021/",
        "comment": "Я хочу что у нас все было очень хорошо!",
        "userPayer": {
          "name": "Василий",
          "lastName": "Иванов",
          "secondName": "Сергеевич",
          "fullName": "Иванов Василий Сергеевич",
          "phone": "89995556644",
          "email": "example@gmail.ru"
        },
        "rooms": [
          {
            "categoryId": 9000,
            "totalSum": 22400,
            "accommodationSum": 16000,
            "serviceSum": 6400,
            "foodSum": 0,
            "foodServicesSum": 0,
            "guestTypeCountInfo": {
              "adult": 1,
              "child": 1
            },
            "places": [
              {
                "type": "main",
                "typeNumber": 1,
                "guestType": "adult",
                "userGuest": {
                  "name": "Василий",
                  "lastName": "Иванов",
                  "secondName": "Сергеевич",
                  "fullName": "Василий Иванов Сергеевич",
                  "gender": "M",
                  "dateBirtday": "1985-01-27"
                }
              },
              {
                "type": "main",
                "typeNumber": 2,
                "guestType": "child",
                "userGuest": {
                  "name": "Алексей",
                  "lastName": "Петров",
                  "secondName": "Сергеевич",
                  "fullName": "Алексей Петров Сергеевич",
                  "gender": "M",
                  "dateBirtday": "1990-01-30"
                }
              }
            ]
          },
          {
            "categoryId": 9009,
            "totalSum": 61120,
            "accommodationSum": 48320,
            "serviceSum": 12800,
            "foodSum": 0,
            "foodServicesSum": 0,
            "guestTypeCountInfo": {
              "adult": 2,
              "child": 2
            },
            "places": [
              {
                "type": "main",
                "typeNumber": 1,
                "guestType": "adult",
                "userGuest": {
                  "name": "Василий",
                  "lastName": "Иванов",
                  "secondName": "Сергеевич",
                  "fullName": "Василий Иванов Сергеевич",
                  "gender": "M",
                  "dateBirtday": "1985-01-27"
                }
              },
              {
                "type": "main",
                "typeNumber": 2,
                "guestType": "adult",
                "userGuest": {
                  "name": "Василий",
                  "lastName": "Иванов",
                  "secondName": "Сергеевич",
                  "fullName": "Василий Иванов Сергеевич",
                  "gender": "F",
                  "dateBirtday": "2001-10-01"
                }
              },
              {
                "type": "additional",
                "typeNumber": 1,
                "guestType": "child",
                "userGuest": {
                  "name": "Василий",
                  "lastName": "Иванов",
                  "secondName": "Сергеевич",
                  "fullName": "Василий Иванов Сергеевич",
                  "gender": "M",
                  "dateBirtday": "1985-01-27"
                }
              },
              {
                "type": "additional",
                "typeNumber": 2,
                "guestType": "child",
                "userGuest": {
                  "name": "Василий",
                  "lastName": "Иванов",
                  "secondName": "Сергеевич",
                  "fullName": "Василий Иванов Сергеевич",
                  "gender": "M",
                  "dateBirtday": "1985-01-27"
                }
              }
            ]
          },
          {
            "categoryId": 9001,
            "totalSum": 46400,
            "accommodationSum": 27200,
            "serviceSum": 19200,
            "foodSum": 0,
            "foodServicesSum": 0,
            "guestTypeCountInfo": {
              "adult": 3,
              "child": 0
            },
            "places": [
              {
                "type": "main",
                "typeNumber": 1,
                "guestType": "adult",
                "userGuest": {
                  "name": "Василий",
                  "lastName": "Иванов",
                  "secondName": "Сергеевич",
                  "fullName": "Василий Иванов Сергеевич",
                  "gender": "M",
                  "dateBirtday": "1985-01-27"
                }
              },
              {
                "type": "main",
                "typeNumber": 2,
                "guestType": "adult",
                "userGuest": {
                  "name": "Василий",
                  "lastName": "Иванов",
                  "secondName": "Сергеевич",
                  "fullName": "Василий Иванов Сергеевич",
                  "gender": "M",
                  "dateBirtday": "1985-01-27"
                }
              },
              {
                "type": "additional",
                "typeNumber": 1,
                "guestType": "adult",
                "userGuest": {
                  "name": "Василий",
                  "lastName": "Иванов",
                  "secondName": "Сергеевич",
                  "fullName": "Василий Иванов Сергеевич",
                  "gender": "M",
                  "dateBirtday": "1985-01-27"
                }
              }
            ]
          }
        ]
      }
    }
```
