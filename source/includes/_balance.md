# Balance

## Get current balance

```javascript
fetch('https://testerpool-api.herokuapp.com/balance', {
  method: 'GET',
  headers: {
    'Accept': 'application/vnd.api+json',
    'Content-Type': 'application/vnd.api+json',
    'Authorization': 'Your-own-personal-tp-api-key',
    'uid': 'user-5642s-UID',
    'access-token': 'user-5642s-access-token',
    'client': 'user-5642s-client-id'
  },
  body: {}
})
```

> The above command returns the users current balance as JSON:

```json
{
  "meta": {
    "tester_points": "2",
    "monetary": "5.984,21 €"
  }
}
```

This endpoint receives the user's current amount of tester points and money.

### HTTP Request

`GET https://testerpool-api.herokuapp.com/balance`

<aside class="success">
Responds 200 on success
</aside>

### Common errors

Error Code | Meaning
---------- | -------
401 | Not signed in
