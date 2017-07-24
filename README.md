## WhatNow
WhatNow is an app for listing parties with an extenstive API. The API is currently only supports REST to send and receive data.

## Base URL
The base URL for all API requests is:
```
https://whatnowapp.net/api/
```

## Authorization
All requests via REST must have an `Authorization` header with an API token (or an authorization querystring parameter).

## Snowflakes
All things with an ID are using snowflakes. Snowflakes are 64bit integers generated based off UNIX time, and are guaranteed to be unique. ID's are returned as strings to prevent integer overflow.
