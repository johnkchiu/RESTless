---
layout: index
---

### Why, why not?
REST is great, actually, it's probably just good.  However, when adopted for mobile, it is problematic.

1. It's chatty -- REST recommends to break down API as resources, but it's too granular.  For mobile communication, the loggest leg of the communcation is the OTA time.  When API are very granular, it demands additional server calls to acomplish complicated tasks. 
2. It mumbles -- REST recommends using HTTP Response Codes (e.g. 200, 404) as the status response code for API.  It's insufficient because it confuses HTTP protocal status with application status.  

### Batch Request

#### Request
```
{
  "flow": "series",
  "error": "terminate",
  "requests": [
    {
      "id": "0",
      "method": "GET",
      "path": "/users"
    },
    {
      "id": "1",
      "method": "POST",
      "path": "/users",
      "body": {
        "name": "John Doe",
        "email": "john@doe.com"
      }
    },
    {
      "id": "2",
      "method": "DELETE",
      "path": "/users/123"
    }
  ]
}
```
#### Response
```
{
  "responses": [
    {
      "id": "0",
      "body": {
        "status": "success",
        "data": [
          {
            "id": "123",
            "name": "Jane Doe",
            "email": "jane@doe.com"
          },
          {
            "id": "456",
            "name": "Jimmy Doe",
            "email": "jimmy@doe.com"
          }
        ]
      }
    },
    {
      "id": "1",
      "body": {
        "status": "success",
        "data": {
          "id": "789",
          "name": "John Doe",
          "email": "john@doe.com"
        }
      }
    },
    {
      "id": "2",
      "body": {
        "status": "success"
      }
    }
  ]
}
```


### Better Response
Coming soon...


#### Read (`GET /user/`)


#### Create (`POST /user/`)

#### Update (`PUT /user/{id}`)

#### Delete (`DELETE /user/{id}`)





