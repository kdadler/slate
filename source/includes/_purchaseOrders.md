# Purchase Orders

> Path

```
/purchase-orders
```

Purchases that are at the order stage.

## Purchase Order Available Verbs

* GET

## Purchase Order Fields

> Example Entity Response

```json
{
  "data": {
    "id": "/api/v1/purchase-orders/PO0000001",
    "type": "PurchaseOrder",
    "attributes": {
      "id": "PO0000001",
      "cancellationReason": "Surpless to requirements",
      "companyId": 2,
      "companyName": "PC World",
      "conditionsOfSale": [],
      "contactAddressData": {},
      "contactEmailAddress": "test@test.com",
      "contactName": "Mr Contact",
      "contactPhoneNumber": "0123984578344",
      "countryOfPurchaseCode": "FR",
      "countryOfPurchaseName": "France",
      "created": "2020-04-06T09:36:35.018Z",
      "currencyCode": "GBP",
      "deliveryTermLabel": "Ex Works",
      "discountRate": 0,
      "expectedMonthOfReceipt": 5,
      "goodsReceivedDate": "2020-04-06T09:36:35.018Z",
      "invoiceDate": "2020-04-06T09:36:35.018Z",
      "lineCount": 2,
      "nonZeroLineCount": 2,
      "paymentTermLabel": "20% up front",
      "publishedLineCount": 0,
      "purchaserName": "Jonathan Day",
      "receivedLineCount": 0,
      "reference": "From: From: From: C offer",
      "status": 1,
      "statusLabel": "Place Order",
      "taxRate": 0,
      "totals": {
        "currencyCode": "GBP",
        "buyingTotal": "11753",
        "preTaxPriceAdjustmentTotal": "1154",
        "taxTotal": "0",
        "postTaxPriceAdjustmentTotal": "0",
        "totalWithoutTax": "12907",
        "totalWithTax": "12907"
      },
      "updated": "2020-04-06T09:36:35.018Z"
    },
    "relationships": {
      "purchaser": {
        "data": {
          "type": "User",
          "id": "/api/v1/users/1"
        }
      }
    }
  }
}
```

| Field                  | Type    | Description                                                             |
|------------------------|---------|-------------------------------------------------------------------------|
| id                     | string  | Unique identifier                                                       |
| cancellationReason     | string  | The reason that the order was cancelled, if any                         |
| companyId              | integer | The ID of the company supplying the order                               |
| companyName            | string  | The name of the company supplying the order                             |
| conditionsOfSale       | object  | The conditions associated with the purchase                             |
| contactAddressData     | object  | An array of the contact address data                                    |
| contactEmailAddress    | string  | The contact's email address                                             |
| contactName            | string  | The name of the contact for the order                                   |
| contactPhoneNumber     | string  | The contact's phone number                                              |
| countryOfPurchaseCode  | string  | The ISO code of the country the purchase is being made from             |
| countryOfPurchaseName  | string  | The name of the country the purchase is being made from                 |
| created                | string  | Datetime that the order was created                                     |
| currencyCode           | string  | ISO code of the currency the order has been placed in                   |
| deliveryTermLabel      | string  | The human-readable label of the delivery term for the order             |
| discountRate           | float   | The volume discount applied to the order                                |
| expectedMonthOfReceipt | integer | The month that the order is expected to be received in                  |
| goodsReceivedDate      | string  | Datetime that the goods were received                                   |
| invoiceDate            | string  | Datetime that the invoice was created by the supplier                   |
| lineCount              | integer | The number of lines the order holds                                     |
| nonZeroLineCount       | integer | The number of lines the order holds that have a quantity greater than 0 |
| paymentTermLabel       | string  | The human-readable label of the payment term for the order              |
| publishedLineCount     | integer | The number of lines that have been published for pre-sale               |
| purchaserName          | string  | The name of the purchaser that owns the order                           |
| receivedLineCount      | integer | The number of lines that have been fully received into our warehouse    |
| reference              | string  | The order's reference                                                   |
| status                 | integer | The status of the order within its workflow                             |
| statusLabel            | string  | The human-readable label of the order's status                          |
| taxRate                | float   | The rate of tax applied to the order                                    |
| totals                 | object  | Total value of order                                                    |
| updated                | string  | Datetime that the order was last updated                                |

## Purchase Order Totals Field

The purchase order totals values are always presented in the currency of the order. The object will contain the following
fields:

| Field                       | Type   | Description                                           |
|-----------------------------|--------|-------------------------------------------------------|
| currencyCode                | string | Currency that the totals are in                       |
| buyingTotal                 | string | Total cost of the order                               |
| preTaxPriceAdjustmentTotal  | string | Total value of all price adjustments applied pre-tax  |
| taxTotal                    | string | Total value of the order's tax                        |
| postTaxPriceAdjustmentTotal | string | Total value of all price adjustments applied post-tax |
| totalWithoutTax             | string | Net cost of the order                                 |
| totalWithTax                | string | Gross cost of the order                               |

## Purchase Order Query Parameters

| Filter          | Type   | Match   | Default | Description                                                            |
|-----------------|--------|---------|---------|------------------------------------------------------------------------|
| reference       | string | partial | null    | The order reference to match against                                   |
| contact         | int    | exact   | null    | The ID of the contact that the purchase orders must be associated with |
| contact.company | int    | exact   | null    | The ID of the company that the purchase orders must be associated with |                                                                      
| purchaser       | int    | exact   | null    | The ID of the purchase person that must own the purchase orders        |
| status          | string | exact   | null    | Specify the status of the purchase orders to be returned               |
| order\[created] | string | exact   | asc     | Order the results by created date                                      |
| itemsPerPage    | int    | exact   | 25      | The number of items to return per page                                 |
| page            | int    | exact   | 1       | The page of results to return                                          |

## Purchase Order Statuses

| Label               | Token | Description                                                       |
|---------------------|-------|-------------------------------------------------------------------|
| Place Order         | 1     | The order has been created and is being worked on                 |
| Confirm Order       | 2     | The order has been confirmed by the supplier                      |
| Arrange Shipping    | 3     | Shipping is being arranged for the order's stock                  |
| Product Data Review | 4     | The product information associated with the order is under review |
| Receive Goods       | 5     | Stock is being received into our warehouse                        |
| Receive Invoice     | 6     | An invoice has been received from the supplier                    |
| Complete            | 7     | All stock is received and the invoice paid                        |
| Cancelled           | 8     | The order is no longer required                                   |
