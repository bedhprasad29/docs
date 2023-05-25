# Mail Template

## API Endpoint

```
{domain}/api/{version}/
```

## View Template

View all the Templates list.

#### GET

```
{endpoint}mail/templates
```

#### PARAMETERS

| name           | optional | value                                                 |
| -------------- | -------- | ----------------------------------------------------- |
| filter[id]     | Yes      | The id is template id                                 |
| filter[name]   | Yes      | The name is template name                             |
| filter[alias]  | Yes      | The alias name of  template                           |
| filter[status] | Yes      | (0 is Draft),(1 is Approved)                          |

#### Example Request

```
curl -X GET \
  '{endpoint}mail/templates' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx'
```

Kindly replace the token with your respective access_token and other params.

#### Example Response

```json
{
    "status": "OK",
    "code": 200,
    "message": "Templates List",
    "data": [
        {
            "id": "6f082e66-317e-4e98-ae24-6a15fxxxxxxx",
            "name": "Demo template",
            "alias": "demo-template",
            "subject": "test subject",
            "payload": "Hi this is the demo template @{{value}}",
            "html": "<html><body>Hi this is the demo template @{{value}}</body></html>",
            "text": null,
            "status": 1,
            "created_at": "2023-03-23T11:34:32.000000Z",
            "updated_at": "2023-03-23T11:34:32.000000Z"
        }
    ],
    "links": {
        "first": "{domain}/api/{version}/mail/templates?page=1",
        "last": "{domain}/api/{version}/mail/templates?page=1",
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
                "url": "{domain}/api/{version}/mail/templates?page=1",
                "label": "1",
                "active": true
            },
            {
                "url": null,
                "label": "Next &raquo;",
                "active": false
            }
        ],
        "path": "{domain}/api/{version}/mail/templates",
        "per_page": 15,
        "to": 1,
        "total": 1
    }
}
```

## Create Templates

#### POST

```
{endpoint}mail/templates
```

#### PARAMETERS

| Name     | Description                                                               | Type                  | Required |
| -------- | ------------------------------------------------------------------------- | --------------------- | -------- |
| `name`     | name of the template                                                    | `string`              | Yes      |
| `subject`  | The subject line for your email                                         | `string`              | Yes      |
| `payload`  | The body of your email (actual text of the email)                       | `string`              | Yes      |
| `text`     | Normal text to send in an email                                         | `string`              | No      |

### Example Request

```
curl -X POST \
  '{endpoint}mail/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "name": "Demo template",
    "subject" : "Test subject",
    "payload": "Hi this is the demo template @{{value}}"
    "text": "Text to send"
}'
```

### Example Response

```
{
    "status": "OK",
    "code": 200,
    "message": "Template created successfully",
    "data": {
        "id": "2e9cef25-fa2d-464b-81fe-14e45a9xxxxx",
        "name": "Demo template",
        "alias": "demo-template",
        "subject": "Test subject",
        "payload": "Hi this is the demo template @{{value}}",
        "html": "<html><body>Hi this is the demo template @{{value}}</body></html>",
        "text": "Text to send",
        "status": 1,
        "created_at": "2023-03-24T11:57:18.000000Z",
        "updated_at": "2023-03-24T11:57:18.000000Z"
    }
}
```

## Edit Templates

Edit template using put method under your account

#### API Endpoint

```
{domain}/api/{version}/
```

#### PUT

```
{endpoint}mail/templates/{id}
```

Replace the {id} with the actual id of the template that you would like to Edit.

#### PARAMETERS

| name     | description                                                               | Type                  | Optional |
| -------- | ------------------------------------------------------------------------- | --------------------- | -------- |
| `name`     | name of the template                                                    | `string`              | Yes      |
| `subject`  | The subject line for your email                                         | `string`              | Yes      |
| `payload`  | The body of your email (actual text of the email)                       | `string`              | Yes      |
| `text`     | Normal text to send in an email                                         | `string`              | Yes      |

#### Example Request

```
curl -X PUT \
  '{endpoint}mail/templates/b23769e6-019f-48f4-aae9-ec00a5xxxxxx' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "payload": "Hi this changed demo template @{{value}}"
    "text": "Text to send in mail"
}'
```

#### Example Response

```
{
    "status": "OK",
    "code": 200,
    "message": "Template updated successfully",
    "data": {
        "id": "2e9cef25-fa2d-464b-81fe-14e45a9xxxxx",
        "name": "Demo template",
        "alias": "demo-template",
        "subject": "Test subject",
        "payload": "Hi this changed demo template @{{value}}",
        "html": "<html><body>Hi this changed demo template @{{value}}</body></html>",
        "text": "Text to send in mail",
        "status": 1,
        "created_at": "2023-03-24T11:57:18.000000Z",
        "updated_at": "2023-03-24T11:57:18.000000Z"
    }
}
```

## Duplicate Template

#### POST

```
{endpoint}mail/templates/duplicate/{id}
```

Replace the {id} with the actual id of the template that you would like to duplicate.
### Example Request

```
curl -X POST \
  '{endpoint}mail/templates/duplicate/b23769e6-019f-48f4-aae9-ec00a5xxxxxx' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx'
```

### Example Response

```
{
    "status": "OK",
    "code": 200,
    "message": "Template created successfully",
    "data": {
        "id": "2e9cef25-fa2d-464b-81fe-14e45a9xxxxx",
        "name": "Duplicate of Demo template",
        "alias": "duplicate-of-demo-template",
        "subject": "Test subject",
        "payload": "Hi this is the demo template @{{value}}",
        "html": "<html><body>Hi this is the demo template @{{value}}</body></html>",
        "text": "Text to send",
        "status": 1,
        "created_at": "2023-03-24T11:57:18.000000Z",
        "updated_at": "2023-03-24T11:57:18.000000Z"
    }
}
```


## Delete Templates

#### DELETE

```
{endpoint}mail/templates/{id}
```

Replace the {id} with the actual id of the template that you would like to delete.

#### Example Request

```
curl -X DELETE \
  {endpoint}mail/templates/7d77d0ef-63df-4ffb-83d6-xxxxxxxx \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx'
```

#### Example Response

```json
{
    "status": "OK",
    "code": 200,
    "message": "Template Successfully Deleted",
    "data": []
}
```