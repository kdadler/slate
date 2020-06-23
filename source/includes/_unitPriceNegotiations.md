# Unit Price Negotiation

> Path

```
/unit-price-negotiation(/{id})
```

Per line unit price negotiations for baskets.

## Unit Price Negotiation Available Verbs

* GET
* POST

## Unit Price Negotiation Fields

> Example Response Body

```json
{
  "id": "/api/unit-price-negotiations/1",
  "type": "UnitPriceNegotiation",
  "attributes": {
    "id": 1,
    "unitPrice": "1043",
    "status": "pending",
    "comment": "I would like a cheaper price please",
    "customerCreated": false,
    "created": "2020-04-06T09:36:35.018Z"
  },
  "relationships": {
    "basketLine": {
      "data": {
        "id":  "/api/basket-lines/1",
        "type": "BasketLine"
      }
    },
    "parent": {
      "data": {
        "id":  "/api/unit-price-negotiations/1",
        "type": "UnitPriceNegotiation"
      }
    }
  }
}
```

> Example POST Body

```json
{
  "basketLine": "/api/basketLine/1",
  "unitPrice": "400",
  "comment": "My comment",
  "customerCreated": true
}
```

Field | Type | Writeable | Description
----- | ---- | --------- | -----------
id | int | No | Unique identifier
unitPrice | string | Yes | The unit price that has been requested
status | string | No | The status of the request
comment | string | Yes | The comment in support of the requested unit price
customerCreated | boolean | Yes | Was this created by the customer?
createdByName | string&#124;null | No | The name of the salesPerson that created the entity. If customerCreated is true, this will be null 
created | string | No | Datetime that the basket was created 

## Unit Price Negotiation Relationships

Name | Type | Description
---- | ---- | -----------
basketLine | One to many | The basket line the negotiation belongs to
parent | One to many | The parent unit price negotiation in the negotiation process.

## Unit Price Negotiation Index Parameters

Name | Type | Match | Default | Description
---- | ---- | ----- | ------- | -----------
basket | int | exact | null | Specify the basket the unit price negotiation must belong to
order\[created] | string | exact | asc | Order the results by creation date

## Statuses

Token | Description
----- | -----------
pending | The negotiation has been created and is pending a response
approved | The negotiation is approved by the salesperson
declined | The negotiation has been declined without a counter offer
countered | The negotiation has been superseded by another unit price negotiation
