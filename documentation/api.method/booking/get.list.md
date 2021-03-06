**Заявки на бронирование**
----------------------------------------------

Метод позволяет получить список заявок на бронирование

**URL:** `/bookings/`

**HTTP метод:** `GET`

**Параметры запроса:**


| Название               | Тип        | Значения  | Обязательный | Описание                                                                                                                                                                                                                                                                                                                               |
|------------------------|------------|-----------|--------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| page                   | `Int`      | от 1 до N | нет          | Номер страницы при постраничной навигации _(по умолчанию 1)_                                                                                                                                                                                                                                                                           |
| size                   | `Int`      | от 1 до N | нет          | Размер страницы при постраничной навигации _(по умолчанию 15)_                                                                                                                                                                                                                                                                         |
| filter[number]         | `String`   |           | нет          | Позволяет выбрать заявку по номеру                                                                                                                                                                                                                                                                                                     |
| filter[status]         | `String`   |           | нет          | Позволяет выбрать заявки по статусу<br > `confirmed`- Подтвержденный <br /> `not_confirmed` - Не подтвержденный <br /> `paid` - Оплачена <br /> `paid_in_part` - Оплачена частично <br /> `completed` - Выполнен <br /> `check-in` - Заезд и проживание <br /> `cancel` - Отменена <br /> `payment_expired` - Истёк срок оплаты <br /> |
| filter[dateCreateFrom] | `DateTime` |           | нет          | Дата начала периода в формате ISO8601                                                                                                                                                                                                                                                                                                  |
| filter[dateCreateTo]   | `DateTime` |           | нет          | Дата окончания периода в формате ISO8601                                                                                                                                                                                                                                                                                               |

<br />

**Успешный ответ: `Code: 200`**

[Общие параметры ответа](../main.response.md)

Описание полей ответа метода: `message -> data`


| Название   | Тип        | Значения  | Описание                     |
|------------|------------|-----------|------------------------------|
| id         | `Int`      | от 1 до N | числовой идентификатор       |
| number     | `String`   |           | номер заявки в системе       |
| status     | `String`   |           | символьный код статуса       |
| statusName | `String`   |           | название статуса             |
| dateCreate | `DateTime` |           | дата и время создания заявки |

<br />

_Пример:_

```json
    {
      "code": 200,
      "status": "success",
      "message": {
        "data": [
          {
            "id": 9341,
            "number": "762859-270921",
            "status": "CONFIRMED",
            "statusName": "Подтвержденный",
            "dateCreate": "2021-09-27T20:14:19+0300"
          },
          {
            "id": 9342,
            "number": "767042-270921",
            "status": "CONFIRMED",
            "statusName": "Подтвержденный",
            "dateCreate": "2021-09-27T21:24:02+0300"
          },
          ...
        ],
        "pagination": {
          "countPage": 7,
          "sizePage": 10,
          "currentPage": 1,
          "nextPage": 2,
          "prevPage": null,
          "totalCount": 68
        }
      }
    }
```
