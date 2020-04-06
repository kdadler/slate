# Offer Products

## Available verbs

> Path

```
/offer-out-products(/{id})
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
    "productSectionId": 1
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
productColumnValues | object | The values for each column, keyed by product column ID (see offer out productColumns field)
productSectionId | integer/null | The product section that the product belongs to

## Relationships

Name | Type | Description
---- | ---- | -----------
offerOut | One to many | The offer that the product is associated with.

## Index Parameters

Name | Type | Match | Default | Description
---- | ---- | ----- | ------- | -----------
offerOut.id | int | exact | null | Specify the offer out the product must belong to
productReference.productGroup.name | string | partial | null | Search against the product's name
productReference.ean | string | partial | null | Search against the product's ean
currency | string | exact | null | Specify the currency of the offers out to be returned
order\[productReference.productGroup.name] | string | exact | asc | Order the results by product name
