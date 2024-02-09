# Custom Fields

> Path

```
/custom-fields
```

Custom fields that a customer can hold which will apply to their orders.

There are currently two entities that support custom fields, `Contact` and `Company`. Both of these entities have
a field titled `customFieldData` which is used to read and write custom field data. See below for details on how this is
structured.

## Custom Field Verbs

* GET

## Custom Field Fields

> Example Entity Response

```json
{
  "data": {
    "id": "/api/v1/custom-fields/1",
    "type": "CustomField",
    "attributes": {
      "id": 1,
      "entityName": "Contact",
      "valueType": "options",
      "name": "my-field",
      "label": "My field",
      "options": {
        "options": [
          { "value": "option1", "label": "Option 1" },
          { "value": "option2", "label": "Option 2" },
        ],
        "optionsSource": "user-defined"
      },
      "active": true,
      "weight": 2,
      "fieldType": "custom",
      "created": "2020-01-01T00:00:00+00:00",
      "updated": "2020-01-01T00:00:00+00:00"
    }
  }
}
```

> Field list

| Field      | Type   | Description                                                               |
|------------|--------|---------------------------------------------------------------------------|
| id         | int    | Unique identifier                                                         |
| entityName | string | The entity the custom field is for. Will be either `Contact` or `Company` |
| valueType  | string | The type of value the field holds. See the value types section below      |
| name       | string | The machine name of the field                                             |
| label      | string | The human-readable label of the field                                     |
| options    | object | The options for the field if it is a select field                         |
| active     | bool   | Whether the field is active or not                                        |
| weight     | int    | The position of the field in lists relative to other fields               |
| fieldType  | string | The type of field. Will be either `custom` or `core`                      |
| created    | string | The date the term was created                                             |
| updated    | string | The date the term was last updated                                        |

## Custom Field Query Parameters

| Filter       | Description                                                              | Example                                | Detail              | 
|--------------|--------------------------------------------------------------------------|----------------------------------------|---------------------|
| id           | Filter by entity ID                                                      | /api/v1/custom-fields?id=1                | Exact match only    |
| label        | Filter by label                                                          | /api/v1/custom-fields?label=My            | Partial match       |
| entity       | Filter by entity name                                                    | /api/v1/custom-fields?entity=Contact      | Exact match only    |
| fieldType    | Filter by field type                                                     | /api/v1/custom-fields?fieldType=custom    | Exact match only    |
| active       | Filter by whether the field is active or not                             | /api/v1/custom-fields?active=true         | Exact match only    |
| itemsPerPage | Set the number of items per page to be returned                          | /api/v1/custom-fields?itemsPerPage=50     | Defaults to 25      |
| page         | Set the page of results to return                                        | /api/v1/custom-fields?page=3              | Defaults to 1       |
| order        | Set the order of results. Supports `id`, `label`, `created` and `weight` | /api/v1/custom-fields?order\[created]=asc | Accepts asc or desc |

## Custom Field Value Types

| Value Type    | Description                                                          | Has options? |
|---------------|----------------------------------------------------------------------|--------------|
| text          | Text field                                                           |
| number        | Number field                                                         |
| date          | Date field                                                           |
| checkbox      | Checkbox                                                             |
| single select | Select field where the user can select a single value from the list  | Y            |
| multi select  | Select field where the user can select multiple values from the list | Y            |

## Custom Field Options

The options field will contain a list of the options available to the user for the custom field. The options field is an
object and contains both an `options` value and `optionsSource` value.

* The `options` value is an array of objects, each containing a `value` and `label` key.
* The `optionsSource` value is a string and will be either `user-defined` or `countries`. In the future more sources may be added as required.

## Custom Field Data Fields

> Example entity response

```json
{
  "customFieldData": [
    {"customFieldId": 1, "value": "GR", "transformedValue": "Greece"},
    {"customFieldId": 2, "value": "My custom value", "transformedValue": "My custom value"}
  ]
}
```

> Example entity request

```json
{
  "customFieldData": [
    {"customFieldId": 1, "value": "GR"},
    {"customFieldId": 2, "value": "My custom value"}
  ]
}
```

Entities that support custom fields include in their API payloads a `customFieldData` field. This field comprises of
an array of objects as follows:

| Field            | Type | Description                                                                          | Read | Write |
|------------------|------|--------------------------------------------------------------------------------------|------|-------|
| customFieldId    | int  | The ID of the custom field that the data relates to                                  | Y    | Y     |
| value            | any  | The value of the custom field. This will be a string or array of strings             | Y    | Y     |
| transformedValue | any  | The transformed value of the custom field. This will be a string for all value types | Y    | N     |

Please note that when writing custom field data, the it will be validated on the following criteria:

* The value must be within the options if the custom field is a select field
* If the field is a multi select field, the value must be an array of strings
* The value must be a valid date if the custom field is a date field
* The field must exist
* The field must be active
* The field must belong to the given entity type
* There can be only 1 entry per custom field per entity
