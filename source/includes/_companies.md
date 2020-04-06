# Companies

## Available Verbs

> Path

```
/companies(/{id})
```

* GET

## Fields

> Example Entity Response

```json
{
  "id": "/api/companies/1",
  "type": "Company",
  "attributes": {
    "id": 1,
    "companyName": "Sony",
    "companyNumber": "92384798234",
    "vatNumber": "123918132",
    "invoiceAddress": {
      "addresslineOne": "Warehouse 1",
      "addresslineTwo": "12 Walkman Road",
      "townCity": "Bravia",
      "region": "Viao",
      "postcode": "BV12 5PP",
      "country": "UK"
    },
    "deliveryAddress": {
      "addresslineOne": "Warehouse 1",
      "addresslineTwo": "12 Walkman Road",
      "townCity": "Bravia",
      "region": "Viao",
      "postcode": "BV12 5PP",
      "country": "UK"
    }
  },
  "relationships": {
    "contacts": [
      {"data": {"id":  "/contacts/1", "type": "Contact"}}
    ]
  }
}
```

Field | Type | Description
----- | ---  | -----------
id | int | Unique identifier
companyName | string | The name of the company
companyNumber | string | The registered number of the company
invoiceAddress | object | The company's invoice address
deliveryAddress | object | The company's delivery address


## Relationships

Name | Type | Description
---- | ---- | -----------
contacts | Many to one | The company's contacts

## Index Parameters

Name | Type | Match | Default | Description
---- | ---- | ----- | ------- | -----------
companyName | string | partial | null | Search against the company's name
