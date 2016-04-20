# Users

## Update a user's settings

```javascript
fetch('https://testerpool-api.herokuapp.com/users/self', {
  method: 'PATCH',
  headers: {
    'Accept': 'application/vnd.api+json',
    'Content-Type': 'application/vnd.api+json',
    'Authorization': 'Your-own-personal-tp-api-key',
    'uid': 'user-5642s-UID',
    'access-token': 'user-5642s-access-token',
    'client': 'user-5642s-client-id'
  },
  body: JSON.stringify({
    data: {
      type: 'users',
      attributes: {
        "email": "a@b.com",
        "note_new_test": true,
        "note_new_message": true,
        "note_reminder": true,
        "daily_summary": true,
        "weekly_summary": false,
        "match_notes_only": true,
        "preferred_locale": 'en',
        "send_declined_from_test_email": true,
        "send_removed_from_test_email": false
      }
    }
  })
})
```

> The above command returns the updated user as JSON

```json
{
  "data": {
    "type": "users",
    "id": 5642,
    "attributes": {
      "id": 5642,
      "email": "a@b.com",
      "created_at": "2016-02-18T04:09:20.803+01:00",
      "updated_at": "2016-02-18T04:09:21.085+01:00",
      "note_new_test": true,
      "note_new_message": true,
      "note_reminder": true,
      "daily_summary": true,
      "weekly_summary": false,
      "match_notes_only": true,
      "preferred_locale": "en",
      "send_declined_from_test_email": true,
      "send_removed_from_test_email": false,
      "last_daily_summary_sent_at": null,
      "last_weekly_summary_sent_at": "2016-02-18T02:09:21.085+01:00",
      "provider": "email",
      "uid": "a@b.com"
    }
  }
}
```

This endpoint updates a user's settings.

### HTTP Request

`PATCH https://testerpool-api.herokuapp.com/users/self`

### Attributes

Parameter | Type | Description
--------- | ---- | -----------
email | string | The users primary email address.
note_new_test | boolean | If *true*, the user receives an email everytime a new test gets published.
note_new_message | boolean | If *true*, the user receives an email everytime he receives a message.
note_reminder | boolean |
daily_summary | boolean | If *true*, the user receives daily summaries about new tests.
weekly_summary | boolean | If *true*, the user receives a summary about new tests on friday afternoon.
match_notes_only | boolean | If *true*, the above notifications only considers tests, the user can apply to.
preferred_locale | string | The user's preferred locale.
send_declined_from_test_email | boolean |  If *true*, the user receives an email everytime he gets declined from a test.
send_removed_from_test_email | boolean |  If *true*, the user receives an email everytime he gets declined from a test.

<aside class="success">
Responds 200 on success
</aside>

### Common errors

Error Code | Meaning
---------- | -------
401 | Not signed in
422 | Attributes invalid
