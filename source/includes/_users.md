# Users

## Invite user to account
> Example Request

```shell
curl http://localhost:3000/api/v1/accounts/:account_id/users \
  -X POST \
  -H "Authorization: Token token=your_api_key" \
  -H "Content-type: application/json" \
  -d \
  '{"url":"http://account1user6668.com", 
    "google_ua_code":"UA-12352365-66", 
    "industry":"home services"
  }'
```

> Example Response:

```json
{
  "id":"ad17872c1fe446239823bc0c072e11da",
  "web_analytics":true,
  "display_numbers":false,"
  call_shield":false,
  "track_chats":true,
  "track_leads":true,
  "digital_ai":false,
  "url":"http://account1user6679.com",
  "created_at":"2017-10-03T16:51:26.000-07:00",
  "updated_at":"2017-10-03T16:51:26.000-07:00"
}
```

### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
account_id | String | Required | The id of the account the user will be created under.
url | String | Required | The url of the user to be created.
google_ua_code | String | Optional | Google UA code for user.
industry | String | Required | Which industry the user is associated with.





## Invite user to group
> Example Request

```shell
curl http://localhost:3000/api/v1/accounts/:account_id/users \
  -X POST \
  -H "Authorization: Token token=your_api_key" \
  -H "Content-type: application/json" \
  -d \
  '{"url":"http://account1user6668.com", 
    "google_ua_code":"UA-12352365-66", 
    "industry":"home services"
  }'
```

> Example Response:

```json
{
  "id":"ad17872c1fe446239823bc0c072e11da",
  "web_analytics":true,
  "display_numbers":false,"
  call_shield":false,
  "track_chats":true,
  "track_leads":true,
  "digital_ai":false,
  "url":"http://account1user6679.com",
  "created_at":"2017-10-03T16:51:26.000-07:00",
  "updated_at":"2017-10-03T16:51:26.000-07:00"
}
```

### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
account_id | String | Required | The id of the account the user will be created under.
url | String | Required | The url of the user to be created.
google_ua_code | String | Optional | Google UA code for user.
industry | String | Required | Which industry the user is associated with.





## Remove user from account



## Remove user from group



## Get user
> Example Request

```shell
curl -H "Authorization: Token token=your_api_key" http://localhost:3000/api/v1/users/:user_id
```


> Example Response:

```json
{
  "id":"ad17872c1fe446239823bc0c072e11da",
  "web_analytics":true,
  "display_numbers":false,"
  call_shield":false,
  "track_chats":true,
  "track_leads":true,
  "digital_ai":false,
  "url":"http://account1user6679.com",
  "created_at":"2017-10-03T16:51:26.000-07:00",
  "updated_at":"2017-10-03T16:51:26.000-07:00"
}
```

This returns user information if the authenticated user has access to the specified user.

### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
user_id | String | Required | The id of the user to retrieve.





## Get users in account





## Get users in group






## Update user
> Example Request

```shell
curl http://localhost:3000/api/v1/users/:user_id \
  -X PUT \
  -H "Authorization: Token token=your_api_key" \
  -H "Content-type: application/json" \
  -d '{"track_leads":false}'
```


> Example Response:

```json
{
  "id":"ad17872c1fe446239823bc0c072e11da",
  "web_analytics":true,
  "display_numbers":false,"
  call_shield":false,
  "track_chats":true,
  "track_leads":false,
  "digital_ai":false,
  "url":"http://account1user6679.com",
  "created_at":"2017-10-03T16:51:26.000-07:00",
  "updated_at":"2017-10-03T16:51:26.000-07:00"
}
```

This returns user information if the authenticated user has access to the specified user.

### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
user_id | String | Required | The id of the user to upate.
name | String | Required | The new name for the user.


<aside class="warning">
Dev Note - implement this.
</aside>








## Delete user
<aside class="warning">
This is currently not supported.
</aside>
