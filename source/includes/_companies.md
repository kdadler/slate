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
    "id": "/api/companies/1",
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
      "invoiceAddress": {
        "addressLineOne": "1 Monster Road",
        "addressLineTwo": "Monster Town",
        "townCity": "Monster City",
        "region": "Monster County",
        "postcode": "MM1 1EE",
        "country": "UK"
      },
      "deliveryAddress": {
        "addressLineOne": "1 Monster Road",
        "addressLineTwo": "Monster Town",
        "townCity": "Monster City",
        "region": "Monster County",
        "postcode": "MM1 1EE",
        "country": "UK"
      },
      "created": "2020-01-01T00:00:00+00:00",
      "updated": "2020-01-01T00:00:00+00:00"
    },
    "relationships": {
      "primaryContact": {
        "data": {
          "id": "/api/contacts/2",
          "type": "Contact"
        }
      },
      "paymentTerm": {
        "data": [
          {
            "id": "/api/payment-terms/1",
            "type": "PaymentTerm"
          }
        ]
      },
      "deliveryTerm": {
        "data": [
          {
            "id": "/api/delivery-terms/1",
            "type": "DeliveryTerm"
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
  "invoiceAddress": {
    "addressLineOne": "1 Monster Road",
    "addressLineTwo": "Monster Town",
    "townCity": "Monster City",
    "region": "Monster County",
    "postcode": "MM1 1EE",
    "country": "UK"
  },
  "deliveryAddress": {
    "addressLineOne": "1 Monster Road",
    "addressLineTwo": "Monster Town",
    "townCity": "Monster City",
    "region": "Monster County",
    "postcode": "MM1 1EE",
    "country": "UK"
  },
  "paymentTerm": "/api/payment-terms/1",
  "deliveryTerm": "/api/delivery-terms/1"
}
        
```

> Field list

| Field                  | Type   | Description                                    | Read | Write | Required |
|------------------------|--------|------------------------------------------------|------|-------|----------|
| id                     | int    | Unique identifier                              | Y    | N     |
| companyName            | string | The company's name                             | Y    | Y     | Y        |
| companyNumber          | string | The company number                             | Y    | Y     |
| vatNumber              | string | The VAT number                                 | Y    | Y     |
| taxCode                | string | The company's tax code                         | Y    | Y     |
| dutchVatTerm           | string | The company's Dutch VAT term                   | Y    | Y     |
| regionOfOperation      | string | The company's region of operation              | Y    | Y     |
| creditLimit            | string | The company's credit limit                     | Y    | Y     |
| currency               | string | The company's currency                         | Y    | Y     |
| eoriNumber             | string | The company's EORI number                      | Y    | Y     |
| companyType            | string | The company's type                             | Y    | Y     |
| emailAddress           | string | The company's email address                    | Y    | Y     |
| phoneNumber            | string | The company's phone number                     | Y    | Y     |
| invoiceAddress         | object | The company's invoice address                  | Y    | Y     |
| deliveryAddress        | object | The company's delivery address                 | Y    | Y     |
| paymentTerm            | iri    | The company's default payment term             | Y    | Y     |
| deliveryTerm           | iri    | The company's default delivery term            | Y    | Y     |
| created                | string | The date and time the company was created      | Y    | N     |
| updated                | string | The date and time the company was last updated | Y    | N     |

## Company Relationships

| Relationship   | Description                         | Read | Write |
|----------------|-------------------------------------|------|-------|
| primaryContact | The company's primary contact       | Y    | Y     |
| paymentTerm    | The company's default payment term  | Y    | Y     |
| deliveryTerm   | The company's default delivery term | Y    | Y     |

## Company Query Parameters

| Filter       | Description                                                      | Example                                | Detail              | 
|--------------|------------------------------------------------------------------|----------------------------------------|---------------------|
| id           | Filter by entity ID                                              | /api/companies?id=1                    | Exact match only    |
| companyName  | Filter by company's name                                         | /api/companies?companyName=Google      | Partial match       |
| itemsPerPage | Set the number of items per page to be returned                  | /api/companies?itemsPerPage=50         | Defaults to 25      |
| page         | Set the page of results to return                                | /api/companies?page=3                  | Defaults to 1       |
| order        | Set the order of results. Supports companyName and companyNumber | /api/companies?order\[companyName]=asc | Accepts asc or desc |
