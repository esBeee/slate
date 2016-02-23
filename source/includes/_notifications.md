# Notifications

## Get notifications

```javascript
fetch('https://testerpool-api.herokuapp.com/notifications?amount=1', {
  method: 'GET',
  headers: {
    'Accept': 'application/vnd.api+json',
    'Content-Type': 'application/vnd.api+json',
    'uid': 'user-5642s-UID',
    'access-token': 'user-5642s-access-token',
    'client': 'user-5642s-client-id'
  },
  body: {}
})
```

> The above command returns an array of notifications as JSON

```json
{
  "meta": {
    "amount_existing": "2"
  },
  "data": [
    {
      "type": "notifications",
      "id": "210",
      "attributes": {
        "created_at": "2016-02-22T23:29:34.660+01:00",
        "message": "You have received a new message on test 'Test to test a test'.",
        "corresponding_path": "/tests/292/conversations/405"
      }
    }
  ]
}
```

This endpoint receives a given amount of the newest notifications for a user.

### HTTP Request

`GET https://testerpool-api.herokuapp.com/notifications?amount=<amount>`

### Query parameters

Parameter | Type | Default | Description
--------- | ---- | ------- | -----------
amount | integer | 10 | Amount of notifications to be loaded.

<aside class="success">
Responds 200 on success
</aside>

### Response

Responds with notifications at the requested amount or less, if not that much exist, in *data* and the total amount of exisiting notifications for the given user as *amount_existing* in *meta*

### Common errors

Error Code | Meaning
---------- | -------
401 | Not signed in



## Delete a notification

```javascript
fetch('https://testerpool-api.herokuapp.com/notifications/1', {
  method: 'DELETE',
  headers: {
    'Accept': 'application/vnd.api+json',
    'Content-Type': 'application/vnd.api+json',
    'uid': 'user-5642s-UID',
    'access-token': 'user-5642s-access-token',
    'client': 'user-5642s-client-id'
  },
  body: {}
})
```

> The above command returns an array of notifications as JSON

```json
{
  "meta": {
    "amount_existing": "2"
  }
}
```

This endpoint allows the deletion of a specific notification of a user.

### HTTP Request

`DELETE https://testerpool-api.herokuapp.com/notifications/<id>`

### Parameters

Parameter | Default | Description
--------- | ------- | -----------
id | - | The numeric ID of the notification to be deleted.

<aside class="success">
Responds 200 on success
</aside>

### Response

Responds with the total amount of remaining notifications for the given user as *amount_existing* in *meta*

### Common errors

Error Code | Meaning
---------- | -------
401 | Not signed in.
404 | The given ID can't be assigned to an existing notification of the authenticated user.


## Delete all notifications

```javascript
fetch('https://testerpool-api.herokuapp.com/notifications', {
  method: 'DELETE',
  headers: {
    'Accept': 'application/vnd.api+json',
    'Content-Type': 'application/vnd.api+json',
    'uid': 'user-5642s-UID',
    'access-token': 'user-5642s-access-token',
    'client': 'user-5642s-client-id'
  },
  body: {}
})
```

> The above command returns an array of notifications as JSON

```json
{
  "meta": {
    "amount_existing": "0",
    "amount_deleted": "5"
  }
}
```

This endpoint allows the deletion of all notifications of a user.

### HTTP Request

`DELETE https://testerpool-api.herokuapp.com/notifications`

<aside class="success">
Responds 200 on success
</aside>

### Response

Responds with the total amount of remaining notifications for the given user as *amount_existing* (right now, there's no reason this number will not be 0 in this context) and *amount_deleted*, as amount of just deleted notifications, in *meta*.

### Common errors

Error Code | Meaning
---------- | -------
401 | Not signed in.
