# Sales Orders

> Path

```
/sales-orders(/{id})
```

Orders that are currently being processed, or have been completed.

## Sales Order Available Verbs



* GET

## Sales Order Fields

> Example Entity Response

```json
{
  "id": "/api/sales-orders/SO0000001",
  "type": "SalesOrder",
  "attributes": {
    "id": "SO0000001",
    "created": "2020-04-06T09:36:35.018Z",
    "status": 60,
    "conditionsOfSale": {"leadTime": "2 weeks"},
    "taxRate": 20,
    "cancellationReason": null,
    "paymentTermLabel": "Pro Forma",
    "deliveryTermLabel": "Ex-works",
    "invoiceId": "IN-92384972",
    "invoiceDate": "2020-04-06T09:36:35.018Z",
    "paymentDate": null
  }
}
```

Field | Type | Description
----- | ---  | -----------
id | string | Unique identifier
created | string | Datetime that the sales order was created
status | int | The status of the order
conditionsOfSale | object | The conditions of sale for the order
taxRate | int | The tax rate applied to the order
cancellationReason | string/null | The reason for the cancellation of the order
paymentTermLabel | string | The label of the payment term
deliveryTermLabel | string | The label of the delivery term
invoiceId | string/null | The ID of the order's invoice
invoiceDate | string/null | The date of the creation of the invoice
paymentDate | string/null | The date of the payment of the invoice

## Sales Order Index Parameters

Name | Type | Match | Default | Description
---- | ---- | ----- | ------- | -----------
contact | string | exact | null | The contact that the sales order must be associated with
status | string | exact | null | Specify the status of the sales orders to be returned
order\[created] | string | exact | asc | Order the results by created date

## Sales Order Subresources

`/product_prices`
`/calculated-values`

## Sales Order Statuses

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
