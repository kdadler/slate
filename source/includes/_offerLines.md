# Offer Lines

> Path

```
/offer-lines
```

The lines associated with an offer.

## Offer Line Available Verbs

* GET

## Offer Line Fields

> Example Entity Response

```json
{
  "id": "/api/offer-lines/1",
  "type": "OfferLine",
  "attributes": {
    "id": 1,
    "offer": "/api/offers/1",
    "ean": "1234567891011",
    "name": "Example Shampoo 250ml",
    "brand": "Elemis",
    "language": "EN",
    "cartonQuantity": 12,
    "baseUnitPrice": {"value": "1055"},
    "unitPriceList": {"1": "1055", "2": "1050", "3": "1043"},
    "new": false,
    "promoted": true,
    "promotedLabel": "Favourite",
    "columnValues": [
      {
        "productColumnId": 5,
        "type": "stockCount",
        "label": "Stock Count",
        "weight": 0,
        "value": "210"
      },
      {
        "productColumnId": 8,
        "type": "custom",
        "label": "A Custom Value",
        "weight": 1,
        "value": "Row item"
      }
    ],
    "unitsPerCase": 15,
    "sectionId": 1
  }
}
```

Field | Type | Description
----- | ---  | -----------
id | int | Unique identifier
offer | string | IRI of the offer that the line is associated with.
ean | string | The EAN for the line
name | string | The line's name
brand | string&#124;null | The name of the line's brand
language | string&#124;null | The line's language
cartonQuantity | string&#124;null | The quantity of units in a carton for the line
baseUnitPrice | object | The base unit price value of the line
unitPriceList | object | The unit price list, keyed by pricing tier ID (see offer out pricingTiers field)
new | boolean | Is this line marked as new?
promoted | boolean | Is this line marked as promoted?
promotedLabel | boolean&#124;null | Label to display for promoted lines
columnValues | object | The values for each column, keyed by column ID (see the offer columns field)
unitsPerCase | int | The number of units per case for the line
sectionId | integer/null | The section that the line belongs to

## Offer Line Index Parameters

Name | Type | Match | Default | Description
---- | ---- | ----- | ------- | -----------
offer | int | exact | null | Specify the ID of the offer the line must belong to
order\[name] | string | exact | asc | Order the results by line name
