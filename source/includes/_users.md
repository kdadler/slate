# Users

> Path

```
/users
```

Users of the system.

## User Available Verbs

* GET

## User Fields

> Example Entity Response

```json
{
  "data": {
    "id": "/api/users/1",
    "type": "User",
    "attributes": {
      "id": 1,
      "forename": "Jonathan",
      "surname": "Day",
      "username": "admin",
      "email": "jonathan.day@simitive.com",
      "enabled": true,
      "fullName": "Jonathan Day",
      "crmId": "1234567890",
      "updated": null
    }
  }
}
```

| Field    | Type        | Description                                 |
|----------|-------------|---------------------------------------------|
| id       | integer     | The unique identifier of the user           |
| forename | string      | The forename of the user                    |
| surname  | string      | The surname of the user                     |
| username | string      | The username of the user                    |
| email    | string      | The email address of the user               |
| enabled  | boolean     | Whether the user is enabled                 |
| fullName | string      | The full name of the user                   |
| crmId    | string      | The unique identifier in the CRM system     |
| updated  | string/null | The date and time the user was last updated |

## User Query Parameters

| Filter       | Description                                             | Example                         | Detail              | 
|--------------|---------------------------------------------------------|---------------------------------|---------------------|
| forename     | Filter by entity ID                                     | /api/users?forename=ted         | Exact match only    |
| surname      | Filter by company's name                                | /api/users?surname=lasso        | Partial match       |
| itemsPerPage | Set the number of items per page to be returned         | /api/users?itemsPerPage=50      | Defaults to 25      |
| page         | Set the page of results to return                       | /api/users?page=3               | Defaults to 1       |
| order        | Set the order of results. Supports forename and surname | /api/users?order\[forename]=asc | Accepts asc or desc |
