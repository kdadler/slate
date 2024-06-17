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
    "id": "/api/v1/addresses/1",
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
          "id": "/api/v1/companies/2",
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
  "company": "/api/v1/companies/2",
  "crmId": "1234567890"
}
        
```

> Field list

| Field          | Type         | Description                             | Read | Write | Required |
|----------------|--------------|-----------------------------------------|------|-------|----------|
| id             | int          | Unique identifier                       | Y    |       |
| addressType    | int          | The type of address                     | Y    | Y     | Y        |
| isPrimary      | bool         | Is this the primary address?            | Y    | Y     |
| addressLineOne | string       | The first line of the address           | Y    | Y     | Y        |
| addressLineTwo | string       | The second line of the address          | Y    | Y     |
| townCity       | string       | The town or city                        | Y    | Y     | Y        |
| region         | string       | The region or county                    | Y    | Y     |
| postcode       | string       | The postcode                            | Y    | Y     | Y        |
| country        | string       | The country                             | Y    | Y     | Y        |
| crmId          | string       | The unique identifier in the CRM system | Y    | Y     |
| created        | string       | The date the record was created         | Y    |       |
| updated        | string       | The date the record was last updated    | Y    |       |
| company        | relationship | The company the address belongs to      | Y    | Y     |

## Address Relationships

| Relationship | Description                         | Read | Write |
|--------------|-------------------------------------|------|-------|
| company      | The company the address belongs to  | Y    | Y     |

## Address Query Parameters

| Filter       | Description                                     | Example                           | Detail         | 
|--------------|-------------------------------------------------|-----------------------------------|----------------|
| company      | Filter by company's unique identifier           | /api/v1/addresses?company=10      | Exact match    |
| itemsPerPage | Set the number of items per page to be returned | /api/v1/addresses?itemsPerPage=50 | Defaults to 25 |
| page         | Set the page of results to return               | /api/v1/addresses?page=3          | Defaults to 1  |

## Address Types

There are 2 permitted types of address as follows:

| Token | Type     |
|-------|----------|
| 2     | Delivery |
| 3     | Invoice  |

A company is only allowed a single invoice address. However, a company may have multiple delivery addresses as required.

## Address Validation Rules

When creating or updating addresses, the following validation rules will be applied.

NOTE: Field value types must conform to the types specified in the field list above.

| Field          | Rule                                                                                                                                                   |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| addressType    | * Required<br/> * Value must be `2` (invoice) or `3` (delivery)<br/> * Only 1 address allowed per-company with a value of `2`                          |
| isPrimary      | * Required<br/> * Must be `true` for invoice addresses<br/> * Only 1 delivery address per company permitted with a `true` value                        |
| addressLineOne | * Required<br/> * Must not be empty<br/> * Max 300 characters                                                                                          |
| addressLineTwo | * Max 300 characters                                                                                                                                   |
| townCity       | * Required<br/> * Must not be empty<br/> * Max 150 characters                                                                                          |
| region         | * Max 150 characters                                                                                                                                   |
| postcode       | * Required<br/> * Must not be empty<br/> * Max 15 characters                                                                                           |
| country        | * Required<br/> * Must not be empty<br/> * Must be an [ISO 3166 country name or A2 code](https://en.wikipedia.org/wiki/List_of_ISO_3166_country_codes) |
| crmId          | * Max 255 characters                                                                                                                                   |
| company        | * Must be a valid company IRI                                                                                                                          |
