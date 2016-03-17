# Accounts

## Get the user's account

```javascript
fetch('https://testerpool-api.herokuapp.com/account', {
  method: 'GET',
  headers: {
    'Accept': 'application/vnd.api+json',
    'Content-Type': 'application/vnd.api+json',
    'uid': 'user-5642s-UID',
    'access-token': 'user-5642s-access-token',
    'client': 'user-5642s-client-id'
  }
})
```

> The above command returns the user's account as JSON

```json
{
  "data": {
    "type": "accounts",
    "id": "4898",
    "attributes": {
      "tester_points": 9
    },
    "relationships": {
      "account_invitations": {
        "data": [
          {
            "type": "account_invitations",
            "id": "4"
          }
        ]
      },
      "members": {
        "data": [
          {
            "type": "profiles",
            "id": "66"
          }
        ]
      }
    }
  },
  "included": [
    {
      "id": "4",
      "type": "account_invitations",
      "attributes": {
        "email": "invited@add.de",
        "processed": true,
        "created_at": "2016-03-17T18:22:33.760+01:00",
        "updated_at": "2016-03-17T18:22:33.760+01:00"
      }
    },
    {
      "type": "profiles",
      "id": "66",
      "attributes": {
        "first_name": "Thomas",
        "last_name": "Anderson",
        "owns_account": false
      }
    }
  ]
}
```

> or "null" data if no account exists

```json
{
  "data": null
}
```

This endpoint retrieves the user's account if one exists.

### HTTP Request

`GET https://testerpool-api.herokuapp.com/account`

<aside class="success">
Responds 200 on success
</aside>

### Common errors

Error Code | Meaning
---------- | -------
401 | Not signed in
422 | Attributes invalid
