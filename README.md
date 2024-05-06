# CODE GAMES API-HUB
CodeGames.gg is a global provider of gaming services in the B2C & B2B sectors.

Key products and services:

Gift Cards: A wide selection of gift cards for the most popular gaming platforms and services. Steam Billing System: Integration with Steam allows users to easily top up their accounts. Mobile Games UID and Gift Cards: Services for instant account top-up in mobile games, enabling fast and secure increase of the gaming balance.

To start working with our platform, you need to go through a connection procedure during which you will be provided with all necessary data for authentication and system access. Contact for communication and onboarding:

If you have any questions or need assistance during the registration process, you can contact us via email at: info@codegames.gg


# CodeGames integration

## Get product offer
`/api/v1/partner/product-offer/check`

### Input
HTTP Method: `POST`

Body:

| Parameter |  Type  | Description      |
|-----------|:------:|------------------|
| `offerId` | number | Product offer ID |

#### Example request:

```json
{
  "offerId": 2
}
```
### Output
HTTP Status: `200`

Body:

| Parameter  |  Type  | Description             |
|------------|:------:|-------------------------|
| `offerId`  | number | Product offer ID        |
| `name`     | string | Product offer name      |
| `count`    | number | Count of product offers |
| `price`    | float  | Price of product offer  |
| `currency` | string | EUR                     |

#### Example response:

```json
{
  "offerId": 2,
  "name": "Steam Gift Card $5 Global Activation Code",
  "count": 521,
  "price": 6.47,
  "currency": "EUR"
}
```

## Pay product offer
`/api/v1/partner/product-offer/buy`

### Input
HTTP Method: `POST`

Body:

| Parameter          |  Type  | Description            |
|--------------------|:------:|------------------------|
| `offerId`          | number | Product offer ID       |
| `price`            | float  | Price of product offer |
| `transactionId`    | string | Your transaction id    |

#### Example request:

```json
{
  "offerId": 2,
  "price": 6.47,
  "transactionId": "112321124214"
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
  "orderId": 4
}
```

## Get keys
`/api/v1/partner/product-offer/keys`

### Input
HTTP Method: `POST`

Body:

| Parameter |  Type  | Description            |
|-----------|:------:|------------------------|
| `orderId` | number | Product offer order ID |

#### Example request:

```json
{
  "orderId": 4
}
```

### Output
HTTP Status: `200`

Body:

| Parameter |  Type  | Description |
|-----------|:------:|-------------|
| `key`     | string | Product key |

#### Example response:

```json
{
  "key": "XBBRF-MR09R-NX8V"
}
```

