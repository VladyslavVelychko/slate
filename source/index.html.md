---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Disqo API Assignment
---

# Introduction

Welcome to the **Phone Number API**! You can use our API to access Phone Number API endpoints, which can get Phone information on various users, based on their Full Name or User ID.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.


# Authentication

> To authorize, use this code:

```ruby
require 'phone_number'

api = Phone_number::APIClient.authorize!('hash_code')
```

```python3
import phone_number

api = phone_number.authorize('hash_code')
```

```shell
# With shell, you can just pass the correct header with each request
curl "https://<url:port>" \
  -H "Authorization: hash_code"
```

```javascript
const phone_number = require('phone_number');

let api = phone_number.authorize('hash_code');
```

> Make sure to replace `meowmeowmeow` with your API key.

API keys allow access to the Phone Number API. You can register a new Phone Number API key at our [developer portal](http://example.com/developers).

API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: hash_token`

<aside class="notice">
You must replace <code>hash_token</code> with your personal API key.
</aside>

<aside class="warning">
Phone-number format used: E.164
</aside>

For API tools, like Postman use *Add to* = **query params**

# Phone Numbers

## Create new User with a Phone Number, Full Name and US state
**POST** method

### Endpoint URL: https://<url:port>/store/phone-number
Payload body:
```json
{
    “phoneNumber”: “+14131234567”,
    “fullName”: “John Doe”,
    “state”: “MA”
}
```

> The above command may return the following:

* 200 OK User successfully created. User id is <user_id>
* 401 Unathorized You’re trying to access the endpoint with wrong Authorization creds/method/etc
* 403 Forbidden You lack certain permission to perform this request


Code | Status | Message
--------- | ------- | -----------
200 | OK | User successfully created. User id is <user_id>
401 | Unathorized | You’re trying to access the endpoint with wrong Authorization creds/method/etc
403 | Forbidden | You lack certain permission to perform this request

<aside class="success">
Remember — a happy call is an authenticated request!
</aside>

## Get a Specific Phone Number

### Endpoint URL: https://<url:port>/users/search


> Params

```json
{
  “searchCriteria”: “fullName” | “user_id”,
  “searchCriteriaValue”: “John Doe” | “user_id”
}
```
GET request can be done both by Full Name or user ID.


Response:
* 200 OK
* Body: {“phoneNumber”: “+14131234567”}


If you’re an Administrator user, you can get all users’ phone numbers.
Params:
“searchCriteria”: “fullName” | “user_id”
“searchCriteriaValue”: “[ALL]”


**PUT**
* Endpoint URL: https://<url:port>/store/phone-number/<user_id>
* Payload body:
```json
{
    “fullName”: “John Doe-Herz”,
    “state”: “CA”
}
```

Response:
200 OK

**DELETE**
Endpoint URL: https://<url:port>/users/<user_id>
Response:
204 No Content

