# Basket Products (Negotiation Products)

This is essentially a join entity between products and negotiations. THe only interaction with this entity is via a
bulk update subresource.

## Available Verbs

> Path

```
/negotiation-products/bulk
```

* POST

## Fields

> Example POST Request Body

```json
[
  {
    "negotiation": "/api/negotiation/1",
    "offerOutProduct": "/api/offer-out-products/1"
  },
  {
    "negotiation": "/api/negotiation/1",
    "offerOutProduct": "/api/offer-out-products/2"
  }
]
```

Field | Type | Writeable | Description
----- | ---  | --------- | -----------
negotiation | string | Yes | IRI of the negotiation that the product is to be added to
offerOutProduct | string | Yes | IRI of the offer out product that is being added.
