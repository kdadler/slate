# Sales Negotiations

> Path

```
/sales-negotiations
```

Sales that are at the negotiation stage with the customer.

## Sales Negotiation Available Verbs

* GET

## Sales Negotiation Fields

> Example Entity Response

```json
{
  "id": "/api/v1/sales-negotiations/1",
  "type": "SalesNegotiation",
  "attributes": {
    "id": 1,
    "formattedId": "SN-000-001",
    "salesOrderId": "SO0000001",
    "currencyCode": "GBP",
    "invoiceId": null,
    "invoiceDate": null,
    "reference": "ref001",
    "status": "Pending",
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
  },
  "relationships": {
    "salesOrder": {
      "data": {
        "id": "/api/v1/sales-orders/SO0000001",
        "type": "SalesOrder"
      }
    }
  }
}
```

| Field                    | Type         | Description                                                              |
|--------------------------|--------------|--------------------------------------------------------------------------|
| id                       | integer      | Unique identifier                                                        |
| formattedId              | string       | The unique identifier formatted for display                              |
| salesOrderId             | string&#124;null | The ID of the sales order that the sales negotiation is associated with  |
| currencyCode             | string       | The currency of the sale                                                 |
| invoiceId                | null         | Always NULL. Included for compatibility with the sales order API format. |
| invoiceDate              | null         | Always NULL. Included for compatibility with the sales order API format. |
| reference                | string&#124;null | Custom reference                                                         |
| status                   | string       | The human-readable status for the sales negotiation                      |
| conditionsOfSale         | array        | The conditions of sale                                                   |
| customerConditionsOfSale | array        | The above conditions formatted for display to the customer               |
| totals                   | object       | Sales negotiation's calculated totals, split into categories (see below) |
| changes                  | object       | A list of changes made to the entity since the basket was submitted      |
| created                  | string       | Datetime that the sales negotiation was created                          |

## Sales Negotiation Total Fields

| Field                       | Type   | Description                                         |
|-----------------------------|--------|-----------------------------------------------------|
| sellTotal                   | string | The product total with the discount applied         |
| sellTotalBeforeDiscount     | string | The product total without the discount applied      |
| sellDiscountPercent         | int    | The discount percent applied.                       |
| sellTax                     | string | The tax applied                                     |
| preTaxPriceAdjustment       | string | The value of the price adjustments applied pre-tax  |
| postTaxPriceAdjustment      | string | The value of the price adjustments applied post-tax |
| adjustedSellTotalWithoutTax | string | The net total                                       |
| adjustedSellTotalWithTax    | string | The gross total                                     |

## Sales Negotiation Query Parameters

| Filter          | Type   | Match   | Default | Description                                                               |
|-----------------|--------|---------|---------|---------------------------------------------------------------------------|
| contact         | int    | exact   | null    | The ID of the contact that the sales negotiations must be associated with |
| contact.company | int    | exact   | null    | The ID of the company that the sales negotiations must be associated with |                                                                      
| salesPerson.id  | int    | exact   | null    | The ID of the sales person that must own the sales negotiations           |
| status          | string | exact   | null    | Specify the status of the sales negotiations to be returned               |
| currencyCode    | string | exact   | null    | The currency that the sales negotiations must have                        |
| reference       | string | partial | null    | Fuzzy match against the sales negotiation's reference field               |
| id              | string | partial | null    | Fuzzy match against the sales negotiation's ID field                      |
| order\[created] | string | exact   | asc     | Order the results by created date                                         |
| itemsPerPage    | int    | exact   | 25      | The number of items to return per page                                    |
| page            | int    | exact   | 1       | The page of results to return                                             |
