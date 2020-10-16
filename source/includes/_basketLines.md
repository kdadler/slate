# Basket Lines

> Path

```
/basket-lines
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
    "basket": "/api/baskets/1",
    "offer": "/api/offers/1",
    "offerLine": "/api/offer-lines/1",
    "ean": "1234567891011",
    "name": "An example product name 500ml",
    "brand": "Elemis",
    "language": "EN",
    "cartonQuantity": 12,
    "immutable": false,
    "unitQuantity": 120,
    "availableUnitQuantity": 250,
    "unitsPerCase": 15,
    "baseUnitPrice": "1055",
    "appliedUnitPrice": "1043",
    "total": "10000",
    "created": "2020-04-06T09:36:35.018Z",
    "updated": "2020-04-06T09:36:35.018Z"
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
basket | string | Yes | IRI of the basket the line belongs to
offer | string&#124;null | Yes | IRI of the offer that the product was sourced from.
offerLine | string&#124;null | Yes | IRI of the offer line that the product was sourced from.
ean | string | No | The EAN for the line
name | string | No | The name of the line
brand | string&#124;null | No | The name of the line's brand
language | string&#124;null | The line's language
cartonQuantity | string&#124;null | The quantity of units in a carton for the line
immutable | boolean | No | Can the customer edit this line? If yes, updates/removal will not be permitted.
unitQuantity | int | Yes | The number of units being purchased
availableUnitQuantity | int | No | The available units number
unitsPerCase | int | No | The number of units per case for the line
baseUnitPrice | string | No | The base unit price, before discounts
appliedUnitPrice | string | No | The applied unit price.
total | string | No | The total for the row.
created | string | No | The datetime that the entity was created
updated | string | No | The datetime that the entity was last updated

## Basket Line Index Parameters

Name | Type | Match | Default | Description
---- | ---- | ----- | ------- | -----------
basket | int | exact | null | Specify the basket the line must belong to
order\[name] | string | exact | asc | Order the results by line name

## Basket Line Subresources

Path | Methods | Description
-----|---------|------------
/bulk | POST | Bulk create multiple offer lines. See above for example body content. 
