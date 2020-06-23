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
    "ean": "1234567891011",
    "name": "Example Shampoo 250ml",
    "baseUnitPrice": {"value": "1055"},
    "unitPriceList": {"1": "1055", "2": "1050", "3": "1043"},
    "new": false,
    "promoted": true,
    "promotedLabel": "Favourite",
    "columnValues": {"1": "EN"},
    "unitsPerCase": 15,
    "sectionId": 1
  },
  "relationships": {
    "offer": {
      "data": {
        "id":  "/api/offers/1",
        "type": "Offer"
      }
    }
  }
}
```

Field | Type | Description
----- | ---  | -----------
id | int | Unique identifier
ean | string | The EAN for the line
name | string | The line's name
baseUnitPrice | object | The base unit price value of the line
unitPriceList | object | The unit price list, keyed by pricing tier ID (see offer out pricingTiers field)
new | boolean | Is this line marked as new?
promoted | boolean | Is this line marked as promoted?
promotedLabel | boolean&#124;null | Label to display for promoted lines
columnValues | object | The values for each column, keyed by column ID (see the offer columns field)
unitsPerCase | int | The number of units per case for the line
sectionId | integer/null | The section that the line belongs to

## Offer Line Relationships

Name | Type | Description
---- | ---- | -----------
offer | One to many | The offer that the line is associated with.

## Offer Line Index Parameters

Name | Type | Match | Default | Description
---- | ---- | ----- | ------- | -----------
offer | string | exact | null | Specify the offer the line must belong to
order\[name] | string | exact | asc | Order the results by line name
