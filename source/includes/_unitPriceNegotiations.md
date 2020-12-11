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
    "statusLabel": "Pending",
    "comment": "I would like a cheaper price please",
    "customerCreated": false,
    "createdByName": "Helen",
    "currencyCode": "EUR",
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
statusLabel | string | No | - | The human-readable label of the request's status. 
comment | string | Yes | No | The comment in support of the requested unit price
customerCreated | boolean | Yes | No | Was this created by the customer?
currencyCode | string | No | - | Currency of the unit price value 
createdByName | string&#124;null | Yes | Yes | The name of the salesPerson that created the entity. If customerCreated is true, this should be null 
created | string | No | - | Datetime that the basket was created 

## Unit Price Negotiation Index Parameters

Name | Type | Match | Default | Description
---- | ---- | ----- | ------- | -----------
basketLine.basket | int | exact | null | Specify the ID of the basket the unit price negotiation must belong to
order\[created] | string | exact | asc | Order the results by creation date
itemsPerPage | int | exact | 25 | The number of items to return per page
page | int | exact | 1 | The page of results to return

## Unit Price Negotiation Statuses

Token | Description
----- | -----------
pending | The negotiation has been created and is pending a response
applied | The negotiation is approved by the salesperson
declined | The negotiation has been declined without a counter offer
countered | The negotiation has been superseded by another unit price negotiation
replaced | The negotiation has been replaced by a newer negotiation.
cancelled | The negotiation has been cancelled by the customer.

## Unit Price Negotiation Subresources

Name | Path | Method | Response | Description
---- | ---- | ------ | -------- | -----------
Replace | /api/unit-price-negotiations/{id}/replace | PUT | Unit price negotiation data | Marks a unit price negotiation as replaced.
Cancel | /api/unit-price-negotiations/{id}/cancel | PUT | Unit price negotiation data | Cancels the unit price negotiation. Only a pending negotiation may be cancelled.
