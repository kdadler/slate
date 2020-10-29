# Account Requests

> Path

```
/account-requests(/{id})
```

Usage data records.

## Account Requests Available Verbs

* GET
* POST

## Account Requests Fields

> Example Entity Response

```json
{
  "id": "/api/account-requests/1",
  "type": "AccountRequest",
  "attributes": {
    "id": 1,
    "contactId": 10,
    "type": "create",
    "requestData": {
      "fullname": "John Bonham",
      "Job Title": "Purchaser",
      "email": "john@zep.com",
      "phoneNumber": "07923494738",
      "companyName": "Zep Solutions",
      "companyNumber": "9283749234",
      "vatNumber": "0923874290384",
      "billingAddress": {
        "addressLineOne": "",
        "addressLineTwo": "",
        "townCity": "",
        "region": "",
        "postcode": "",
        "country": ""
      } 
    },
    "created": "2020-04-06T09:36:35.018Z",
    "updated": "2020-04-06T09:36:35.018Z"            
  }
}
```

> Example POST Body

```json
{
  "contactId": 10,
  "type": "update",
  "requestData": {
    "fullname": "John Bonham",
    "Job Title": "Purchaser",
    "email": "john@zep.com",
    "phoneNumber": "07923494738",
    "companyName": "Zep Solutions",
    "companyNumber": "9283749234",
    "vatNumber": "0923874290384",
    "billingAddress": {
      "addressLineOne": "",
      "addressLineTwo": "",
      "townCity": "",
      "region": "",
      "postcode": "",
      "country": ""
    } 
  }
}
```

Field | Type | Writeable | Nullable | Description
----- | ---- | --------- | -------- | -----------
id | int | No | - | Identifier
contactId | int | Yes | Yes | ID of the contact the request relates to. Only pass this when an update request is made
type | string | Yes | No | Type of the request. Must be either 'create' or 'update'
requestData | object | Yes | No | The data provided in support of the request.
created | datetime | No | - | Creation datetime of the entity
updated | datetime | No | - | Update datetime of the entity
