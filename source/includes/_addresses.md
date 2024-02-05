# Addresses

> Path

```
/addresses
```

Records of addresses.

## Address Verbs

* GET
* POST
* PUT
* DELETE

## Address Fields

> Example Entity Response

```json
{
  "data": {
    "id": "/api/addresses/1",
    "type": "Address",
    "attributes": {
      "id": 1,
      "addressType": 2,
      "isPrimary": false,
      "addressLineOne": "1 Monster Road",
      "addressLineTwo": "Monster Town",
      "townCity": "Monster City",
      "region": "Monster County",
      "postcode": "MM1 1EE",
      "country": "United Kingdom",
      "crmId": "1234567890",
      "created": "2020-01-01T00:00:00+00:00",
      "updated": "2020-01-01T00:00:00+00:00"
    },
    "relationships": {
      "company": {
        "data": {
          "id": "/api/companies/2",
          "type": "Company"
        }
      }
    }
  }
}
```

> Example entity payload

```json
{
  "addressType": 2,
  "isPrimary": false,
  "addressLineOne": "1 Monster Road",
  "addressLineTwo": "Monster Town",
  "townCity": "Monster City",
  "region": "Monster County",
  "postcode": "MM1 1EE",
  "country": "United Kingdom",
  "company": "/api/companies/2",
  "crmId": "1234567890"
}
        
```

> Field list

| Field          | Type   | Description                               | Read | Write | Required |
|----------------|--------|-------------------------------------------|------|-------|----------|
| id             | int    | Unique identifier                         | Y    |       |
| addressType    | int    | The type of address                       | Y    | Y     | Y        |
| isPrimary      | bool   | Is this the primary address?              | Y    | Y     |
| addressLineOne | string | The first line of the address             | Y    | Y     | Y        |
| addressLineTwo | string | The second line of the address            | Y    | Y     |
| townCity       | string | The town or city                          | Y    | Y     | Y        |
| region         | string | The region or county                      | Y    | Y     |
| postcode       | string | The postcode                              | Y    | Y     | Y        |
| country        | string | The country                               | Y    | Y     | Y        |
| crmId          | string | The unique identifier in the CRM system   | Y    | Y     |
| created        | string | The date the record was created           | Y    |       |
| updated        | string | The date the record was last updated      | Y    |       |
| company        | iri    | The IRI of company the address belongs to | N    | Y     | Y        |

## Address Relationships

| Relationship | Description                         | Read | Write |
|--------------|-------------------------------------|------|-------|
| company      | The company the address belongs to  | Y    | Y     |

## Address Query Parameters

| Filter       | Description                                     | Example                        | Detail           | 
|--------------|-------------------------------------------------|--------------------------------|------------------|
| company      | Filter by company's unique identifier           | /api/addresses?company=10      | Exact match      |
| itemsPerPage | Set the number of items per page to be returned | /api/addresses?itemsPerPage=50 | Defaults to 25   |
| page         | Set the page of results to return               | /api/addresses?page=3          | Defaults to 1    |

## Address Types

There are 2 permitted types of address as follows:

| Token | Type     |
|-------|----------|
| 2     | Invoice  |
| 3     | Delivery |

A company is only allowed a single invoice address. However, a company may have multiple delivery addresses as required.
