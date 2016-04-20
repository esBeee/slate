# Profiles

## Update a user profile

```javascript
fetch('https://testerpool-api.herokuapp.com/profiles/own', {
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
      type: "profiles",
      attributes: {
        first_name: "Mark",
        last_name: "Hark",
        day_of_birth: "1990-02-17",
        sex: 2,
        status: 1
      },
      relationships: {
        user_addresses: {
          data: [
            {
              type: "user_addresses",
              id: 4,
              attributes: {
                company: "Caltec",
                longitude: 5.643423,
                latitude: 2.3565,
                street: "Sesamstr.",
                street_no: "3 A",
                zip_code: "35673",
                city: "Berlin",
                state: "Berlin",
                vat_no: "DE294407310",
                country: "Germany"
              }
            }
          ]
        }
      }
    }
  })
})
```

> The above command returns the updated profile as JSON

```json
{
  "data"=> {
    "id"=>"10722",
    "type"=>"profiles",
    "attributes"=> {
      "first_name"=>"Thomas",
      "last_name"=>"Anderson",
      "sex"=>2,
      "balance"=>"0,00 €",
      "day_of_birth"=>"1998-04-15",
      "status"=>1,
      "created_at"=>"2016-04-15T16:02:23.245Z",
      "updated_at"=>"2016-04-15T16:02:23.245Z"
    }, 
    "relationships"=> {
      "addresses"=> {
        "data"=> [
          {
            "id"=>"15031",
            "type"=>"addresses"
          }
        ]
      },
      "phone_numbers"=> {
        "data"=>[]
      },
      "bank_accounts"=> {
        "data"=>[]
      },
      "paypal_accounts"=> {
        "data"=>[]
      }
    }
  },
  "included"=> [
    {
      "id"=>"15031",
      "type"=>"addresses",
      "attributes"=> {
        "street"=>"Sesamstr.",
        "street_no"=>"3 A",
        "zip_code"=>"35673",
        "city"=>"Berlin",
        "country"=>"Germany",
        "company"=>"Caltec",
        "additional_address"=>null,
        "vat_no"=>"DE294407310",
        "longitude"=>5.643423,
        "latitude"=>2.3565,
        "activity_radius"=>0,
        "created_at"=>"2016-04-15T16:02:23.247Z",
        "updated_at"=>"2016-04-15T16:02:23.247Z",
        "state"=>"Berlin"
      }
    }
  ]
}
```

This endpoint updates a user profile.

### HTTP Request

`PATCH https://testerpool-api.herokuapp.com/profiles/own`

### Profile attributes

Parameter | Type | Description
--------- | ---- | -----------
first_name | string | The user's first name.
last_name | string | The user's last name.
day_of_birth | date | The user's day of birth.
sex | integer | The user's gender. Legend: 1 => Female, 2 => Male, 3 => Unassigned.
status | integer | Legend: 0 => The user is a tester, 1 => The user is a sponsor.

### User address attributes

Parameter | Type | Description
--------- | ---- | -----------
company | string |
longitude | decimal |
latitude | decimal |
street | string |
street_no | string |
zip_code | string |
city | string |
state | string |
vat_no | string |
country | string |

<aside class="success">
Responds 200 on success
</aside>

### Common errors

Error Code | Meaning
---------- | -------
401 | Not signed in
422 | Attributes invalid
