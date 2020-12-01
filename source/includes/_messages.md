# Messages

> Path

```
/messages
```

A message is an entity that represents a customer contacting a Beautynet account manager.

## Message Available Verbs

* POST

## Message Fields

> Example Response Body

```json
{
  "id": "/api/messages/1",
  "type": "Message",
  "attributes": {
    "id": 1
  }
}
```

> Example POST Request Body

```json
{
  "contact": "/api/contacts/1",
  "subject": "A question",
  "body": "When is my order due?"
}
```

Field | Type | Writeable | Required | Description
----- | ---  | --------- | -------- | -----------
id | int | No | - | Unique identifier
contact | string | Yes | Yes | The IRI of the contact that the message is sent by
subject | string | Yes | The subject of the message
body | string | Yes | The body of the  message
