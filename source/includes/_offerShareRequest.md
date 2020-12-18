# Offer Share Requests

> Path

```
/offer-share-requests(/{id})
```

Requests to share an offer from customers.

## Offer Share Requests Available Verbs

* GET
* POST

## Offer Share Requests Fields

> Example Entity Response

```json
{
  "id": "/api/offer-share-requests/1",
  "type": "OfferShareRequest",
  "attributes": {
    "id": 1,
    "offer": "/api/offers/1",
    "contact": "/api/contacts/2",
    "emailList": ["email@customer.com"],
    "message": "Please enjoy this offer",
    "status": "pending",
    "created": "2020-04-06T09:36:35.018Z",
    "updated": "2020-04-06T09:36:35.018Z"            
  }
}
```

> Example POST Body

```json
{
  "offer": "/api/offers/1",
  "contact": "/api/contacts/2",
  "emailList": ["email@customer.com"],
  "message": "Please enjoy this offer"
}
```

Field | Type | Writeable | Nullable | Description
----- | ---- | --------- | -------- | -----------
id | int | No | - | Identifier
offer | string | Yes | No | The IRI of the offer that is being shared
contact | string | Yes | No | The IRI of the contact that is sharing the offer
emailList | array | Yes | No | The list of email addresses that the offer is to be shared with
message | string | Yes | No | The message from the customer to be included in the share email
status | string | No | - | The status of the request. Either 'pending' or 'sent'
created | datetime | No | - | Creation datetime of the entity
updated | datetime | No | - | Update datetime of the entity
