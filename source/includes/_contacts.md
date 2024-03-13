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
  "id": "/api/v1/contacts/1",
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
    "updated": "2020-01-01T00:00:00+00:00",
    "customFieldData": [
      {"customFieldId": 1, "value": "GR", "transformedValue": "Greece"},
      {"customFieldId": 2, "value": "My custom value", "transformedValue": "My custom value"}
    ],
    "isDeletable": false
  },
  "relationships": {
    "company": {
      "data": {
        "id": "/api/v1/companies/1",
        "type": "Company"
      }
    },
    "defaultSalespersonName": {
      "data": {
        "id": "/api/v1/users/1",
        "type": "User"
      }
    }
  }
}
```

> Example entity payload

```json
{
  "company": "/api/v1/companies/1",
  "isPrimary": true,
  "fullName": "Billy Crystal",
  "emailAddress": "",
  "phoneNumber": "0129827394",
  "crmId": "1234567890",
  "customFieldData": [
    {"customFieldId": 1, "value": "GR"},
    {"customFieldId": 2, "value": "My custom value"}
  ]
}
        
```

> Field list

| Field                  | Type             | Description                                                | Read | Write | Required |
|------------------------|------------------|------------------------------------------------------------|------|-------|----------|
| id                     | int              | Unique identifier                                          | Y    | N     |
| isPrimary              | boolean          | Whether the contact is the primary contact for the company | Y    | Y     |
| fullName               | string           | Full name of the contact                                   | Y    | Y     | Y        |
| emailAddress           | string&#124;null | The contact's email address                                | Y    | Y     |
| phoneNumber            | string&#124;null | The contact's phone number                                 | Y    | Y     |
| companyName            | string           | The name of the company the contact belongs to             | Y    | N     |
| companyNumber          | string&#124;null | The company number for the company the contact belongs to  | Y    | N     |
| vatNumber              | string&#124;null | The VAT number for the company the contact belongs to      | Y    | N     |
| defaultSalespersonName | string&#124;null | The name of the default salesperson for the contact        | Y    | N     |
| crmId                  | string&#124;null | The unique identifier in the CRM system                    | Y    | Y     |
| created                | string           | The date the contact was created                           | Y    | N     |
| updated                | string           | The date the contact was last updated                      | Y    | N     |
| isDeletable            | boolean          | Whether the contact can be deleted                         | Y    | N     |
| company                | relationship     | The company the contact belongs to                         | Y    | Y     | Y        |
| defaultSalesperson     | relationship     | The default salesperson of the associated company          | Y    | N     |
| customFieldData        | relationship     | The data relating to custom fields owned by the contact    | Y    | Y     |

## Contact Relationships

| Relationship       | Description                                        | Read | Write |
|--------------------|----------------------------------------------------|------|-------|
| company            | The company the contact belongs to                 | Y    | Y     |
| defaultSalesperson | The default salesperson for the associated company | Y    | Y     |

## Contact Query Parameters

| Filter              | Description                                                                        | Example                                     | Detail              | 
|---------------------|------------------------------------------------------------------------------------|---------------------------------------------|---------------------|
| id                  | Filter by entity ID                                                                | /api/v1/contacts?id=1                       | Exact match only    |
| company             | Filter by company ID                                                               | /api/v1/contacts?company=1                  | Exact match only    |
| fullName            | Filter by the contact's full name                                                  | /api/v1/contacts?fullName=Steph             | Partial match       |
| company.companyName | Filter by company's name                                                           | /api/v1/contacts?company.companyName=Google | Partial match       |
| itemsPerPage        | Set the number of items per page to be returned                                    | /api/v1/contacts?itemsPerPage=50            | Defaults to 25      |
| page                | Set the page of results to return                                                  | /api/v1/contacts?page=3                     | Defaults to 1       |
| order               | Set the order of results. Supports `created`, `fullName` and `company.companyName` | /api/v1/contacts?order\[created]=asc        | Accepts asc or desc |

## Contact Validation Rules

When creating or updating contacts, the following validation rules will be applied.

NOTE: Field value types must conform to the types specified in the field list above.

| Field           | Rule                                                     | Operation |
|-----------------|----------------------------------------------------------|-----------|
| isPrimary       | * A company may only have 1 primary contact              | PUT, POST |
| fullName        | * Required<br/> * Max 200 characters                     | PUT, POST |
| emailAddress    | * Must be valid email address                            | PUT, POST |
| crmId           | * Max 255 characters                                     | PUT, POST |
| company         | * Required<br/> * Must be a valid company IRI            | PUT, POST |
| customFieldData | _See custom fields section for validation rules_         | PUT, POST |
| -               | Contact must not be associated with any offers or orders | DELETE    |
