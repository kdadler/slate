# Basket Lines

> Path

```
/basket-lines(/{id})
```

Lines for a basket.

## Basket Line Available Verbs

* GET
* PUT
* POST
* DELETE

## Basket Line Fields

> Example Response Body

```json
{
  "id": "/api/basket-lines/1",
  "type": "BasketLine",
  "attributes": {
    "id": 1,
    "ean": "1234567891011",
    "name": "An example product name 500ml",
    "immutable": false,
    "unitQuantity": 120,
    "availableUnitQuantity": 250,
    "unitsPerCase": 15,
    "baseUnitPrice": "1055",
    "appliedUnitPrice": "1043",
    "created": "2020-04-06T09:36:35.018Z"
  },
  "relationships": {
    "basket": {
      "data": {
        "id":  "/api/baskets/1",
        "type": "Basket"
      }
    },
    "offer": {
      "data": {
        "id":  "/api/offers/1",
        "type": "Offer"
      }
    },
    "offerLine": {
      "data": {
        "id":  "/api/offer-lines/1",
        "type": "OfferLine"
      }
    }
  }
}
```

> Example POST Body

```json
{
  "basket": "/api/baskets/1",
  "offerLine": "/api/offer-lines/1",
  "unitQuantity": 400
}
```
> Example bulk POST Body

```json
[
  {
    "basket": "/api/baskets/1",
    "offerLine": "/api/offer-lines/1",
    "unitQuantity": 400
  },
  {
    "basket": "/api/baskets/1",
    "offerLine": "/api/offer-lines/2",
    "unitQuantity": 300
  }
]
```


> Example PUT Body

```json
{
  "unitQuantity": 400
}
```

Field | Type | Writeable | Description
----- | ---- | --------- | -----------
id | int | No | Unique identifier
ean | string | No | The EAN for the line
name | string | No | The name of the line
immutable | boolean | No | Can the customer edit this line? If yes, updates/removal will not be permitted.
unitQuantity | int | Yes | The number of units being purchased
availableUnitQuantity | int | No | The available units number
unitsPerCase | int | No | The number of units per case for the line
baseUnitPrice | string | No | The base unit price, before discounts
appliedUnitPrice | string | No | The applied unit price.
total | string | No | The total for the row.

## Basket Line Relationships

Name | Type | Description
---- | ---- | -----------
basket | One to many | The basket the line belongs to
offer | One to many | The offer that the product was sourced from.
offerLine | One to many | The offer line that the product was sourced from.

## Basket Line Index Parameters

Name | Type | Match | Default | Description
---- | ---- | ----- | ------- | -----------
basket | int | exact | null | Specify the basket the line must belong to
order\[name] | string | exact | asc | Order the results by line name

## Basket Line Subresources
