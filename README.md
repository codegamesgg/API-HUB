# CODE GAMES API-HUB
CodeGames.gg – это глобальный поставщик игровых сервисов в B2C & B2B секторе.

Основные продукты и услуги:

Gift карты: Широкий выбор подарочных карт для самых популярных игровых платформ и сервисов.
Биллинговая система Steam: Интеграция с Steam позволяет пользователям легко пополнять свои аккаунты.
Пополнение мобильных игр UID и Gift Cards: Услуги по мгновенному пополнению аккаунтов в мобильных играх, позволяющие быстро и безопасно увеличивать игровой баланс.

Для начала работы с нашей платформой необходимо пройти процедуру подключения, в ходе которой вам будут предоставлены все необходимые данные для аутентификации и входа в систему.
Контакты для связи и онбординга:

Если у вас возникнут вопросы или вам необходима помощь в процессе регистрации, вы можете связаться с нами через почту:
email: info@codegames.gg




# Интеграция мерчанта в систему CodeGames

Простая оплата через в системе Мерчанта проводится в 2 этапа: проверка данных и оплата, дополнительно может использоваться обработка операции из очереди.



# **1  Получение данных о продукте:**

1\.1 Мерчант отправляет запрос на получение описания и стоимости продукта.

Пример запроса:

```json
POST partner_url/check
{
  "product_id":1234567890
}
```

Описание полей запроса:



| Название | Тип | Обязательное | Описание |
| --- | --- | --- | --- |
| product_id | long | + | идентификатор продукта в системе codegames |


1\.2 CodeGames.gg отправляет ответ, сообщающий системе Мерчанта информацию о продукте подтверждая его доступность либо сообщает об отсутствии продукта.

Примеры ответов:

* успех:

```json
  {
    "status":"OK",
    "comment":"Проверка прошла успешно, продолжайте оплату",
    "product":{
        "id":1234567890,
        "name":"Карта пополнения PSN USA 100 USD",
        "shortDescription":"Kарта оплаты, позволяющая пополнить баланс для американской версии аккаунта Playstation Network (PlayStation US Store) на 100 долларов.",
        "price":50000.0,
        "partner_price":45000.0,
        "addInfo":{}
    }
  }
```

* ошибки:

```json
{
  "status":"PRODUCT_NOT_FOUND",
  "comment":"Продукт не найден"
}
```

```json
{
  "status":"PRODUCT_OUT_OF_STOCK",
  "comment":"Продукт закончился"
}
```

Описание полей ответа:



| Название | Тип | Обязательное | Описание |
| --- | --- | --- | --- |
| status | enum | + если не указан code | статус запроса в системе codegames |
| comment | string |  | комментарий к ответу |
| product | object |  | продукт codegames |


Описание объекта product

| Название | Тип | Обязательное | Описание |
| --- | --- | --- | --- |
| id | long | + | идентификатор продукта в системе codegames |
| name | string | + | наименование товара |
| shortDescription | string |  | короткое описание товара |
| price | double | + | цена для клиента |
| partner_price | double | + | цена для wooppay равная price без комиссии |
| addInfo | object |  | опциональные поля для описания продукта |




# **2 Оплата:**

2\.1 CodeGames.gg отправляет запрос на оплату.

Пример запроса:

```json
POST partner_url/pay
{
   "product_id":1234567890,
   "price":50000.0,
   "txn_id":"1700220589699083777"
}
```

Описание полей запроса:



| Название | Тип | Обязательное | Описание |
| --- | --- | --- | --- |
| product_id | long | + | идентификатор продукта в системе codegames |
| price | double | + | сумма операции |
| txn_id | string | + | идентификатор транзакции в системе Wooppay |



2\.2.1 Успешный сценарий:

* Если ответ успешный, переводим операцию в статус успешной, выдаем чек пользователю
* Если ответ содержит критическую ошибку, операция отменяется, денежные средства возвращаются пользователю


Примеры ответов:

* успех:

```json
{
  "partner_txn_id":"W5345623457426245",
  "status":"OK",
  "comment":"Оплата прошла успешно",
  "product":{
        "id":1234567890,
        "name":"Карта пополнения PSN USA 100 USD",
        "shortDescription":"Kарта оплаты, позволяющая пополнить баланс для американской версии аккаунта Playstation Network (PlayStation US Store) на 100 долларов.",
        "productKey":"FJQR-RGPM-BXLD",
        "addInfo":{}
  }
}
```

* ошибки:

```json
{
  "status":"TXN_DUPLICATE",
  "comment":"Дубликат транзакции"
}
```

```json
{
  "status":"WRONG_PRICE",
  "comment":"Переданная сумма не соответствует цене"
}
```

```json
{
  "status":"PRODUCT_NOT_FOUND",
  "comment":"Продукт не найден"
}
```

```json
{
  "status":"PRODUCT_OUT_OF_STOCK",
  "comment":"Продукт закончился"
}
```

Описание полей ответа:



| Название | Тип | Обязательное | Описание |
| --- | --- | --- | --- |
| partner_txn_id | string | + | идентификатор транзакции в системе codegames |
| status | enum | + | статус запроса в системе codegames |
| comment | string |  | комментарий к ответу |
| product | object |  | продукт codegames |


Описание объекта product

| Название | Тип | Обязательное | Описание |
| --- | --- | --- | --- |
| id | long | + | идентификатор продукта в системе codegames |
| name | string | + | наименование товара |
| shortDescription | string |  | короткое описание товара |
| price | double | + | цена для клиента |
| productKey | string | + | ключ продукта |
| addInfo | object |  | опциональные поля для описания продукта |


2\.2.2 Неуспешный сценарий

Если на запрос оплаты система Мерчанта получила в ответ HTTP status code 5xx или Read timed out или другие ошибки допускающие проведение операции на стороне codegames, система Мерчанта ставит такую операцию в очередь на проверку статуса.

Очередь на проверку статуса транзакции, будет вызывать метод получения статуса транзакции пока не получит ответ, по умолчанию очередь делает 100 попыток с периодом 2 минуты(может быть измененно по согласованию)

* Если ответ успешный, операция переходит в статус успешной в системе Мерчанта.
* Если ответ содержит критическую ошибку, операция отменяется, денежные средства возвращаются клиенту.

```json
 POST partner_url/status
 {
   "txn_id":"1700220589699083777"
 }
```

Описание полей запроса:

| Название | Тип | Обязательное | Описание |
| --- | --- | --- | --- |
| txn_id | string | + | идентификатор транзакции в системе Wooppay |


Примеры ответов:

* успех:

```json
{
  "partner_txn_id":"W5345623457426245",
  "status":"OK",
  "comment":"Оплата прошла успешно"
}
```

* ошибки:

```json
{
  "status":"TXN_NOT_FOUND",
  "comment":"Транзакция не найдена"
}
```

```json
{
  "status":"TXN_CANCELED",
  "comment":"Транзакция отменена"
}
```

| Название | Тип | Обязательное | Описание |
| --- | --- | --- | --- |
| partner_txn_id | string | + | идентификатор транзакции в системе codegames |
| status | enum | + | статус транзакции в системе codegames |
| comment | string |  | комментарий к ответу |
