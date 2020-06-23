# Sales Order Lines

> Path

```
/sales-order-lines(/{id})
```

Sales order lines.

## Sales Order Line Available Verbs

* GET

## Sales Order Line Fields

> Example Entity Response

```json
{
  "id": "/api/sales-order-lines/1",
  "type": "SalesOrderLine",
  "attributes": {
    "id": "1",
    "sellUnitPrice": "1055",
    "unitQuantity": 100,
    "ean": "1234567891011",
    "name": "An example product name 500ml"
  }
}
```

Field | Type | Description
----- | ---  | -----------
id | string | Unique identifier
sellUnitPrice | object | The amount that each unit is being sold for
unitQuantity | int | The quantity of units being supplied 
ean | string | The EAN of the product being sold
name | string | The name of the line

## Sales Order Line Index Parameters

Name | Type | Match | Default | Description
---- | ---- | ----- | ------- | -----------
salesOrder | string | exact | null | The sales order the lines must belong to.
