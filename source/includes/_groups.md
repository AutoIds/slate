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

Groups added, will be shown in the Groups menu list when you refresh your broswer.


### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
account_id | String | Required | The id of the account the group will be created under.
name | String | Required | The name of the group to be created.


<aside class="success">
A group contains can multiple domains and users.
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
  "updated_at": "2017-10-01T16:44:31.642-07:00",
  "groups":[
    {"group JSON"},
    ...
  ],
  "domains":[
    {"domain JSON"},
    ...
  ],
  "users":[
    {"user JSON"},
    ...
  ]   
}
```

Adding a domain to group will allow the group to see the specified domain data. Domains added to a group will show as a selected domain in the groups list of domains.
This returns group information if the authenticated user has access to the specified group.

### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
group_id | String | Required | The id of the group to retrieve.








## Get groups in account

See <a href="#get-account">Get account</a>


<aside class="success">
An account can only have a single group.
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
Currently you can only change the group name.
</aside>












## Add domain to group
> Example Request

```shell
curl http://localhost:3000/api/v1/groups/:group_id/domains/:domain_id \
  -X POST \
  -H "Authorization: Token token=your_api_key" \
  -H "Content-type: application/json" 
```


> Example Response:

```json
{
  "id": ":group_id",
  "name": "group name",
  "created_at": "2017-10-01T16:44:31.642-07:00",
  "updated_at": "2017-10-01T17:03:14.049-07:00",
  "domains":[
    {"domain JSON"},
    ...
  ],
  "users":[
    {"user JSON"},
    ...
  ]   
}
```

Adding a domain to a group will include the domain in the list of domains when the appropriate group is selected in the AutoID user interface.
This returns group information if the authenticated user has access to the specified group.

### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
group_id | String | Required | The id of the group to upate.
domain_name | String | Required | The name of the domain to add to the group.


<aside class="warning">
Domain must be associated with the account before it can be associated with the group. See <a href="#add-domain-to-account">Add domain to account</a>
</aside>








## Remove domain from group
> Example Request

```shell
curl http://localhost:3000/api/v1/groups/:group_id/domains/:domain_id \
  -X DELETE \
  -H "Authorization: Token token=your_api_key" \
  -H "Content-type: application/json" \
```


> Example Response:

```json
{
  "id": ":group_id",
  "name": "new group name",
  "created_at": "2017-10-01T16:44:31.642-07:00",
  "updated_at": "2017-10-01T17:03:14.049-07:00",
  "domains":[
    {"domain JSON"},
    ...
  ],
  "users":[
    {"user JSON"},
    ...
  ]   
}
```

Removing a domain from a group will exclude the domain in the list of domains when the appropriate group is selected in the AutoID user interface.
This returns group information if the authenticated user has access to the specified group.

### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
group_id | String | Required | The id of the group to upate.
domain_name | String | Required | The name of the domain to remove from the group.


<aside class="warning">
Domain must be associated with the account before it can be associated with the group. See <a href="#add-domain-to-account">Add domain to account</a>
</aside>

<aside class="success">
This command only removes the domain from being included in the group's list of domains.
</aside>








## Add user to group
> Example Request

```shell
curl http://localhost:3000/api/v1/groups/:group_id/users \
  -X POST \
  -H "Authorization: Token token=your_api_key" \
  -H "Content-type: application/json" \
  -d '{"email":"bob@example.com"}'
```

> Example Response:

```json
{
  "id": ":group_id",
  "name": "group name",
  "created_at": "2017-10-01T16:44:31.642-07:00",
  "updated_at": "2017-10-01T17:03:14.049-07:00",
  "domains":[
    {"domain JSON"},
    ...
  ],
  "users":[
    {"user JSON"},
    ...
  ]   
}
```

Users added will be sent an email invitation. These user will be allowed, upon login, to access all domains associated with this group.


### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
group_id | String | Required | The id of the group the user will be added to.
email | String | Required | The email of the user to be associated with the group.





## Remove user from group
> Example Request

```shell
curl http://localhost:3000/api/v1/groups/:group_id/users/:user_id \
  -X Delete \
  -H "Authorization: Token token=your_api_key" \
  -H "Content-type: application/json" 
```

> Example Response:

```json
{
  "id": ":group_id",
  "name": "group name",
  "created_at": "2017-10-01T16:44:31.642-07:00",
  "updated_at": "2017-10-01T17:03:14.049-07:00",
  "domains":[
    {"domain JSON"},
    ...
  ],
  "users":[
    {"user JSON"},
    ...
  ]   
}
```

Users removed from a group will no longer be allowed to access the domains associated with this group.


### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
group_id | String | Required | The id of the group the user will be added to.
user_id | String | Required | The id of the user to be associated with the group.







## Delete group
See <a href="#remove-group-from-account">Remove group from account</a>