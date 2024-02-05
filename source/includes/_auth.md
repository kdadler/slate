## Authentication

Authentication is handled via an Oauth2 flow. The first step is to contact our team to set up your credentials. They
will provide you with a client ID and client secret.

### Generating an Access Token

Once you have your credentials, you can get an access token by making a POST request to the `/token` endpoint. The
request must include the following headers:

* Accept: application/api
* Content-Type: application/api

> Example token request body

```json
{
  "grant_type": "client_credentials",
  "client_id": "MY_CLIENT_ID",
  "client_secret": "MY_CLIENT_ID"
}
```

The request body must include the following fields:

| Field         | Type   | Description                            |
|---------------|--------|----------------------------------------|
| grant_type    | string | Must be set to `client_credentials`    |
| client_id     | string | The client ID provided by our team     |
| client_secret | string | The client secret provided by our team |

> Example token response body

```json
{
    "token_type": "Bearer",
    "expires_in": 3600,
    "access_token": "ACCESS_TOKEN"
}
```

If successful, the token request will return a response with the following fields:

| Field        | Type   | Description                                   |
|--------------|--------|-----------------------------------------------|
| access_token | string | The access token                              |
| expires_in   | int    | The number of seconds until the token expires |
| token_type   | string | The type of token. Will always be `Bearer`    |

### Using the Access Token

> Example request header

```
Authorization: Bearer {ACCESS_TOKEN}
```

Once you have an access token, you can use it to make requests to the API. The access token must be included in the
`Authorization` header of each request. The header must be set to `Bearer {ACCESS_TOKEN}`.
