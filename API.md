# API Schema

This is a JSON API, hence `Content-Type` is always `application-json`.

`checklist_uuid` and `item_uuid` should have different format/length to be easily distinguishable.

##GET `/[checklist_uuid]`
Get a checklist

- Request: `{ "uuid": "6uD7mU" }`
- Response: `200 OK`

```json
{
  "checklist": {
    "uuid": "6uD7mU",
    "title": "My New Checklist"
  },
  "items": [
    {
      "uuid": "97af0f62-f988-11e6-bc64-92361f002671",
      "title": "My First Item",
      "done": false,
      "priority": 0
    },
    {
      "uuid": "c5f74b50-f988-11e6-bc64-92361f002671",
      "title": "My 2nd Item",
      "done": true,
      "priority": 1
    }
  ]
}
```

##POST `/checklists`
Create a checklist

- Request: `{ "title": "My New Checklist" }`
- Response: `200 OK`

```json
{
  "uuid": "6uD7mU"
}
```

##POST `/[checklist_uuid]`
Update a checklist

- Request: `{ "title": "The Updated Title" }`
- Response: `204 No Content`

##POST `/items`
Create an item

- Request: `{ "checklist": "6uD7mU", "item": "A New Item" }`
- Response: `200 OK`

```json
{
  "uuid": "5d68a68c-f989-11e6-bc64-92361f002671",
  "priority": 2
}
```

##POST `/[item_uuid]`
Update an item

- Request: `{ "title": "New title", "done": true }`
- Response: `204 No Content`

##POST `/items/reorder`
Change order of items

- Request: 
```json
{ 
  "97af0f62-f988-11e6-bc64-92361f002671": 2, 
  "c5f74b50-f988-11e6-bc64-92361f002671": 0, 
  "5d68a68c-f989-11e6-bc64-92361f002671": 1
}
```

- Response: `204 No Content`

##POST `/[item_uuid]/delete`
Delete an item

- Response: `204 No Content`
