# Registrations

## Sign up

```javascript
fetch('https://testerpool-api.herokuapp.com/auth/', {
  method: 'POST',
  headers: {
    'Accept': 'application/vnd.api+json',
    'Content-Type': 'application/vnd.api+json'
  },
  body: JSON.stringify({
    email: 'a@b.de',
    confirm_success_url: 'https://www.testerpool.com/successful_signup'
  })
})
```

> The above command returns user information as JSON structured like this:

```json
{
  "status": "success",
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
    "uid": "person_3@example.com",
    "created_at": "2016-02-17T17:15:00.650+01:00",
    "updated_at": "2016-02-17T17:15:00.650+01:00"
  }
}
```

This endpoint creates a new (unconfirmed) user.


### HTTP Request

`POST https://testerpool-api.herokuapp.com/auth/`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
email | - | The email address of the user to be signed in.
confirm_success_url | - | The URL the user gets redirected to after she clicks on the link in the confirmation instructions email.

<aside class="notice">
It's also possible to pass password and password_confirmation as query parameters, but this functionality is not yet tested.
</aside>

<aside class="success">
On success, an email gets send to the posted email address, containing a confirmation link that redirects to confirm_success_url after confirmation. It adds the following query parameters to the confirm_success_url:
</aside>

Parameter | Description
--------- | -----------
token | The first valid access-token.
client_id | The newly created client-id.
uid | The user's *uid*.
expiry | Some information about when the token will be invalid.
account_confirmation_success | Is always *true* in this case.
config | Usually set to *default*


### Common errors

Error Code | Meaning
---------- | -------
403 | Invalid email (malformed or already in use) or missing parameter
