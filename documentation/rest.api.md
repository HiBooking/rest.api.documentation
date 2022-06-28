### Основное

* `host` [Получение точки доступа URL API](host.md)
* `token` [Авторизация](auth.md)

### Методы

* Категории
  * [Получить категории](api.method/category/get.md) : `GET <host>/categories/`
  * Квоты
    * [Получить квоты категории номера](api.method/category/quota/get.md) : `GET <host>/categories/:id/quotas/`
    * [Установить квоты категории номера](api.method/category/quota/post.md) : `POST <host>/categories/:id/quotas/`
    * [Удалить квоты категории номера](api.method/category/quota/delete.md) : `DELETE <host>/categories/:id/quotas/`
* Заявки на бронирование
  * [Получить список заявок на бронирование](api.method/booking/get.list.md) : `GET <host>/bookings/`
  * [Получить полную информацию по бронированию](api.method/booking/get.one.md) : `GET <host>/bookings/`
* Дополнительно
  * [Служебный метод](api.method/status.md) : `GET <host>/status/`



