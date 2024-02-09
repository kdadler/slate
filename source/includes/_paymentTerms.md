# Payment Terms

> Path

```
/payment-terms
```

Payment terms that a customer can hold which will apply to their orders.

## Payment Term Verbs

* GET

## Payment Term Fields

> Example Entity Response

```json
{
  "data": {
    "id": "/api/v1/payment-terms/1",
    "type": "PaymentTerm",
    "attributes": {
      "id": 1,
      "label": "Strictly Proforma",
      "active": true,
      "created": "2020-01-01T00:00:00+00:00",
      "updated": "2020-01-01T00:00:00+00:00"
    }
  }
}
```

> Field list

| Field          | Type   | Description                          |
|----------------|--------|--------------------------------------|
| id             | int    | Unique identifier                    |
| label          | string | The label of the term                |
| active         | bool   | Whether the term is active or not    |
| created        | string | The date the term was created        |
| updated        | string | The date the term was last updated   |

## Payment Term Query Parameters

| Filter       | Description                                     | Example                               | Detail           | 
|--------------|-------------------------------------------------|---------------------------------------|------------------|
| id           | Filter by entity ID                             | /api/v1/payment-terms?id=1            | Exact match only |
| label        | Filter by term's label                          | /api/v1/payment-terms?label=Ex        | Partial match    |
| active       | Filter by the active flag against terms         | /api/v1/payment-terms?active=1        | Boolean          |
| itemsPerPage | Set the number of items per page to be returned | /api/v1/payment-terms?itemsPerPage=50 | Defaults to 25   |
| page         | Set the page of results to return               | /api/v1/payment-terms?page=3          | Defaults to 1    |
