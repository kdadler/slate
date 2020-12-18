# Sales Negotiations

> Path

```
/sales-negotiations
```

Sales negotiations that are currently being processed.

## Sales Negotiation Available Verbs

* GET

## Sales Negotiation Fields

> Example Entity Response

```json
{
  "id": "/api/sales-negotiations/1",
  "type": "SalesNegotiationDataContainer",
  "attributes": {
    "id": 1,
    "currencyCode": "GBP",
    "invoiceId": null,
    "invoiceDate": null,
    "reference": "ref001",
    "status": "active",
    "conditionsOfSale": {"leadTime": "2 weeks"},
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
    "created": "2020-04-06T09:36:35.018Z"
  }
}
```

Field | Type | Description
----- | ---  | -----------
id | string | Unique identifier
currencyCode | string | The currency of the sale
invoiceId | null | Always NULL. Included for compatibility with the sales order API format.
invoiceDate | null | Always NULL. Included for compatibility with the sales order API format.
reference | string/null | Custom reference
status | string | The status of the sales negotiation
conditionsOfSale | object | The conditions of sale for the sale
totals | object | Sales negotiation's calculated totals, split into categories (see below)
created | string | Datetime that the sales negotiation was created

## Sales Negotiation Total Fields

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

## Sales Negotiation Index Parameters

Name | Type | Match | Default | Description
---- | ---- | ----- | ------- | -----------
contact | string | exact | null | The contact that the sales negotiation must be associated with
status | string | exact | null | Specify the status of the sales negotiations to be returned
order\[created] | string | exact | asc | Order the results by created date
itemsPerPage | int | exact | 25 | The number of items to return per page
page | int | exact | 1 | The page of results to return

## Sales Negotiation Statuses

Token | Label | Description
----- | ----- | -----------
basket | Basket | The negotiation is being managed by the customer via their basket
active | Active | The account manager is managing the sales negotiation
pending-approval | Pending Approval | Pending customer approval
complete | Complete | The negotiation is complete and a sales order has been created.

## Example request

Example request that will fetch the sales negotiations that are to be displayed to the customer as orders.

```
/api/sales-negotiations?status[]=active&status[]=pending-approval&contact=123&order[created]=desc
```