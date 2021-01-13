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
    "conditionsOfSale": [
      {
        "type": "deliveryTerms",
        "typeLabel": "Delivery Terms",
        "value": "Ex works",
        "weight": 1,
        "label": null
      },
      {
        "type": "leadTime",
        "typeLabel": "Lead Time",
        "value": "5 weeks",
        "weight": 2,
        "label": null
      },
      {
        "type": "extraConditionsOfSale",
        "typeLabel": "Extra Condition",
        "value": "Yes",
        "weight": 3,
        "label": "Take all"
      },
      {
        "type": "volumeDiscount",
        "typeLabel": "Volume Discount",
        "value": {
          "threshold": 10000,
          "discountPercentage": 5
        },
        "weight": 4,
        "label": null
      }
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
    "changes": [
      {
        "field": "currencyCode",
        "action": "changed",
        "from": "GBP",
        "to": "EUR",
        "context": null
      },
      {
        "field": "conditionsOfSale",
        "action": "changed",
        "from": [
          {
            "type": "deliveryTerms",
            "typeLabel": "Delivery Terms",
            "value": "Ex works",
            "weight": 0,
            "label": null
          }
        ],
        "to": [
          {
            "type": "volumeDiscount",
            "typeLabel": "Volume Discount",
            "value": {
              "threshold": 10000,
              "discountPercentage": 5
            },
            "weight": 0,
            "label": null
          }
        ],
        "context": null
      },
      {
        "field": "productPrices",
        "action": "added",
        "context": {
          "ean": "02389472934823423",
          "unitQuantity": 340,
          "unitPrice": "1050"
        }
      },
      {
        "field": "productPrices",
        "action": "removed",
        "context": {
          "ean": "5548234895345934578",
          "unitQuantity": 120,
          "unitPrice": "869"
        }
      }
    ],
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
conditionsOfSale | array | The conditions of sale
totals | object | Sales negotiation's calculated totals, split into categories (see below)
changes | object | A list of changes made to the entity since the basket was submitted
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
with-customer | Pending Approval by Customer | Changes have been made and the entity is waiting for the customer to approve them
complete | Complete | The negotiation is complete and a sales order has been created.

## Example request

Example request that will fetch the sales negotiations that are to be displayed to the customer as orders.

```
/api/sales-negotiations?status[]=active&status[]=pending-approval&contact=123&order[created]=desc
```

## Sales Negotiation Subresources

The sales negotiation resource has the following subresources:

Name | Path | Method | Response | Description
---- | ---- | ------ | -------- | -----------
Approve | /api/sales-negotiations/{id}/approve | PUT | Entity data | Approves a sales negotiation. Will fail if entity is not at 'with-customer' status
