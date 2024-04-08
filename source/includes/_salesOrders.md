# Sales Orders

> Path

```
/sales-orders
```

Sales that are at the order stage.

## Sales Order Available Verbs

* GET

## Sales Order Fields

> Example Entity Response

```json
{
  "id": "/api/v1/sales-orders/SO0000002",
  "type": "SalesOrder",
  "attributes": {
    "id": "SO0000002",
    "salesNegotiationFormattedId": "SN-000-002",
    "additionalInfo": "...",
    "buyCurrency": "GBP",
    "cancellationReason": "Customer declined order",
    "channelTotals": [],
    "collectionDetailsId": 5,
    "companyName": "PC World",
    "companyId": 2,
    "conditionsOfSale": {
      "minOrderQuantity": 10000,
      "leadTime": "5 Weeks"
    },
    "contactName": "Mr Contact",
    "created": "2020-04-06T09:36:35.018Z",
    "customerConditionsOfSale": [
      {
        "label": "Lead Time",
        "value": "5 Weeks"
      },
      {
        "label": "Min Order Quantity Unit",
        "value": 10000
      }
    ],
    "deliveryTermLabel": "Ex Works",
    "destinationCountry": "Spain",
    "discountCriteria": [],
    "exchangeRate": 1,
    "expectedMonthOfInvoice": 10,
    "invoiceDate": "2020-04-06T09:36:35.018Z",
    "invoiceId": "IN-000-045",
    "packGoodsSkipped": false,
    "paymentDate": "2020-04-06T09:36:35.018Z",
    "paymentTermLabel": "Strictly Proforma",
    "reference": "From: B offer",
    "salesPersonName": "David",
    "sellCurrency": "GBP",
    "status": 40,
    "taxCodeId": 10,
    "taxRate": 20,
    "totals": {
      "sale": {
        "currencyCode": "GBP",
        "buyTotal": "0",
        "sellTotal": "0",
        "difference": "0",
        "sellTotalBeforeDiscount": "0",
        "sellDiscountPercent": 0,
        "sellTax": "0",
        "preTaxPriceAdjustment": "0",
        "postTaxPriceAdjustment": "0",
        "adjustedSellTotalWithoutTax": "0",
        "adjustedSellTotalWithTax": "0",
        "margin": 0
      },
      "purchase": {
        "currencyCode": "GBP",
        "buyTotal": "0",
        "sellTotal": "0",
        "difference": "0",
        "sellTotalBeforeDiscount": "0",
        "sellDiscountPercent": 0,
        "sellTax": "0",
        "preTaxPriceAdjustment": "0",
        "postTaxPriceAdjustment": "0",
        "adjustedSellTotalWithoutTax": "0",
        "adjustedSellTotalWithTax": "0",
        "margin": 0
      },
      "GBP": {
        "currencyCode": "GBP",
        "buyTotal": "0",
        "sellTotal": "0",
        "difference": "0",
        "sellTotalBeforeDiscount": "0",
        "sellDiscountPercent": 0,
        "sellTax": "0",
        "preTaxPriceAdjustment": "0",
        "postTaxPriceAdjustment": "0",
        "adjustedSellTotalWithoutTax": "0",
        "adjustedSellTotalWithTax": "0",
        "margin": 0
      },
      "EUR": {
        "currencyCode": "EUR",
        "buyTotal": "0",
        "sellTotal": "0",
        "difference": "0",
        "sellTotalBeforeDiscount": "0",
        "sellDiscountPercent": 0,
        "sellTax": "0",
        "preTaxPriceAdjustment": "0",
        "postTaxPriceAdjustment": "0",
        "adjustedSellTotalWithoutTax": "0",
        "adjustedSellTotalWithTax": "0",
        "margin": 0
      }
    },
    "updated": "2020-04-06T09:36:35.018Z"
  },
  "relationships": {
    "contact": {
      "data": {
        "id": "/api/v1/contacts/1",
        "type": "Contact"
      }
    },
    "salesPerson": {
      "data": {
        "id": "/api/v1/users/2",
        "type": "User"
      }
    },
    "salesNegotiation": {
      "data": {
        "id": "/api/v1/sales-negotiations/2",
        "type": "SalesNegotiation"
      }
    }
  }
}
```

