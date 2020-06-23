# Offers

> Path

```
/offers
```

Offers are product availability lists that are sent out to current or prospective customers.

## Offer Available Verbs

* GET

## Offer Fields

> Example Entity Response

```json
{
  "id": "/api/offers/OF-000-001",
  "type": "Offer",
  "attributes": {
    "id": "OF-000-001",
    "name": "My offer",
    "description": "<p>I am describing the offer</p>",
    "status": "active",
    "conditionsOfSale": [
      {
        "type": "deliveryTerms",
        "value": "Ex works",
        "weight": 1,
        "label": null
      },
      {
        "type": "leadTime",
        "value": "5 weeks",
        "weight": 2,
        "label": null
      },
      {
        "type": "extraConditionsOfSale",
        "value": "Yes",
        "weight": 3,
        "label": "Take all"
      },
      {
        "type": "volumeDiscount",
        "value": {
          "threshold": 10000,
          "discountPercentage": 5
        },
        "weight": 4,
        "label": null
      }
    ],
    "expiresOn": "2020-04-06T00:00:00.000Z",
    "currencyCode":  "EUR",
    "productCount": 5,
    "pricingTiers": [
        {"id": 1, "lowerThreshold":  0, "upperThreshold": 99, "discountPercentage": 0},
        {"id": 2, "lowerThreshold":  100, "upperThreshold": 239, "discountPercentage": 2},
        {"id": 3, "lowerThreshold":  240, "upperThreshold": null, "discountPercentage": 4}
    ],
    "columns": [
      {"id": 1, "label": "Language", "weight":  4}
    ],
    "sections": [
      {"id": 1, "label": "Fragrance", "weight": 10}
    ],
    "public": false,
    "restricted": false,
    "contactIds": [10, 20, 60],
    "created": "2020-04-06T09:36:35.018Z"
  }
}
```

Field | Type | Description
----- | ---  | -----------
id | string | Unique identifier
name | string | The offer's name 
description | string | HTML description 
status | string | The status token for the offer.
conditionsOfSale | object | The conditions of any sales made from products in this offer. Includes global discount criteria.
expiresOn | string&#124;null | Date of the expiry of the offer. 
currencyCode | string | Code of the currency that the offer is being made in
productCount | int | A count of the number of products in the offer.
pricingTiers | array | The pricing tiers in the offer
columns | array | The columns that are to be displayed on the offer's product table 
sections | array | The sections that products can be displayed in
public | boolean | Is this offer viewable by customers without the need to log in?
restricted | boolean | Is this offer only available to customers listed in the contactIds?
contactIds | array | A list of the contact IDs that are permitted to access the offer.
created | string | Datetime that the offer was created

## Offer Index Parameters

Name | Type | Match | Default | Description
---- | ---- | ----- | ------- | -----------
name | string | partial | null | Search against the offer name
status | string | exact | null | Specify the status of the offers to be returned
public | boolean | exact | null | Filter results by publicly accessible offers
restricted | boolean | exact | null | Filter results by restricted flag
contactId | int | exact | null | Exclude offers that are restricted but not to the specified contact.
order\[created] | string | exact | asc | Order the results by created date
order\[name] | string | exact | asc | Order the results by name

## Offer Statuses

Token | Label | Description
----- | ----- | -----------
new | New | The offer has been created but not yet available to order from
active | Active | The offer is currently active and available to be ordered from
expired | Expired | The offer has passed its expiry date
cancelled | Cancelled | The offer has been cancelled by the sales person
