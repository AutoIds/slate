# Accounts

## Create account
> Example Request

```shell
curl http://localhost:3000/api/v1/accounts \
  -X POST \
  -H "Authorization: Token token=your_api_key" \
  -H "Content-type: application/json" \
  -d '{"name":"account name"}'
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

This is a top level resource that contains groups, domains and users.

<aside class="notice">
  Notes:
  <ul>
    <li>Account names at this time are expected to be unique globally.</li>
    <li>Any user can currently create an account.</li>
    <li>User's can only access accounts they belong to.</li>
  </ul>
</aside>

### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
name | String | Required | The name of the account to be created.






## Get account
> Example Request

```shell
curl -H "Authorization: Token token=your_api_key" \
http://localhost:3000/api/v1/accounts/:account_id
```


> Example Response:

```json
{
  "id": "d0032abf630641eb973d52e3d7e1674c",
  "name": "account name",
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

This returns detailed account information if the authenticated user has access to the specified account.
User's can only access accounts they belong to.

### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
account_id | String | Required | The id of the account to retrieve.







## Get accounts
> Example Request

```shell
curl -H "Authorization: Token token=your_api_key" \
http://localhost:3000/api/v1/accounts
```


> Example Response:

```json
[
  {
    "id": account id,
    "name": "account name",
    "created_at": "2017-10-01T16:44:31.642-07:00",
    "updated_at": "2017-10-01T16:44:31.642-07:00",
    "groups": 2,
    "domains": 10,
    "admins": 1,
  },
]
```

This returns an array of all accounts the authenticated user has access to. If the user has access to no accounts, an empty array is returned.
The numbers returned for groups, admins and domains represents the total number of data associated with the account. For example, this account contains 2 groups, 1 admin user and 10 domains.

You can GET a specific account to see the actual data.









## Update account
> Example Request

```shell
curl http://localhost:3000/api/v1/accounts/:account_id \
  -X PUT \
  -H "Authorization: Token token=your_api_key" \
  -H "Content-type: application/json" \
  -d '{"name":"new account name"}'
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

Returns updated account information. If the user does not have access to the specified account, this request will fail.

<aside class="success">
Currently you can only change the account name.
</aside>


### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
account_id | String | Required | The id of the account to upate.
name | String | Required | The new name for the account.














## Add user to account
> Example Request

```shell
curl http://localhost:3000/api/v1/accounts/:account_id/admins \
  -X POST \
  -H "Authorization: Token token=your_api_key" \
  -H "Content-type: application/json" \
  -d '{"email":"bob@example.com"}'
```


> Example Response:

```json
{
  "id": "account id",
  "name": "account name",
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
    {"id":"user id","email":"bob@example.com"},
    {"user JSON"},
    ...
  ] 
}
```

User will be sent an email invitation be added to the specified account. User's currently invited to an account have account admin permissions. This allows these users to perform admin function on the account.

### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
account_id | String | Required | The id of the account to add user to.
email | String | Required | The email of user to invite to account.








## Remove user from account
> Example Request

```shell
curl http://localhost:3000/api/v1/accounts/:account_id/admins\:user_id \
  -X DELETE \
  -H "Authorization: Token token=your_api_key" \
  -H "Content-type: application/json" \
```


> Example Response:

```json
{
  "id": "account id",
  "name": "account name",
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

User will be removed from the specified account. User's email will not be included in the returned JSON indicating they are no longer associated with the account. 

### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
account_id | String | Required | The id of the account to remove the user from.
user_id | String | Required | The id of user to remove from the account.











## Add group to account
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
  "id": "group id",
  "name": "group name",
  "created_at": "2017-10-01T16:44:31.642-07:00",
  "updated_at": "2017-10-01T16:44:31.642-07:00"
}
```


### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
account_id | String | Required | The id of the account to add user to.
name | String | Required | The name of the group to add to account.



<aside class="success">
An account can only have a single group.
</aside>


<aside class="warning">
Dev Note - We may want to remove the unique key on groups table.
</aside>










## Remove group from account
> Example Request

```shell
curl http://localhost:3000/api/v1/accounts/:account_id/groups/:group_id \
  -X DELETE \
  -H "Authorization: Token token=your_api_key" 
```


> Example Response:

```json
{
  "id": "account id",
  "name": "account name",
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

The specified group will not be included in the returned JSON.

### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
account_id | String | Required | The id of the account to act upon.
group_id | String | Required | The id of the group to be removed.










## Add domain to account
> Example Request

```shell
curl http://localhost:3000/api/v1/accounts/:account_id/domains \
  -X POST \
  -H "Authorization: Token token=your_api_key" \
  -H "Content-type: application/json" \
  -d \
  '{"domain":"example.com", 
    "google_ua_code":"UA-12352365-66", 
    "industry":"home services"
  }'
```


> Example Response:

```json
{
  "id":"domain id",
  "domain":"example.com",
  "web_analytics":true,
  "display_numbers":false,
  "call_shield":false,
  "track_chats":true,
  "track_leads":true,
  "digital_ai":false,
  "url":"http://example.com",
  "created_at":"2017-10-04T14:17:33.000-07:00",
  "updated_at":"2017-10-04T14:17:33.000-07:00"
}
```


### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
account_id | String | Required | The id of the account the domain will be created under.
domain | String | Required | The domain name of the domain to be created.
google_ua_code | String | Optional | Google UA code for domain.
industry | String | Required | Which industry the domain is associated with.



<aside class="success">
Adding a domain to the account will list the domain in a groups available domains list.
</aside>









## Remove domain from account
> Example Request

```shell
curl http://localhost:3000/api/v1/accounts/:account_id/domains/:domain_id \
  -X DELETE \
  -H "Authorization: Token token=your_api_key" 
```


> Example Response:

```json
{
  "id": "account id",
  "name": "account name",
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

The specified domain will not be included in the returned JSON.

### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
account_id | String | Required | The id of the account to act upon.
domain_id | String | Required | The id of the domainå to be removed.






## Delete account
<aside class="warning">
This is currently not supported.
</aside>
