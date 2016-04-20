# Passwords

## Change password

```javascript
fetch('https://testerpool-api.herokuapp.com/auth/password', {
  method: 'PUT',
  headers: {
    'Accept': 'application/vnd.api+json',
    'Content-Type': 'application/vnd.api+json',
    'Authorization': 'Your-own-personal-tp-api-key',
    'uid': 'the-users-UID',
    'access-token': 'the-users-access-token',
    'client': 'the-client-id'
  },
  body: JSON.stringify({
    password: 'foobar',
    password_confirmation: 'foobar'
  })
})
```

> The above command returns user information as JSON structured like this:

```json
{
  "success": true,
  "data": {
    "user": {
      "id": 4048,
      "email": "person_25@example.com",
      "created_at": "2016-02-17T20:27:25.974+01:00",
      "updated_at": "2016-02-17T20:27:26.198+01:00",
      "note_new_test": true,
      "note_new_message": true,
      "note_reminder": true,
      "daily_summary": true,
      "weekly_summary": false,
      "match_notes_only": true,
      "preferred_locale": null,
      "send_declined_from_test_email": null,
      "send_removed_from_test_email": null,
      "last_daily_summary_sent_at": null,
      "last_weekly_summary_sent_at": null,
      "provider": "email",
      "uid": "person_25@example.com"
    },
    "message": "Ihr Passwort wurde erfolgreich aktualisiert."
  }
}
```

This endpoint changes the signed in user's password.


### HTTP Request

`PUT https://testerpool-api.herokuapp.com/auth/password`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
password | - | The new password
password_confirmation | - | Confirmation for new password.

<aside class="warning">
This will additionally require the user's current password as query paramter in the near future.
</aside>


### Common errors

Error Code | Meaning
---------- | -------
422 | Password confirmation doesn't match password / Password blank / Password too short
