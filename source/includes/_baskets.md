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
    "currencyCode": "GBP",
    "current": true,
    "offers": {
      "OF-000-001": {
        "name": "My offer",
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
        "totals": {
          "net": "£100.00",
          "discount": "£10.00",
          "gross": "£90.00" 
        }
      }
    },
    "totals": {
      "net": "£100.00",
      "discount": "£10.00",
      "gross": "£90.00"
    },
    "created": "2020-04-06T09:36:35.018Z"
  },
  "relationships": {
    "contact": {
      "data": {
        "id":  "/contact/1",
        "type": "Contact"
      }
    }
  }
}
```

> Example POST Request Body

```json
{
  "contact": "/api/contacts/1",
  "offerLines": [
    "/api/offer-lines/1",
    "/api/offer-lines/2",
    "/api/offer-lines/3"
  ]
}
```

Field | Type | Writeable | Description
----- | ---  | --------- | -----------
id | int | No | Unique identifier
currencyCode | string | No | The currency of the basket
current | boolean | No | Is the basket current for the user?
offers | object | No | A set of offer data for the basket. This includes the name, ID, conditions of sale and totals.
totals | object | No | The totals for the basket.
created | string | No | Datetime that the basket was created
contact | string | Yes | The IRI of the contact that a new basket is to belong to
offerLines | array | Yes | List of offer line IRIs that the basket is to be created with

## Basket Relationships

Name | Type | Description
---- | ---- | -----------
contact | One to many | The contact that the basket is with

## Basket Subresources

`/cancel`
`/accept`