| Field                       | Type             | Description                                                                            |
|-----------------------------|------------------|----------------------------------------------------------------------------------------|
| id                          | string           | Unique identifier                                                                      |
| salesNegotiationFormattedId | string&#124;null     | The ID of the associated sales negotiation, formatted for display                      |
| additionalInfo              | string           | Additional information that can be included when sending documents for the sales order |
| buyCurrency                 | string           | The currency that goods are expected to be bought in                                   |
| cancellationReason          | string           | The reason that the order was cancelled                                                |
| conditionsOfSale            | array            | The conditions attached to the sale                                                    |
| contactName                 | string           | The name of the contact for the order                                                  |
| companyId                   | integer          | ID of the associated company record                                                    |
| companyName                 | string           | The name of the company for the order                                                  |
| created                     | string           | The datetime of the order's creation                                                   |
| customerConditionsOfSale    | array            | The conditions attached to the sale in a customer-friendly format                      |
| deliveryTermLabel           | string           | The label of the delivery term for the order                                           |
| destinationCountry          | string           | The name of the country that the sale is being made to                                 | 
| discountCriteria            | array            | Criteria that must be met for bulk discounts to be applied                             |
| exchangeRate                | float            | The rate of exchange between the sale and buy currencies                               |
| expectedMonthOfInvoice      | integer          | The month that the order is expected to be fulfilled in                                |
| invoiceDate                 | string           | The date that the order was invoiced                                                   |
| invoiceId                   | string           | The ID of the associated invoice                                                       |
| packGoodsSkipped            | boolean          | Flag: Was the pack goods stage skipped for this order?                                 |
| paymentDate                 | string           | The date that payment was made                                                         |
| paymentTermLabel            | string           | The label of the payment term for the order                                            |
| reference                   | string           | The order's reference                                                                  |
| salesPersonName             | string           | The name of the salesperson that owns the order                                        |
| sellCurrency                | string           | Currency the sale is being made in                                                     |
| status                      | integer          | The status of the order                                                                |
| statusLabel                 | string           | The human readable label of the order's status                                         |
| updated                     | string           | The datetime that the order was last updated                                           |
| taxCodeId                   | integer          | The ID of the associated tax code entity                                               |
| taxRate                     | integer          | The tax rate                                                                           |
| totals                      | array            | The order's total values                                                               |
| contact                     | Contact          | Contact the sale is being made to                                                      |                                                     |
| salesPerson                 | User             | User that owns the sale                                                                |
| salesNegotiation            | SalesNegotiation | The associated sales negotiation entity                                                |

## Sales Order Totals Field

The sales order totals values are broken down into the following currencies:

* `sale`: Totals in the selling currency of the order
* `purchase`: Totals in the buying currency of the order
* `GBP`: Totals in GBP
* `EUR`: Totals in EUR

Within each currency, there will be the following fields:

| Field                       | Type   | Description                                                        |
|-----------------------------|--------|--------------------------------------------------------------------|
| currencyCode                | string | The code of the currency the totals are in                         |
| buyTotal                    | string | The total cost of the order                                        |
| sellTotal                   | string | The total value of the order                                       |
| difference                  | string | The difference between the buying and selling totals               |
| sellTotalBeforeDiscount     | string | The total value of the order before any volume discount is applied |
| sellDiscountPercent         | float  | The percentage volume discount applied                             |
| sellTax                     | string | The amount of tax applied to the order                             |
| preTaxPriceAdjustment       | string | The total value of price adjustments to be applied pre-tax         |
| postTaxPriceAdjustment      | string | The total value of price adjustments to be applied post-tax        |
| adjustedSellTotalWithoutTax | string | The net value of the order                                         |
| adjustedSellTotalWithTax    | string | The gross value of the order                                       |
| margin                      | float  | The margin of the order                                            |

## Sales Order Query Parameters

| Filter                 | Type   | Match   | Default | Description                                                         |
|------------------------|--------|---------|---------|---------------------------------------------------------------------|
| reference              | string | partial | null    | The order reference to match against                                |
| contact                | int    | exact   | null    | The ID of the contact that the sales orders must be associated with |
| contact.company        | int    | exact   | null    | The ID of the company that the sales orders must be associated with |                                                                      
| salesPerson            | int    | exact   | null    | The ID of the sales person that must own the sales orders           |
| status                 | string | exact   | null    | Specify the status of the sales orders to be returned               |
| expectedMonthOfInvoice | string | exact   | null    | Filter by the expected month of invoice field                       |
| order\[created]        | string | exact   | asc     | Order the results by created date                                   |
| itemsPerPage           | int    | exact   | 25      | The number of items to return per page                              |
| page                   | int    | exact   | 1       | The page of results to return                                       |

## Sales Order Statuses

| Label                 | Token | Description                                                                   |
|-----------------------|-------|-------------------------------------------------------------------------------|
| Draft Order           | 10    | The order has been created and is still being worked on                       |
| Supplier Confirmation | 20    | The order is pending confirmation from the supplier                           |
| Customer Confirmation | 30    | The order is pending confirmation from the customer                           |
| Purchase Goods        | 40    | The order is confirmed but cannot be fulfilled from stock                     |
| Available to Pack     | 45    | The order is confirmed and can be fulfilled from stock                        |
| Pack Goods            | 50    | The order's stock is being packed by the warehouse                            |
| Invoice               | 60    | The order has been invoiced. It may still be waiting for dispatch and payment |
| Complete              | 70    | The order has been paid for and the stock dispatched                          |
| Closed Lost           | 80    | The order was closed as no longer required                                    |
| Closed Merged         | 90    | The order was closed as it was merged into another order                      |
