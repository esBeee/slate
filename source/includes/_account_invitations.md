# Account Invitations

## Create a new account invitation

```javascript
fetch('https://testerpool-api.herokuapp.com/account_invitations', {
  method: 'POST',
  headers: {
    'Accept': 'application/vnd.api+json',
    'Content-Type': 'application/vnd.api+json',
    'uid': 'user-5642s-UID',
    'access-token': 'user-5642s-access-token',
    'client': 'user-5642s-client-id'
  },
  body: {
    'email': 'a@b.de',
    'new_user_registration_url': 'https://www.testerpool.com/sign_up'
  }
})
```

> The above command returns the user's account as JSON including the just created account invitation

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
        "email": "a@b.de",
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

This endpoint creates a new invitation to the requesting user's account. After creating, an invitation email gets send to the given email address.

### HTTP Request

`POST https://testerpool-api.herokuapp.com/account_invitations`

### Parameters

Parameter | Description
--------- | -----------
email | The email address of the user to be invited.
new_user_registration_url | The url the invited user gets send in the invitation email.

<aside class="success">
Responds 201 on success
</aside>

### Common errors

Error Code | Meaning
---------- | -------
401 | Not signed in
404 | User doesn't have a profile
422 | Invalid parameters (e.g. not a valid email address)


## Destroy an account invitation

```javascript
fetch('https://testerpool-api.herokuapp.com/account_invitations/32', {
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

> The above command returns the user's account as JSON (which doesn't contain the just destroyed invitation anymore)

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
        "email": "a@b.de",
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

This endpoint destroys the account invitation whose id is given in the url, but only if the current user is owner of the account the invitation invites to.

### HTTP Request

`DELETE https://testerpool-api.herokuapp.com/account_invitations/<id>`

### Parameters

Parameter | Description
--------- | -----------
id | The id of the invitation to be destroyed.

<aside class="success">
Responds 200 on success
</aside>

### Common errors

Error Code | Meaning
---------- | -------
401 | Not signed in / User is not account owner / Invitation doesn't belong to the user's account
404 | Invitation with this id doesn't exist
