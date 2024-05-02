# CODE GAMES API-HUB
CodeGames.gg is a global provider of gaming services in the B2C & B2B sectors.

Key products and services:

Gift Cards: A wide selection of gift cards for the most popular gaming platforms and services. Steam Billing System: Integration with Steam allows users to easily top up their accounts. Mobile Games UID and Gift Cards: Services for instant account top-up in mobile games, enabling fast and secure increase of the gaming balance.

To start working with our platform, you need to go through a connection procedure during which you will be provided with all necessary data for authentication and system access. Contact for communication and onboarding:

If you have any questions or need assistance during the registration process, you can contact us via email at: info@codegames.gg


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

