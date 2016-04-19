# Notifications

## Get notifications

> Note: The example query parameters beyond use unencoded [ and ] characters simply for readability. In practice, these characters must be percent-encoded, per the requirements in <a href='http://tools.ietf.org/html/rfc3986#section-3.4'>RFC 3986</a>.

```javascript
fetch('https://testerpool-api.herokuapp.com/notifications?page[limit]=2&page[offset]=1', {
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

> The above command returns 1 notification (when 2 exist), since the first was omitted by setting page[offset] to 1

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

This endpoint receives a users notifications according to the provided limit and offset parameters. Before the query parameters are applied, the notifications get sorted by creation date (newest first).

### HTTP Request

`GET https://testerpool-api.herokuapp.com/notifications?limit=<limit>&offset=<offset>`

### Query parameters

Parameter | Type | Default | Description
--------- | ---- | ------- | -----------
limit | integer | 10 | Amount of notifications to be received (tops).
offset | integer | 0 | Amount of notifications to be omitted.

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
