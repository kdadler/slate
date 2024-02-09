# Companies

> Path

```
/companies
```

Customer and supplier records.

## Company Verbs

* GET
* POST
* PUT
* DELETE

## Company Fields

> Example Entity Response

```json
{
  "data": {
    "id": "/api/v1/companies/1",
    "type": "Company",
    "attributes": {
      "id": 1,
      "companyName": "Curry's",
      "companyNumber": "123456789xyz",
      "vatNumber": "xxxx-xxxxx-xxx",
      "taxCode": "xxxxxx",
      "dutchVatTerm": "xxxxxxx",
      "regionOfOperation": "",
      "creditLimit": "€100,000.00",
      "currency": "GBP",
      "eoriNumber": "xxxxxxxx",
      "companyType": "",
      "emailAddress": "billy@crystal.com",
      "phoneNumberValue": "0129827394",
      "invoiceAddressData": {
        "id": 1,
        "addressType": "2",
        "isPrimary": true,
        "addressLineOne": "1 Monster Road",
        "addressLineTwo": "Monster Town",
        "townCity": "Monster City",
        "region": "Monster County",
        "postcode": "MM1 1EE",
        "country": "UK"
      },
      "deliveryAddressData": [
        {
          "id": 2,
          "addressType": "3",
          "isPrimary": true,
          "addressLineOne": "1 Monster Road",
          "addressLineTwo": "Monster Town",
          "townCity": "Monster City",
          "region": "Monster County",
          "postcode": "MM1 1EE",
          "country": "UK"
        },
        {
          "id": 3,
          "addressType": "3",
          "isPrimary": true,
          "addressLineOne": "3 Monster Road",
          "addressLineTwo": "Monster Town",
          "townCity": "Monster City",
          "region": "Monster County",
          "postcode": "MM1 1EE",
          "country": "UK"
        }
      ],
      "crmId": "1234567890",
      "created": "2020-01-01T00:00:00+00:00",
      "updated": "2020-01-01T00:00:00+00:00",
      "customFieldData": [
        {"customFieldId": 1, "value": "GR", "transformedValue": "Greece"},
        {"customFieldId": 2, "value": "My custom value", "transformedValue": "My custom value"}
      ]
    },
    "relationships": {
      "primaryContact": {
        "data": {
          "id": "/api/v1/contacts/2",
          "type": "Contact"
        }
      },
      "paymentTerm": {
        "data": [
          {
            "id": "/api/v1/payment-terms/1",
            "type": "PaymentTerm"
          }
        ]
      },
      "deliveryTerm": {
        "data": [
          {
            "id": "/api/v1/delivery-terms/1",
            "type": "DeliveryTerm"
          }
        ]
      },
      "invoiceAddress": {
        "data": {
          "id": "/api/v1/addresses/1",
          "type": "Address"
        }
      },
      "deliveryAddresses": {
        "data": [
          {
            "id": "/api/v1/addresses/2",
            "type": "Address"
          },
          {
            "id": "/api/v1/addresses/3",
            "type": "Address"
          }
        ]
      }
    }
  }
}
```

> Example entity payload

```json
{
  "companyName": "Curry's",
  "companyNumber": "123456789xyz",
  "vatNumber": "xxxx-xxxxx-xxx",
  "taxCode": "xxxxxx",
  "dutchVatTerm": "xxxxxxx",
  "regionOfOperation": "",
  "creditLimit": "€100,000.00",
  "currency": "GBP",
  "eoriNumber": "xxxxxxxx",
  "companyType": "",
  "emailAddress": "billy@crystal.com",
  "phoneNumberValue": "0129827394",
  "paymentTerm": "/api/v1/payment-terms/1",
  "deliveryTerm": "/api/v1/delivery-terms/1",
  "crmId": "1234567890",
  "customFieldData": [
    {"customFieldId": 1, "value": "GR"},
    {"customFieldId": 2, "value": "My custom value"}
  ]
}
        
```

> Field list

