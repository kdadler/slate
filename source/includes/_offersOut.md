# Offers

> Path

```
/offers-out(/{id})
```

Offers are product availability lists that are sent out to current or prospective customers.

## Available Verbs

* GET

## Fields

> Example Entity Response

```json
{
  "id": "/api/offers-out/1",
  "type": "OfferOut",
  "attributes": {
    "id": 1,
    "name": "My offer out",
    "description": "<p>I am describing the offer</p>",
    "status": "active",
    "discountCriteria": [{"threshold": 10000, "percentage":  5}],
    "conditionsOfSale": {"leadTime": "2 weeks"},
    "expiresOn": "2020-04-06T00:00:00.000Z",
    "created": "2020-04-06T09:36:35.018Z",
    "currencyCode":  "EUR",
    "statusLabel": "Active",
    "productCount": 5,
    "deliveryTermLabel": "Ex-works",
    "pricingTiers": [
        {"id": 1, "lowerThreshold":  0, "upperThreshold": 99, "discountPercentage": 0},
        {"id": 2, "lowerThreshold":  100, "upperThreshold": 239, "discountPercentage": 2},
        {"id": 3, "lowerThreshold":  240, "upperThreshold": null, "discountPercentage": 4}
    ],
    "productColumns": [
      {"id": 1, "label": "Language", "weight":  4}
    ],
    "productSections": [
      {"id": 1, "label": "Fragrance", "weight": 10}
    ]
  },
  "relationships": {
    "offerOutProducts": [
      {"data": {"id":  "/offer-out-products/1", "type": "OfferOutProduct"}},
      {"data": {"id":  "/offer-out-products/2", "type": "OfferOutProduct"}}
    ]
  }
}
```

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

## Index Parameters

Name | Type | Match | Default | Description
---- | ---- | ----- | ------- | -----------
name | string | partial | null | Search against the offer out name
status | string | exact | null | Specify the status of the offers out to be returned
currency | string | exact | null | Specify the currency of the offers out to be returned
order\[created] | string | exact | asc | Order the results by created date

## Subresources

`/offer-out-products`

## Statuses

Token | Label | Description
----- | ----- | -----------
active | Active | The offer is currently active and available to be ordered from
expired | Expired | The offer has passed its expiry date
cancelled | Cancelled | The offer has been cancelled by the sales person 
