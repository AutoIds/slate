# Groups

## Create group
> Example Request

```shell
curl http://localhost:3000/api/v1/accounts/:account_id/groups \
  -X POST \
  -H "Authorization: Token token=your_api_key" \
  -H "Content-type: application/json" \
  -d '{"name":"group name"}'
```

> Example Response:

```json
{
  "id": "d0032abf630641eb973d52e3d7e1674c",
  "name": "group name",
  "created_at": "2017-10-01T16:44:31.642-07:00",
  "updated_at": "2017-10-01T16:44:31.642-07:00"
}
```

### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
account_id | String | Required | The id of the account the group will be created under.
name | String | Required | The name of the group to be created.


<aside class="success">
Dev Note - Show errors.
</aside>





## Get group
> Example Request

```shell
curl -H "Authorization: Token token=your_api_key" http://localhost:3000/api/v1/groups/:group_id
```


> Example Response:

```json
{
  "id": "group_id",
  "name": "group name",
  "created_at": "2017-10-01T16:44:31.642-07:00",
  "updated_at": "2017-10-01T16:44:31.642-07:00"
}
```

This returns group information if the authenticated user has access to the specified group.

### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
group_id | String | Required | The id of the group to retrieve.


<aside class="warning">
Dev Note - Show errors.
</aside>






## Get groups
> Example Request

```shell
curl -H "Authorization: Token token=your_api_key" http://localhost:3000/api/v1/groups
```


> Example Response:

```json
[
  {
    "id": 1,
    "name": "group name 1",
    "created_at": "2017-10-01T16:44:31.642-07:00",
    "updated_at": "2017-10-01T16:44:31.642-07:00"
  },
  {
    "id": 2,
    "name": "group name 2",
    "created_at": "2017-10-01T16:44:31.642-07:00",
    "updated_at": "2017-10-01T16:44:31.642-07:00"
  }
]
```

This returns an array of all groups the authenticated user has access to. If the user has access to no groups, an empty array is returned.


<aside class="warning">
Dev Note - Add a new user column api_key that is then used to authenticate users.
</aside>







## Update group
> Example Request

```shell
curl http://localhost:3000/api/v1/groups/:group_id \
  -X PUT \
  -H "Authorization: Token token=your_api_key" \
  -H "Content-type: application/json" \
  -d '{"name":"new group name"}'
```


> Example Response:

```json
{
  "id": ":group_id",
  "name": "new group name",
  "created_at": "2017-10-01T16:44:31.642-07:00",
  "updated_at": "2017-10-01T17:03:14.049-07:00"
}
```

This returns group information if the authenticated user has access to the specified group.

### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
group_id | String | Required | The id of the group to upate.
name | String | Required | The new name for the group.


<aside class="warning">
Dev Note - Show errors.
</aside>







## Delete group
<aside class="warning">
This is currently not supported.
</aside>
