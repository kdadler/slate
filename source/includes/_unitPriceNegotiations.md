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
  "id": "/api/unit-price-negotiations/2",
  "type": "UnitPriceNegotiation",
  "attributes": {
    "id": 2,
    "basketLine": "/api/basket-lines/1",
    "parent": "/api/unit-price-negotiations/1",
    "unitPrice": "1043",
    "status": "pending",
    "comment": "I would like a cheaper price please",
    "customerCreated": false,
    "createdByName": "Helen",
    "created": "2020-04-06T09:36:35.018Z",
    "updated": "2020-04-06T09:36:35.018Z"
  }
}
```

> Example POST Body

```json
{
  "basketLine": "/api/basketLine/1",
  "parent": "/api/basketLine/1",
  "unitPrice": "400",
  "comment": "My comment",
  "customerCreated": true
}
```

Field | Type | Writeable | Nullable | Description
----- | ---- | --------- | -------- | -----------
id | int | No | - | Unique identifier
basketLine | string | Yes | No | IRI of the basket line the negotiation belongs to.
parent | string | Yes | Yes | IRI of the parent unit price negotiation in the negotiation process
unitPrice | string | Yes | No | The unit price that has been requested
status | string | No | - | The status of the request
comment | string | Yes | No | The comment in support of the requested unit price
customerCreated | boolean | Yes | No | Was this created by the customer?
createdByName | string&#124;null | Yes | Yes | The name of the salesPerson that created the entity. If customerCreated is true, this should be null 
created | string | No | - | Datetime that the basket was created 

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
