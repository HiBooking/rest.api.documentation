**Категории номера**
----
Метод позволяет получить список категорий номеров

**URL:** `/categories/`

**HTTP метод:** `GET` 

**Параметры запроса:**

| Название        | Тип      | Значения  | Обязательный | Описание                                                         |
|-----------------|----------|-----------|--------------|------------------------------------------------------------------|
| page            | `Int`    | от 1 до N | нет          | Номер страницы при постраничной навигации _(по умолчанию 1)_     |
| size            | `Int`    | от 1 до N | нет          | Размер страницы при постраничной навигации _(по умолчанию 15)_   |
| filter[active]   | `String` | Y или N   | нет          | Позволяет выбрать категории по значению активности        _      |

<br />

**Успешный ответ: `Code: 200`** <br />  
[Общие параметры ответа](../main.response.md) <br /> 
Описание полей ответа метода: `message -> data`


| Название         | Тип      | Значения  | Описание                                                 |
|------------------|----------|-----------|----------------------------------------------------------|
| id               | `Int`    | от 1 до N | числовой идентификатор                                   |
| active           | `String` | Y или N   | флаг активности                                          |
| name             | `String` |           | название категории ("ru", "en" ... переводы)             |
| shortName        | `String` |           | сокращенное название категории ("ru", "en" ... переводы) |



Пример:

    {
        "code": 200,
        "status": "success",
        "message": {
            "data": [
                {
                    "id": 9000,
                    "active": "Y",
                    "name": {
                        "ru": "Категория класса Люкс",
                        "en": "",
                        "de": ""
                    },
                    "shortName": {
                        "ru": "Люкс",
                        "en": "",
                        "de": ""
                    }
                },
                ...
            ]
        },
        "pagination": {
            "countPage": 2,
            "sizePage": 15,
            "currentPage": 1,
            "nextPage": 2,
            "prevPage": null,
            "totalCount": 16
        }
    }


**Ответ с ошибкой:**

  <_Most endpoints will have many ways they can fail. From unauthorized access, to wrongful parameters etc. All of those should be liste d here. It might seem repetitive, but it helps prevent assumptions from being made where they should be._>

    * **Code:** 401 UNAUTHORIZED <br />
      **Content:** `{ error : "Log in" }`

  OR

    * **Code:** 422 UNPROCESSABLE ENTRY <br />
      **Content:** `{ error : "Email Invalid" }`

* **Sample Call:**

  <_Just a sample call to your endpoint in a runnable format ($.ajax call or a curl request) - this makes life easier and more predictable._>

* **Notes:**

  <_This is where all uncertainties, commentary, discussion etc. can go. I recommend timestamping and identifying oneself when leaving comments here._> 