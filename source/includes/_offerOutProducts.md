# Offer Products

> Path

```
/offer-out-products
```

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

## Available verbs

* GET

## Fields

Field | Type | Description
----- | ---  | -----------
id | int | Unique identifier
name | string | The offer's name 
description | string | HTML description 
status | string | The status token for the offer
discountCriteria | array | The criteria that must be met for a discount to be applied
conditionsOfSale | object | The conditions of any sales made from products in this offer
expiresOn | ?string | Date of the expiry of the offer. 
created | string | Datetime that the offer was created
currencyCode | string | Code of the currency that the offer is being made in
statusLabel | string | Human-readable version of the status
productCount | int | A count of the number of products in the offer.
deliveryTermLabel | string | The label for the delivery term
pricingTiers | array | The pricing tiers in the offer
productColumns | array | The columns that are to be displayed on the offer's product table 
productSections | array | The sections that products can be displayed in

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
