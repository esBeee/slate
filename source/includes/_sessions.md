# Sessions

## Sign in

```javascript
fetch('https://testerpool-api.herokuapp.com/auth/sign_in', {
  method: 'POST',
  headers: {
    'Accept': 'application/vnd.api+json',
    'Content-Type': 'application/vnd.api+json'
  },
  body: JSON.stringify({
    email: 'a@b.de',
    password: 'foobar'
  })
})
```

> The above command returns user information as JSON structured like this:

```json
{
  "data": {
    "id": 1341,
    "email": "person_3@example.com",
    "note_new_test": true,
    "note_new_message": true,
    "note_reminder": true,
    "daily_summary": true,
    "weekly_summary": false,
    "match_notes_only": true,
    "preferred_locale": null,
    "send_declined_from_test_email":null,
    "send_removed_from_test_email": null,
    "last_daily_summary_sent_at": null,
    "last_weekly_summary_sent_at": null,
    "provider": "email",
    "uid": "person_3@example.com"
  }
}
```

This endpoint creates a session for a signed up user.


### HTTP Request

`POST https://testerpool-api.herokuapp.com/auth/sign_in`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
email | - | The email address of the user to be signed in.
password | - | The password of the user to be signed in.

### Noteable header content

On success, the response headers contain the uid and an access-token. Put those into the header of your next request for an authorized call.

Key | Meaning
--- | -------
uid | The user's uid.
access-token | The user's access-token. Changes with every successful authenticated request.
client | The specific client id.
expiry | The date at which the current session will expire.

<aside class="warning">
With every request, the access-token gets refreshed. So you always need to use the access-token from the response of the last successful request you used it for.
</aside>

<aside class="notice">
A user can only be signed up on up to 10 concurrent devices.
</aside>

<aside class="notice">
A token will remain valid for 2 weeks only.
</aside>


### Common errors

Error Code | Meaning
---------- | -------
401 | Invalid email-password-pair, User not confirmed


## Sign out

```javascript
fetch('https://testerpool-api.herokuapp.com/auth/sign_out', {
  method: 'DELETE',
  headers: {
    'Accept': 'application/vnd.api+json',
    'Content-Type': 'application/vnd.api+json',
    'uid': 'the-users-UID',
    'access-token': 'the-users-access-token',
    'client': 'the-client-id'
  },
  body: JSON.stringify({
  })
})
```

> The above command returns user information as JSON structured like this:

```json
{
  "success": true
}
```

This endpoint invalidates the current access-token for the given client-id.


### HTTP Request

`DELETE https://testerpool-api.herokuapp.com/auth/sign_out`

### Query Parameters

This method does not process any paramters.

### Common errors

Error Code | Meaning
---------- | -------
404 | Invalid session (user not found by given header)
