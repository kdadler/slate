# Offer Products

## Available verbs

> Path

```
/offer-out-products
```

* GET

## Fields

> Example Entity Response

```json
{
  "id": "/api/offers-out-products/1",
  "type": "OfferOutProduct",
  "attributes": {
    "id": 1,
    "baseUnitPrice": {"value": "1055"},
    "new": true,
    "promoted": false,
    "ean": "1234567891011",
    "productName": "Example Shampoo 250ml",
    "unitPriceList": {"1": "1055", "2": "1050", "3": "1043"},
    "productColumnValues": {"1": "EN"},
    "productSectionId": "1"
  },
  "relationships": {
    "offerOut": {"data": {"id":  "/offer-out-products/1", "type": "OfferOutProduct"}}
  }
}
```

Field | Type | Description
----- | ---  | -----------
id | int | Unique identifier
baseUnitPrice | object | The base unit price value of the product
new | boolean | Is this product marked as new?
promoted | boolean | Is this product marked as promoted?
ean | string | The product's EAN
productName | string | The product's name
unitPriceList | object | The unit price list, keyed by pricing tier ID (see offer out pricingTiers field)
productColumnValues
productSectionId


## Relationships

Name | Type | Description
---- | ---- | -----------
offerOutProducts | Many to one | The products associated with the offer

## Statuses

Token | Label | Description
----- | ----- | -----------
active | Active | The offer is currently active and available to be ordered from
expired | Expired | The offer has passed its expiry date
cancelled | Cancelled | The offer has been cancelled by the sales person 

## Index Parameters

Name | Type | Match | Default | Description
---- | ---- | ----- | ------- | -----------
name | string | partial | null | Search against the offer out name
status | string | exact | null | Specify the status of the offers out to be returned
currency | string | exact | null | Specify the currency of the offers out to be returned
order\[created] | string | exact | asc | Order the results by created date

## Subresources

`/offer-out-products`
