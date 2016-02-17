---
title: API Reference

language_tabs:
  - javascript
  - ruby

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - sessions
  - kittens
  - errors

search: true
---

# Introduction

Welcome to testerpool API! It follows the [json:api](http://jsonapi.org/) specification.

We have language bindings in Ruby! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/tripit/slate). Feel free to edit it and use it as a base for your own API's documentation.

### By default, all response headers contain this information

Key | Value
--- | -----
Content-Type | application/vnd.api+json; charset=utf-8
token-type | Bearer

<aside class="warning">
Always set the above Content-Type in the header of your requests.
</aside>


# Authentication

testerpool API currently responds to every request coming from host localhost:3000.


# Requests

```javascript
fetch('https://testerpool-api.herokuapp.com/some/thing', {
  method: 'POST',
  headers: {
    'Accept': 'application/vnd.api+json',
    'Content-Type': 'application/vnd.api+json',
    'uid': 'the-users-UID',
    'access-token': 'the-users-access-token',
    'client': 'the-id-of-this-client'
  },
  body: JSON.stringify({
    some: "data"
  })
})
```

Always include this information in the headers of your requests:

Key | Value
--- | -----
Accept | application/vnd.api+json
Content-Type | application/vnd.api+json

To send an authorized request, the following data is expected in the headers:

Key | Value
--- | -----
uid | The user's uid. You receive that on sign in.
access-token | The user's current access-token. You receive that on sign in or on any other successful authorized request. Note that only the last access-token you have received is valid!
client | The client id you use for your app


# Responses

```json
{
  "errors": [
    "Ungültige Anmeldeinformationen. Bitte versuchen Sie es erneut."
  ]
}
```

Unless otherwise stated, an unsuccessful request is of the following form (see code example)
