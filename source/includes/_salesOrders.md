# Sales Orders

> Path

```
/sales-orders
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
    "currencyCode": "GBP",
    "invoiceId": "IN-92384972",
    "invoiceDate": "2020-04-06T09:36:35.018Z",
    "reference": "ref001",
    "status": "Invoiced",
    "conditionsOfSale": {"leadTime": "2 weeks"},
    "customerConditionsOfSale": [
      { "label": "Delivery Terms", "value": "Ex Works" },
      { "label": "Lead Time", "value": "5 weeks" },
      { "label": "Take All", "value": null },
      { "label": "Volume Discount", "value": "5% at €10,000" }
    ],
    "totals": {
      "sellTotal": "10000",
      "sellTotalBeforeDiscount": "12000",
      "sellDiscountPercent": 4,
      "sellTax": "100",
      "preTaxPriceAdjustment": "200",
      "postTaxPriceAdjustment": "400",
      "adjustedSellTotalWithoutTax": "10000",
      "adjustedSellTotalWithTax": "10000"
    },
    "packingListAvailable": false,
    "invoiceAvailable": true,
    "created": "2020-04-06T09:36:35.018Z"
  }
}
```

Field | Type | Description
----- | ---  | -----------
id | string | Unique identifier
currencyCode | string | The currency of the order
invoiceId | string/null | The ID of the order's invoice
invoiceDate | string/null | The date of the creation of the invoice
reference | string/null | Custom order reference
status | string | The status of the order
conditionsOfSale | object | The conditions of sale for the order
customerConditionsOfSale | array | The above conditions formatted for display to the customer
totals | object | Sales order calculated totals, split into categories (see below)
packingListAvailable | bool | Is the packing list file available to be downloaded?
invoiceAvailable | bool | Is the invoice file available to be downloaded?
created | string | Datetime that the sales order was created

## Sales Order Total Fields

Field | Type | Description
----- | ---- | -----------
sellTotal | string | The product total with the discount applied
sellTotalBeforeDiscount | string | The product total without the discount applied 
sellDiscountPercent | int | The discount percent applied.
sellTax | string | The tax applied
preTaxPriceAdjustment | string | The value of the price adjustments applied pre-tax
postTaxPriceAdjustment | string | The value of the price adjustments applied post-tax
adjustedSellTotalWithoutTax | string | The net total
adjustedSellTotalWithTax | string | The gross total

## Sales Order Conditions of Sale

The customer conditions of sale are returned as an array of objects with label / value keys. The following rules should
be followed when rendering the conditions:

* They should be rendered in the order provided by the API
* If a condition's value is not null and not empty, it should be rendered as `{{ condition.label }} - {{ condition.value }}`
* If a condition's value is null or empty, it should be rendered as `{{ condition.label }}`

## Sales Order Index Parameters

Name | Type | Match | Default | Description
---- | ---- | ----- | ------- | -----------
contact | string | exact | null | The contact that the sales order must be associated with
status | string | exact | null | Specify the status of the sales orders to be returned
order\[created] | string | exact | asc | Order the results by created date
itemsPerPage | int | exact | 25 | The number of items to return per page
page | int | exact | 1 | The page of results to return

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

## Sales Order Subresources

The sales order resource has the following subresources:

Name | Path | Method | Response | Description
---- | ---- | ------ | -------- | -----------
pdf | /api/sales-orders/{id}/pdf | GET | PDF file contents | Fetches the sales order confirmation PDF file 
invoice pdf | /api/sales-orders/{id}/invoice-pdf | GET | PDF file contents | Fetches the sales order's invoice PDF file 
packing list pdf | /api/sales-orders/{id}/packing-list-pdf | GET | PDF file contents | Fetches the sales order packing list PDF file 
