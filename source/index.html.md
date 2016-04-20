---
title: API Reference

language_tabs:
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - localization
  - dates_and_times
  - currencies
  - registrations
  - passwords
  - sessions
  - users
  - profiles
  - notifications
  - balance
  - accounts
  - account_invitations
  - errors

search: true
---

# Introduction

Welcome to testerpool API! It loosely follows the [json:api](http://jsonapi.org/) specification.

We have language bindings in JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This API documentation was created with [Slate](https://github.com/tripit/slate).


# Authentication

> This is how a minimal request should look (including the testerpool API key under _Authorization_)

```javascript
fetch('https://testerpool-api.herokuapp.com/some/thing', {
  method: 'GET',
  headers: {
    'Accept': 'application/vnd.api+json',
    'Content-Type': 'application/vnd.api+json',
    'Authorization': 'Your-own-personal-tp-api-key'
  }
})
```

To successfully request the **testerpool API**, you need to place a valid *testerpool API key* under key _Authorization_ in your request header.

Contact us at <a href="mailto:api@testerpool.com">api@testerpool.com</a> to request an API key.

testerpool API currently responds to every request coming from host localhost:3000, testerpool.s3-website.eu-central-1.amazonaws.com and testerpool.herokuapp.com


# Requests

> This is how a minimal request with user authorization should look

```javascript
fetch('https://testerpool-api.herokuapp.com/some/thing', {
  method: 'GET',
  headers: {
    'Accept': 'application/vnd.api+json',
    'Content-Type': 'application/vnd.api+json',
    'Authorization': 'Your-own-personal-tp-api-key',
    'uid': 'the-users-UID',
    'access-token': 'the-users-access-token',
    'client': 'the-client-id'
  }
})
```

Always include this information in the headers of your requests:

Key | Value
--- | -----
Accept | application/vnd.api+json
Content-Type | application/vnd.api+json
Authorization | Your own personal testerpool API key (learn more under section _Authorization_)

To send an authorized request, the following data is expected in the headers:

Key | Value
--- | -----
uid | The user's uid. You receive that on sign in.
access-token | The user's current access-token. You receive that on sign in or on any other successful authorized request. Note that only the last access-token you have received is valid!
client | The client id. You receive that on sign in.


# Responses

```json
{
  "errors": [
    { 
      "status": 422,
      "source": {
        "pointer": "/data/attributes/rooms"
      },
      "detail": "Must be present."
    }
  ]
}
```

> In some cases (regarding user authentication) also this and other formats are possible:

```json
{
  "errors": ["Authorized users only."]
}
```

### By default, all response headers contain this information

Key | Value
--- | -----
Content-Type | application/vnd.api+json; charset=utf-8
token-type | Bearer

### The following response codes are use on success

Code | Meaning
---- | -------
200 | Success
201 | Resource created

### Unless otherwise stated, an unsuccessful request is of the following form (see code example; note that only the keys *status* and *detail* are mandatory)
