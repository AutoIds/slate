---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell: curl
  - ruby: Ruby

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - accounts
  - groups
  - domains
  - users
  - errors

search: true
---

# Introduction

Welcome to the AutoID API. Our API is organized around REST and uses HTTP response codes to indicate API errors. We use built-in HTTP features, like HTTP authentication and HTTP verbs, which are understood by off-the-shelf HTTP clients. We support cross-origin resource sharing, allowing you to interact securely with our API from a client-side web application. JSON is returned by all API responses.

We have language bindings in Shell and Ruby! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.


# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = AutoID::APIClient.authorize!('meowmeowmeow')
```


```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```


> Make sure to replace `meowmeowmeow` with your API key.

AutoID uses API keys to allow access to the API. Each AutoID user has an AutoID API key found in their user profile view.

AutoID expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: your_api_key`

<aside class="notice">
You must replace <code>your_api_key</code> with your personal API key.
</aside>


