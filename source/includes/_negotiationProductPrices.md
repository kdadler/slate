# Basket Product Prices (Negotiation Product Prices)

## Available Verbs

> Path

```
/negotiation-product-prices(/{id})
```

* GET
* PUT
* DELETE

## Fields

> Example Response Body

```json
{
  "id": "/api/negotiation-product-prices/1",
  "type": "NegotiationProductPrice",
  "attributes": {
    "id": 1,
    "baseUnitPrice": {"value": "1055"},
    "acceptedUnitPrice": {"value": "1043"},
    "unitQuantity": 120,
    "created": "2020-04-06T09:36:35.018Z",
    "updated": "2020-04-06T09:36:35.018Z",
    "ean": "1234567891011",
    "productName": "An example product name 500ml",
    "offerOutId": 1,
    "offerOutName": "My offer out" 
  },
  "relationships": {
    "offerOut": {"data": {"id":  "/offers-out/1", "type": "OfferOut"}}
  }
}
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
baseUnitPrice | object | No | The base unit price for the product
acceptedUnitPrice | object | No | The currently applied unit price for the product line 
unitQuantity | int | Yes | The quantity of units being purchased
created | string | No | The datetime that the product price line was created
updated | string | No | The datetime that the product price line last updated
ean | string | No | The EAN of the product
productName | string | No | The name of the product
offerOutId | string | No | The ID of the associated offer out
offerOutName | string | No | The name of the associated offer out

## Relationships

Name | Type | Description
---- | ---- | -----------
offerOut | One to many | The offer out that the product was sourced from.
