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
      "invitations": {
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
        "email": "thomas@anderson.com",
        "owns_account": false
      }
    }
  ]
}
```

> or if no account exists

```json
{
  "data": null
}
```

This endpoint retrieves the user's account along with its associated invitations and members if one exists.

### HTTP Request

`GET https://testerpool-api.herokuapp.com/account`

<aside class="success">
Responds 200 on success
</aside>

### Common errors

Error Code | Meaning
---------- | -------
401 | Not signed in


## Remove a user from an account

```javascript
fetch('https://testerpool-api.herokuapp.com/account/members/:id', {
  method: 'DELETE',
  headers: {
    'Accept': 'application/vnd.api+json',
    'Content-Type': 'application/vnd.api+json',
    'uid': 'user-5642s-UID',
    'access-token': 'user-5642s-access-token',
    'client': 'user-5642s-client-id'
  }
})
```

> The above command returns the user's account without the just deleted member as JSON

```json
{
  "data": {
    "type": "accounts",
    "id": "4898",
    "attributes": {
      "tester_points": 9
    },
    "relationships": {
      "invitations": {
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
        "email": "thomas@anderson.com",
        "owns_account": false
      }
    }
  ]
}
```

This endpoint removes a member from the user's account if this user is owner of his account.

### HTTP Request

`GET https://testerpool-api.herokuapp.com/account/members/<id>`

### Parameters

Parameter | Description
--------- | -----------
id | The profile id of the account member to be removed.

<aside class="success">
Responds 200 on success
</aside>

### Common errors

Error Code | Meaning
---------- | -------
401 | Not signed in
404 | No profile with this id is member of this account
