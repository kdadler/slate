# Sales Order Product Prices

## Available Verbs

> Path

```
/sales-order-product-prices(/{id})
```

* GET

## Fields

> Example Entity Response

```json
{
  "id": "/api/sales-order-product-prices/1",
  "type": "SalesOrderProductPrice",
  "attributes": {
    "id": "SO0000001",
    "sellUnitPrice": {"amount": "1055"},
    "unitQuantity": 100,
    "ean": "1234567891011",
    "productName": "An example product name 500ml"
  }
}
```

Field | Type | Description
----- | ---  | -----------
id | string | Unique identifier
sellUnitPrice | object | The amount that each unit is being sold for
unitQuantity | int | The quantity of units being supplied 
ean | string | The EAN of the product being sold
productName | string | The name of the product being sold

## Index Parameters

Name | Type | Match | Default | Description
---- | ---- | ----- | ------- | -----------

## Statuses

Token | Label | Description
----- | ----- | -----------
10 | Placed | The order has been placed
20 | Supplier Confirmation | The order is awaiting confirmation from the supplier
30 | Customer Confirmation | The order is awaiting confirmation from the customer
40 | Purchase Goods | The order is awaiting the purchase of goods
45 | Ready to Pack | The order is supplied with goods that are awaiting packing
50 | Pack Goods | The order's goods are being packed
60 | Invoice | The order has been invoiced
70 | Complete | The order is complete
80 | Closed Lost | The order has been cancelled
