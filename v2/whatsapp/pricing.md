# View Pricing List

View all Country wise pricing list.
#include "_include/endpoint.md"

#### GET

```
{endpoint}whatsapp/pricing
```

#### PARAMETERS

| name               | optional | value                                          |
| ------------------ | -------- | ---------------------------------------------- |
| filter[iso]        | Yes      | The ISO code of the Country. EX: (IN, AF, ...) |
| filter[service]    | Yes      | The short code of the service name. EX: (WAP)  |
| filter[subservice] | Yes      | The short code of the service name. EX: (WAI)  |
| filter[status]     | Yes      | 1 or 0                                         |

#### Example Request

```
curl -X GET \
  '{endpoint}whatsapp/pricing' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx'
```

Kindly replace the token with your respective access_token and other params.

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Pricing List",
  "data": [
    {
      "iso": "IN",
      "country_name": "India",
      "calling_code": 91,
      "sale_price": "***",
      "sub_service": "WAI",
      "service": "WAP",
      "service_name": "Whatsapp",
      "currency": "IND",
      "status": 1,
      "created_at": "2022-09-26T01:05:28.000000Z",
      "updated_at": "2022-09-26T01:05:28.000000Z"
    }
  ],
  "links": {
    "first": "{endpoint}whatsapp/pricing?page=1",
    "last": "{endpoint}whatsapp/pricing?page=1",
    "prev": null,
    "next": null
  },
  "meta": {
    "current_page": 1,
    "from": 1,
    "last_page": 1,
    "links": [
      {
        "url": null,
        "label": "&laquo; Previous",
        "active": false
      },
      {
        "url": "{endpoint}whatsapp/pricing?page=1",
        "label": "1",
        "active": true
      },
      {
        "url": null,
        "label": "Next &raquo;",
        "active": false
      }
    ],
    "path": "{endpoint}whatsapp/pricing",
    "per_page": 15,
    "to": 1,
    "total": 1
  }
}
```
