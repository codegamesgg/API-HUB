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


# CodeGames.gg integration

## Sign in
`/api/v1/auth/sign-in`

### Input
HTTP Method: `POST`

Body:

| Parameter  |  Type  | Description   |
|------------|:------:|---------------|
| `login`    | string | User login    |
| `password` | string | User password |

#### Example request:

```json
{
  "login": "cc_user",
  "password": "strong_password"
}
```

### Output
HTTP Status: `200`

Body:

| Parameter |  Type  | Description         |
|-----------|:------:|---------------------|
| `token`   | string | Authorisation token |

#### Example response:

```json
{
  "token": "##I##.#LOVE#.###GAMES###"
}
```

### Errors
| Code                  | Description                 |
|-----------------------|-----------------------------|
| `INVALID_CREDENTIALS` | Incorrect login or password |
| `USER_NOT_FOUND`      | User not found              |

## Get product offer
`/api/v1/partner/product-offers/check`

### Input
HTTP Method: `POST`

Body:

| Parameter  |  Type  | Description      |
|------------|:------:|------------------|
| `id`       | string | Product offer ID |
| `currency` | string | Available: `KZT` |

#### Example request:

```bash
/api/v1/product-offers/partner/562
```

### Output
HTTP Status: `200`

Body:

| Parameter |  Type  | Description             |
|-----------|:------:|-------------------------|
| `count`   | number | Count of product offers |
| `price`   | float  | Price of product offer  |

#### Example response:

```json
{
  "count": 7,
  "price": 956.3
}
```

### Errors
| Code                         | Description                |
|------------------------------|----------------------------|
| `PRODUCT_OFFER_NOT_FOUND`    | Product offer not found    |
| `PRODUCT_OFFER_OUT_OF_STOCK` | Product offer our of stock |

## Pay product offer
`/api/v1/partner/product-offers/pay`

### Input
HTTP Method: `POST`

Body:

| Parameter          |  Type  | Description            |
|--------------------|:------:|------------------------|
| `id`               | string | Product offer ID       |
| `price`            | float  | Price of product offer |
| `currency`         | string | Available: `KZT`       |
| `txnId`            | string | Transaction id         |
| `count` (optional) | number | Product offers count   |

#### Example request:

```json
{
  "id": 562,
  "price": 956.3,
  "txnId": "1700220589699083777",
  "currency": "KZT"
}
```

### Output
HTTP Status: `201`

Body:

| Parameter |  Type  | Description            |
|-----------|:------:|------------------------|
| `orderId` | number | Product offer order id |

#### Example response:

```json
{
  "orderId": 782
}
```

### Errors
| Code                          | Description                         |
|-------------------------------|-------------------------------------|
| `PRODUCT_OFFER_NOT_FOUND`     | Product offer not found             |
| `PRODUCT_OFFER_OUT_OF_STOCK`  | Product offer our of stock          |
| `PRODUCT_OFFER_WRONG_PRICE`   | Product offer wrong price           |
| `PRODUCT_OFFER_TXN_DUPLICATE` | Product offer transaction duplicate |

## Get keys
`/api/v1/partner/product-offers/keys`

### Input
HTTP Method: `POST`

Body:

| Parameter |  Type  | Description            |
|-----------|:------:|------------------------|
| `orderId` | number | Product offer order ID |

#### Example request:

```json
{
  "orderId": 782
}
```

### Output
HTTP Status: `200`

Body:

| Parameter |        Type        | Description                               |
|-----------|:------------------:|-------------------------------------------|
| `keys`    | string or string[] | Can be a single key or an array with keys |

#### Example response:

```json
{
  "keys": "XBBRF-MR09R-NX8V"
}
```

### Errors
| Code                            | Description                   |
|---------------------------------|-------------------------------|
| `PRODUCT_OFFER_ORDER_NOT_FOUND` | Product offer order not found |

