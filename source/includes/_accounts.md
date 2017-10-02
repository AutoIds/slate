# Accounts

## Create account
> Example Request

```shell
curl http://localhost:3000/api/v1/accounts \
  -H "Authorization: Token token=your_api_key" \
  -d name="account name"
```

> Example Response:

```json
{
  "id": "d0032abf630641eb973d52e3d7e1674c",
  "name": "account name",
  "created_at": "2017-10-01T16:44:31.642-07:00",
  "updated_at": "2017-10-01T16:44:31.642-07:00"
}
```

### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
name | String | Required | The name of the account to be created.


<aside class="success">
Dev Note - Show errors.
</aside>





## Get account
> Example Request

```shell
curl -H "Authorization: Token token=your_api_key" http://localhost:3000/api/v1/accounts/:account_id
```


> Example Response:

```json
{
  "id": "d0032abf630641eb973d52e3d7e1674c",
  "name": "account name",
  "created_at": "2017-10-01T16:44:31.642-07:00",
  "updated_at": "2017-10-01T16:44:31.642-07:00"
}
```

This returns account information if the authenticated user has access to the specified account.

### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
account_id | String | Required | The id of the account to retrieve.


<aside class="warning">
Dev Note - Show errors.
</aside>






## Get accounts
> Example Request

```shell
curl -H "Authorization: Token token=your_api_key" http://localhost:3000/api/v1/accounts
```


> Example Response:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "created_at": "2017-10-01T16:44:31.642-07:00",
    "updated_at": "2017-10-01T16:44:31.642-07:00"
  },
  {
    "id": 2,
    "name": "Max",
    "created_at": "2017-10-01T16:44:31.642-07:00",
    "updated_at": "2017-10-01T16:44:31.642-07:00"
  }
]
```

This returns an array of all accounts the authenticated user has access to. If the user has access to no accounts, an empty array is returned.


<aside class="warning">
Dev Note - We may need to only authenticate account admins and pass a specific user id as it may make sense for an account admin to query specific users and not send transactions as that user.
</aside>

<aside class="warning">
Dev Note - Add a new user column api_key that is then used to authenticate users.
</aside>







## Update account
> Example Request

```shell
curl http://localhost:3000/api/v1/accounts/:account_id \
  -H "Authorization: Token token=your_api_key" \
  -d name="new account name" \
  -X PUT
```


> Example Response:

```json
{
  "id": ":account_id",
  "name": "new account name",
  "created_at": "2017-10-01T16:44:31.642-07:00",
  "updated_at": "2017-10-01T17:03:14.049-07:00"
}
```

This returns account information if the authenticated user has access to the specified account.

### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
account_id | String | Required | The id of the account to upate.
name | String | Required | The new name for the account.


<aside class="warning">
Dev Note - Show errors.
</aside>







## Delete account
<aside class="warning">
This is currently not supported.
</aside>
