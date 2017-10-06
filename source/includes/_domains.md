# Domains

## Create domain
> Example Request

```shell
curl http://localhost:3000/api/v1/accounts/:account_id/domains \
  -X POST \
  -H "Authorization: Token token=your_api_key" \
  -H "Content-type: application/json" \
  -d \
  '{"domain_name":"http://example.com", 
    "google_ua_code":"UA-12352365-66", 
    "industry":"home services"
  }'
```

> Example Response:

```json
{
  "id":"domain id",
  "web_analytics":true,
  "display_numbers":false,"
  call_shield":false,
  "track_chats":true,
  "track_leads":true,
  "digital_ai":false,
  "domain_name":"http://example.com",
  "created_at":"2017-10-03T16:51:26.000-07:00",
  "updated_at":"2017-10-03T16:51:26.000-07:00"
}
```

### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
account_id | String | Required | The id of the account the domain will be created under.
url | String | Required | The url of the domain to be created.
google_ua_code | String | Optional | Google UA code for domain.
industry | String | Required | Which industry the domain is associated with.


<aside class="success">
Dev Note - Show errors.
</aside>

<aside class="warning">
Dev Note - Show list of allowed industries.
</aside>


<aside class="warning">
Dev Note - Describe features.
</aside>


<aside class="warning">
Dev Note - Domains can belong to multiple accounts. Changes to one domain effects all instances as we do not copy domains at this point.
</aside>








## Get domain
> Example Request

```shell
curl -H "Authorization: Token token=your_api_key" \
http://localhost:3000/api/v1/domains/:domain_id
```


> Example Response:

```json
{
  "id":"domain id",
  "web_analytics":true,
  "display_numbers":false,"
  call_shield":false,
  "track_chats":true,
  "track_leads":true,
  "digital_ai":false,
  "domain_name":"http://example.com",
  "created_at":"2017-10-03T16:51:26.000-07:00",
  "updated_at":"2017-10-03T16:51:26.000-07:00"
}
```

This returns domain information if the authenticated user has access to the specified domain.

### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
domain_id | String | Required | The id of the domain to retrieve.





## Get domains in account

See <a href="#get-account">Get account</a>




## Get domains in group
See <a href="#get-group">Get group</a>




## Update domain
> Example Request

```shell
curl http://localhost:3000/api/v1/domains/:domain_id \
  -X PUT \
  -H "Authorization: Token token=your_api_key" \
  -H "Content-type: application/json" \
  -d '{"track_leads":false}'
```


> Example Response:

```json
{
  "id":"domain id",
  "web_analytics":true,
  "display_numbers":false,"
  call_shield":false,
  "track_chats":true,
  "track_leads":false,
  "digital_ai":false,
  "domain_name":"http://example.com",
  "created_at":"2017-10-03T16:51:26.000-07:00",
  "updated_at":"2017-10-03T16:51:26.000-07:00"
}
```

This returns domain information if the authenticated user has access to the specified domain.

### ARGUMENTS

Argument | Type | Required | Description
---------  | ----------- | ----------- | -----------
domain_id | String | Required | The id of the domain to upate.
name | String | Required | The new name for the domain.


<aside class="warning">
Dev Note - Do we want to allow users to change anything about domains?
</aside>



## Add domain to account

See <a href="#add-domain-to-account">Add domain to account</a>



## Remove domain from account

See <a href="#remove-domain-from-account">Add domain to account</a>


## Add domain to group

See <a href="#add-domain-to-group">Add domain to group</a>


## Remove domain from group

See <a href="#remove-domain-from-group">Add domain to group</a>





## Delete domain
<aside class="warning">
This is currently not supported.
</aside>
