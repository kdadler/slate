# Usage Data

> Path

```
/usage-data(/{id})
```

Usage data records.

## Usage Data Available Verbs

* POST

## Usage Data Fields

> Example POST Body

```json
{
  "contact": "/api/contacts/1",
  "action": "view",
  "data": {}
}
```

Field | Type | Writeable | Nullable | Description
----- | ---- | --------- | -------- | -----------
contact | string | Yes | Yes | The IRI of the contact that has performed the action
action | string | Yes | No | Token representing the action performed
data | object/array | Yes | No | Payload of data in support of the action being performed
