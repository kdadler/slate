# Sales Negotiation Lines

> Path

```
/sales-negotiation-lines
```

Sales negotiation lines.

## Sales Negotiation Line Available Verbs

* GET

## Sales Negotiation Line Fields

> Example Entity Response

```json
{
  "id": "/api/sales-negotiation-lines/1",
  "type": "SalesOrderLine",
  "attributes": {
    "id": "1",
    "unitPrice": "1055",
    "total": "105500",
    "unitQuantity": 100,
    "ean": "1234567891011",
    "name": "An example product name 500ml"
  },
  "relationships": {}
}
```

Field | Type | Description
----- | ---  | -----------
id | string | Unique identifier
unitPrice | string | The amount that each unit is being sold for, in pence/cents
total | string | The total value of the line, in pence/cents
unitQuantity | int | The quantity of units being supplied
ean | string | The EAN of the product being sold
name | string | The name of the line

## Sales Negotiation Line Index Parameters

Name | Type | Match | Default | Description
---- | ---- | ----- | ------- | -----------
salesNegotiation | string | exact | null | The ID of the sales negotiation the lines must belong to.
order\[name] | string | sort | asc | Sorts the lines by name.
itemsPerPage | int | exact | 25 | The number of items to return per page
page | int | exact | 1 | The page of results to return 
