# Baskets

> Path

```
/baskets
```

A basket is where users can add products that they are looking to buy, or are in the process of negotiating on. A
contact may only have 1 active basket at any given time.

## Basket Available Verbs

* GET
* POST

## Basket Fields

> Example Response Body

```json
{
  "id": "/api/baskets/1",
  "type": "Basket",
  "attributes": {
    "id": 1,
    "contact": "/api/contact/1",
    "currencyCode": "GBP",
    "current": true,
    "offers": [
      {
        "id": "42",
        "idString": "OF-000-042",
        "name": "My offer",
        "description": "<p>Example description HTML</p>",
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
        "customerConditionsOfSale": [
          { "label": "Delivery Terms", "value": "Ex Works" },
          { "label": "Lead Time", "value": "5 weeks" },
          { "label": "Take All", "value": null },
          { "label": "Volume Discount", "value": "5% at €10,000" }
        ]
      }
    ],
    "totals": {
      "currency": "EUR",
      "lineTotal": "10000",
      "discountedLineTotal": "8000",
      "grossTotal": "8000",
      "offerTotals": [
        {
          "offerId": 42,
          "currency": "EUR",
          "lineTotal": "10000",
          "discountedLineTotal": "8000",
          "discountPercentage": 20,
          "grossTotal": "8000",
          "totalDiscountValue": "2000"
        }
      ]
    },
    "created": "2020-04-06T09:36:35.018Z"
  }
}
```

> Example POST Request Body

```json
{
  "contact": "/api/contacts/1",
  "currencyCode": "EUR"
}
```

Field | Type | Writeable | Description
----- | ---  | --------- | -----------
id | int | No | Unique identifier
contact | string | Yes | The IRI of the contact that a new basket is to belong to
currencyCode | string | Yes | The currency of the basket
current | boolean | No | Is the basket current for the user?
offers | object | No | A set of offer data for the basket. This includes the name, ID, conditions of sale and totals.
totals | object | No | The totals for the basket.
created | string | No | Datetime that the basket was created

## Basket Subresources

Name | Path | Method | Response | Description
---- | ---- | ------ | -------- | -----------
Cancel | /api/basket/{id}/cancel | PUT | Basket data | Cancels a basket. Marks the basket as non-current.
Submit | /api/basket/{id}/submit | PUT | Basket data | Submits a basket to the salesperson.
Export | /api/basket/{id}/export-data | GET | XSLX file contents | Exports a basket to an Excel file. NOTE: This is currently a stub and returns and empty file.
