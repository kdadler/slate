# Contacts

> Path

```
/contacts
```

Points of contacts with customers/suppliers.

## Contact Verbs

* GET
* POST
* PUT
* DELETE

## Contact Fields

> Example Entity Response

```json
{
  "id": "/api/contacts/1",
  "type": "Contact",
  "attributes": {
    "id": 1,
    "isPrimary": true,
    "fullName": "Billy Crystal",
    "emailAddress": "billy@gmail.com",
    "phoneNumber": "0129827394",
    "companyName": "Monsters Inc",
    "companyNumber": "0000000000",
    "vatNumber": "0000000000",
    "defaultSalespersonName": "Jonathan Day",
    "crmId": "1234567890",
    "created": "2020-01-01T00:00:00+00:00",
    "updated": "2020-01-01T00:00:00+00:00"
  },
  "relationships": {
    "company": {
      "data": {
        "id": "/api/companies/1",
        "type": "Company"
      }
    },
    "defaultSalespersonName": {
      "data": {
        "id": "/api/users/1",
        "type": "User"
      }
    }
  }
}
```

> Example entity payload

```json
{
  "company": "/api/companies/1",
  "fullName": "Billy Crystal",
  "emailAddress": "",
  "phoneNumber": "0129827394",
  "crmId": "1234567890"
}
        
```

> Field list

| Field                  | Type   | Description                                               | Read | Write | Required |
|------------------------|--------|-----------------------------------------------------------|------|-------|----------|
| id                     | int    | Unique identifier                                         | Y    | N     |
| fullName               | string | Full name of the contact                                  | Y    | Y     | Y        |
| emailAddress           | string | The contact's email address                               | Y    | Y     |
| phoneNumber            | string | The contact's phone number                                | Y    | Y     |
| companyName            | string | The name of the company the contact belongs to            | Y    | N     |
| companyNumber          | string | The company number for the company the contact belongs to | Y    | N     |
| vatNumber              | string | The VAT number for the company the contact belongs to     | Y    | N     |
| defaultSalespersonName | string | The name of the default salesperson for the contact       | Y    | N     |
| company                | iri    | The IRI of the company the contact belongs to             | N    | Y     | Y        |
| crmId                  | string | The unique identifier in the CRM system                   | Y    | Y     |
| created                | string | The date the contact was created                          | Y    | N     |
| updated                | string | The date the contact was last updated                     | Y    | N     |

## Contact Relationships

| Relationship       | Description                                        | Read | Write |
|--------------------|----------------------------------------------------|------|-------|
| company            | The company the contact belongs to                 | Y    | Y     |
| defaultSalesperson | The default salesperson for the associated company | Y    | Y     |

## Contact Query Parameters

| Filter              | Description                                                                  | Example                                  | Detail              | 
|---------------------|------------------------------------------------------------------------------|------------------------------------------|---------------------|
| id                  | Filter by entity ID                                                          | /api/contacts?id=1                       | Exact match only    |
| company             | Filter by company ID                                                         | /api/contacts?company=1                  | Exact match only    |
| fullName            | Filter by the contact's full name                                            | /api/contacts?fullName=Steph             | Partial match       |
| company.companyName | Filter by company's name                                                     | /api/contacts?company.companyName=Google | Partial match       |
| itemsPerPage        | Set the number of items per page to be returned                              | /api/contacts?itemsPerPage=50            | Defaults to 25      |
| page                | Set the page of results to return                                            | /api/contacts?page=3                     | Defaults to 1       |
| order               | Set the order of results. Supports created, fullName and company.companyName | /api/contacts?order\[created]=asc        | Accepts asc or desc |
