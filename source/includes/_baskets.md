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
    "locked": false,
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
          "grossTotal": "8000"
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
locked | boolean | No | Is the basket locked?
offers | object | No | A set of offer data for the basket. This includes the name, ID, conditions of sale and totals.
totals | object | No | The totals for the basket.
created | string | No | Datetime that the basket was created

## Basket Subresources

Path | Methods | Description
---- | ------- | -----------
cancel | PUT | Cancels a basket. Marks the basket as non-current.
submit | PUT | Submits a basket to the salesperson
