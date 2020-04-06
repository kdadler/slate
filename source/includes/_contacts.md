# Contacts

## Available verbs

> Path

```
/contacts(/{id})
```

* GET

## Fields

> Example Entity Response

```json
{
  "id": "/api/contacts/1",
  "type": "Contact",
  "attributes": {
    "id": 1,
    "fullName": "Billy Crystal",
    "emailAddress": "billy@gmail.com",
    "phoneNumber": "0129827394"
  },
  "relationships": {
    "company": {"data": {"id":  "/company/1", "type": "Company"}}
  }
}
```

Field | Type | Description
----- | ---  | -----------
id | int | Unique identifier
fullName | string | Full name of the contact
emailAddress | string | The contact's email address
phoneNumber | string | The contact's phone number.

## Relationships

Name | Type | Description
---- | ---- | -----------
company | One to many | The company that the contact belongs to.

## Index Parameters

Name | Type | Match | Default | Description
---- | ---- | ----- | ------- | -----------
fullName | string | partial | null | Search against the company's name
company | int | exact | null | The ID of the company that the contact belongs to
