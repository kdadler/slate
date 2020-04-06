# Baskets (Negotiations)

Negotiation is the backend terminology to be used for baskets. It is expected that Basket will be used in all places
in the Portal except when directly making contact with Yoda.

## Available verbs

> Path

```
/negotiations(/{id})
```

* GET
* POST

## Fields

> Example Response Body

```json
{
  "id": "/api/negotiations/1",
  "type": "Negotiation",
  "attributes": {
    "id": 1,
    "currency": "GBP",
    "conditionsOfSale": {"1": {"leadTime": "2 weeks"}},
    "discountCriteria": {"1": [{"threshold": 10000, "percentage":  5}]},
    "cancellationReason": null,
    "status": "active",
    "created": "2020-04-06T09:36:35.018Z",
    "statusLabel": "Active",
    "productCount": 12
  },
  "relationships": {
    "contact": {"data": {"id":  "/contact/1", "type": "Contact"}}
  }
}
```

> Example POST Request Body

```json
{
  "contact": "/api/contact/1",
  "sourceOfferOutProducts": [
    "/api/offer-out-products/1",
    "/api/offer-out-products/2",
    "/api/offer-out-products/3"
  ]
}
```

Field | Type | Writeable | Description
----- | ---  | --------- | -----------
id | int | No | Unique identifier
currency | string | No | The currency offer the negotiation
conditionsOfSale | object | No | The conditions of sale for the negotiation, keyed by offer out ID
discountCriteria | object | No | The discount criteria for the negotiation, keyed by offer out ID
cancellationReason | string/null | No | The reason for the cancellation of the negotiation
status | string | No | The current status of the negotiation
created | string | No | Datetime that the negotiation was created
statusLabel | string | No | The human-readable status label
productCount | int | No | The number of products in the negotiation
contact | string | Yes | The IRI of the contact that a new negotiation is to belong to
sourceOfferOutProducts | array | Yes | List of offer out product IRIs that the negotiation is to be created with

## Relationships

Name | Type | Description
---- | ---- | -----------
contact | One to many | The contact that the negotiation is with

## Subresources

`/cancel`
`/accept`

## Statuses

Token | Label | Description
----- | ----- | -----------
active | Active | The negotiation is currently active
cancelled | Cancelled | The negotiation has been cancelled 
completed | Completed | The negotiation has been accepted and converted into a sales order 
