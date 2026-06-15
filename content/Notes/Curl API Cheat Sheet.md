---
---
## Common Curl Flags

|**Flag**|**Long Version**|**Explanation**|
|---|---|---|
|`-X`|`--request`|Specifies the HTTP method to use (`GET`, `POST`, `PUT`, `DELETE`, `PATCH`).|
|`-d`|`--data`|Sends the specified data to the HTTP server (automatically triggers a POST method if `-X` isn't set).|
|`-H`|`--header`|Passes extra HTTP headers to the server (e.g., Content-Type or Authentication tokens).|
|`-i`|`--include`|Includes the HTTP response headers in the output (helps verify status codes).|
|`-v`|`--verbose`|Shows the entire handshake, request headers, and response headers for deep troubleshooting.|

## Core HTTP Commands

### 1. GET (Retrieve Data)


```
curl https://api.example.com/users
```

### 2. POST (Create Data)


```
curl -X POST \
  -H "Content-Type: application/json" \
  -d '{"username": "johndoe", "email": "john@example.com"}' \
  https://api.example.com/users
```

### 3. PUT (Update/Replace Data)


```
curl -X PUT \
  -H "Content-Type: application/json" \
  -d '{"username": "johndoe", "email": "newjohn@example.com"}' \
  https://api.example.com/users/123
```

### 4. PATCH (Partially Update Data)


```
curl -X PATCH \
  -H "Content-Type: application/json" \
  -d '{"email": "patchjohn@example.com"}' \
  https://api.example.com/users/123
```

### 5. DELETE (Remove Data)


```
curl -X DELETE https://api.example.com/users/123
```