| Field               | Type         | Description                                    | Read | Write | Required | Notes                             |
|---------------------|--------------|------------------------------------------------|------|-------|----------|-----------------------------------| 
| id                  | int          | Unique identifier                              | Y    | N     |
| isCustomer          | bool         | Is the company a customer?                     | Y    | Y     |          | Defaults to `false`               |
| isSupplier          | bool         | Is the company a supplier?                     | Y    | Y     |          | Defaults to `false`               |
| companyName         | string       | The company's name                             | Y    | Y     | Y        |
| companyNumber       | string\|null | The company number                             | Y    | Y     |
| companyType         | string\|null | The company's type                             | Y    | Y     |
| emailAddress        | string\|null | The company's email address                    | Y    | Y     |
| vatNumber           | string\|null | The VAT number                                 | Y    | Y     |
| eoriNumber          | string\|null | The company's EORI number                      | Y    | Y     |
| taxCode             | string\|null | The company's tax code                         | Y    | Y     |
| dutchVatTerm        | string\|null | The company's Dutch VAT term                   | Y    | Y     |
| regionOfOperation   | string\|null | The company's region of operation              | Y    | Y     |
| phoneNumber         | string\|null | The company's phone number                     | Y    | Y     |
| currency            | string\|null | The company's currency                         | Y    | Y     |
| creditLimit         | string\|null | The company's credit limit                     | Y    | Y     |
| invoiceAddressData  | object\|null | Content of the associated invoice address      | Y    | N     |
| deliveryAddressData | array        | Content of the associated delivery addresses   | Y    | N     |
| crmId               | string\|null | The unique identifier in the CRM system        | Y    | Y     |
| created             | string       | The date and time the company was created      | Y    | N     |
| updated             | string       | The date and time the company was last updated | Y    | N     |
| customFieldData     | array        | Values associated with the custom fields       | Y    | Y     |
| defaultSalesperson  | relationship | The default salesperson for the company        | Y    | Y     |
| primaryContact      | relationship | The company's primary contact                  | Y    | N     |          | Set this via the contact resource |
| paymentTerm         | relationship | The company's default payment term             | Y    | Y     |
| deliveryTerm        | relationship | The company's default delivery term            | Y    | Y     |
| invoiceAddress      | relationship | The associated invoice address                 | Y    | N     |          | Set this via the address resource |
| deliveryAddresses   | relationship | The associated delivery addresses              | Y    | N     |          | Set this via the address resource |

## Company Relationships

| Relationship       | Description                             | Read | Write |
|--------------------|-----------------------------------------|------|-------|
| defaultSalesperson | The default salesperson for the company | Y    | Y     |
| primaryContact     | The company's primary contact           | Y    | N     |
| paymentTerm        | The company's default payment term      | Y    | Y     |
| deliveryTerm       | The company's default delivery term     | Y    | Y     |
| invoiceAddress     | The company's invoice address           | Y    | N     |
| deliveryAddresses  | The company's delivery addresses        | Y    | N     |

## Company Query Parameters

| Filter       | Description                                                          | Example                                   | Detail              | 
|--------------|----------------------------------------------------------------------|-------------------------------------------|---------------------|
| id           | Filter by entity ID                                                  | /api/v1/companies?id=1                    | Exact match only    |
| companyName  | Filter by company's name                                             | /api/v1/companies?companyName=Google      | Partial match       |
| itemsPerPage | Set the number of items per page to be returned                      | /api/v1/companies?itemsPerPage=50         | Defaults to 25      |
| page         | Set the page of results to return                                    | /api/v1/companies?page=3                  | Defaults to 1       |
| order        | Set the order of results. Supports `companyName` and `companyNumber` | /api/v1/companies?order\[companyName]=asc | Accepts asc or desc |

## Company Validation Rules

When creating or updating companies, the following validation rules will be applied.

NOTE: Field value types must conform to the types specified in the field list above.

| Field                   | Rule                                                                                                                               |
|-------------------------|------------------------------------------------------------------------------------------------------------------------------------|
| isCustomer & isSupplier | * One or both flags must be `true`                                                                                                 |
| companyName             | * Required<br/> * Must not be empty<br/> * Must be unique<br/> * Max 500 characters                                                |
| companyNumber           | * Max 50 characters                                                                                                                |
| companyType             | * Must be one of: `distributor`, `manufacturer`, `trader`, `wholesaler`, `retail_chain`, `retail_e_commerce`, `retail_independent` |
| emailAddress            | * Must be a valid email address                                                                                                    |
| vatNumber               | * Max 50 characters                                                                                                                |
| eoriNumber              | * Max 50 characters                                                                                                                |
| taxCode                 | * Max 50 characters                                                                                                                |
| dutchVatTerm            | * Max 50 characters                                                                                                                |
| regionOfOperation       | * Max 50 characters                                                                                                                |
| phoneNumber             | * Must be a valid phone number                                                                                                     |
| currency                | * Must be one of: `GBP`, `EUR`, `USD`                                                                                              |
| creditLimit             | * Max 255 characters                                                                                                               |
| crmId                   | * Max 255 characters                                                                                                               |
| customFieldData         | TODO: Add validation rules for custom fields                                                                                       |
| defaultSalesperson      | * Must be a valid user IRI                                                                                                         |
| paymentTerm             | * Must be a valid payment term IRI                                                                                                 |
| deliveryTerm            | * Must be a valid delivery term IRI                                                                                                |
