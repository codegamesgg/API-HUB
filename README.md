ODE GAMES API-HUB
CodeGames.gg is a global provider of gaming services in the B2C & B2B sectors.

Key products and services:

Gift Cards: A wide selection of gift cards for the most popular gaming platforms and services. Steam Billing System: Integration with Steam allows users to easily top up their accounts. Mobile Games UID and Gift Cards: Services for instant account top-up in mobile games, enabling fast and secure increase of the gaming balance.

To start working with our platform, you need to go through a connection procedure during which you will be provided with all necessary data for authentication and system access. Contact for communication and onboarding:

If you have any questions or need assistance during the registration process, you can contact us via email at: info@codegames.gg  , or telegram @igoryan34


# CodeGames integration

## Get product offer
`/api/v1/offers/find-one`

HTTP Method: `POST`

#### Example request:

```json
{
  "offerId": 2061
}
```

#### Example response with gift card:

```json
{
  "offerId": 2061,
  "productName": "PUBG",
  "offerName": "60 UC",
  "price": 674.47,
  "currency": "KZT",
  "isReturnDataForCustomer": true
}
```

#### Example response without gift card:

```json
{
  "offerId": 2061,
  "productName": "PUBG",
  "offerName": "60 UC",
  "price": 674.47,
  "currency": "KZT",
  "isReturnDataForCustomer": false,
  "required": [
    "gameUserId"
  ]
}
```

## Create order
`/api/v1/offers/create-order`

HTTP Method: `POST`

#### Example request with gift card:

```json
{
  "offerId": 2061,
  "price": 674.47,
  "transactionId": "112321124214"
}
```

#### Example request without gift card:

```json
{
  "offerId": 2061,
  "price": 674.47,
  "transactionId": "112321124214",
  "customer": {
    "gameUserId": "52357322414"
  }
}
```

#### Example response with gift card:

```json
{
  "orderId": 10502,
  "price": 674.47,
  "currency": "KZT",
  "offerId": 2061,
  "productName": "PUBG",
  "offerName": "60 UC",
  "status": "COMPLETED",
  "key": "001434249936",
  "isReturnDataForCustomer": true
}
```

If the status is COMPLETED, the key will be returned immediately. If the status is PROCESSING, the key is not present in the body.

#### Example response with PROCESSING status and gift card:
```json
{
  "orderId": 10502,
  "count": 1,
  "price": 674.47,
  "currency": "KZT",
  "offerId": 2061,
  "productName": "PUBG",
  "offerName": "60 UC",
  "status": "PROCESSING",
  "isReturnDataForCustomer": true
}
```

#### Example response without gift card:

```json
{
  "orderId": 10502,
  "price": 674.47,
  "currency": "KZT",
  "offerId": 2061,
  "productName": "PUBG",
  "offerName": "60 UC",
  "status": "COMPLETED",
  "key": "001434249936",
  "isReturnDataForCustomer": false
}
```

If `isReturnDataForCustomer` is false, there is no need to query for `offers/keys` as it will return an error.

## Check order status
`/api/v1/offers/order-status`

HTTP Method: `POST`

#### Example request:

```json
{
  "orderId": 10502
}
```

#### Example response:

```json
{
  "status": "PROCESSING",
  "isReturnDataForCustomer": true
}
```

**The following are the possible order statuses:**

* PROCESSING: The order is being processed. Please wait a while for the keys to be ready.
* COMPLETED: The order has been processed. The keys are ready and can be picked up.
* CANCELED | REFUND: The order has been cancelled. Keys will not be provided.

## Get keys
`/api/v1/offers/keys`

HTTP Method: `POST`

If `isReturnDataForCustomer` was false, the query will return an error.

#### Example request:

```json
{
  "orderId": 10502
}
```

#### Example response:

```json
{
  "key": "001434249936"
}
```
