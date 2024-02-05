# Delivery Terms

> Path

```
/delivery-terms
```

Delivery terms that a customer can hold which will apply to their orders.

## Delivery Term Verbs

* GET

## Delivery Term Fields

> Example Entity Response

```json
{
  "data": {
    "id": "/api/delivery-terms/1",
    "type": "DeliveryTerm",
    "attributes": {
      "id": 1,
      "label": "Ex works",
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

## Delivery Term Query Parameters

| Filter       | Description                                     | Example                             | Detail           | 
|--------------|-------------------------------------------------|-------------------------------------|------------------|
| id           | Filter by entity ID                             | /api/delivery-terms?id=1            | Exact match only |
| label        | Filter by term's label                          | /api/delivery-terms?label=Ex        | Partial match    |
| active       | Filter by the active flag against terms         | /api/delivery-terms?active=1        | Boolean          |
| itemsPerPage | Set the number of items per page to be returned | /api/delivery-terms?itemsPerPage=50 | Defaults to 25   |
| page         | Set the page of results to return               | /api/delivery-terms?page=3          | Defaults to 1    |
