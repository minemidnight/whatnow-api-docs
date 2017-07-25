## WhatNow
WhatNow is an app for listing parties with an extenstive API. The API is currently uses REST to send and receive data. Users must have a verified email to use the app.

## Base URL
The base URL for all API requests is:
```
https://whatnowapp.net/api/
```

## Authorization
All requests via REST must have an `Authorization` header with an API token, or an authorization querystring parameter.

Requests with no authorization will have the JSON code 50001, and those with an invalid token will have the JSON code 50002.

## Snowflakes
ID's are generated based off Twitter's snowflakes. Snowflakes are 64bit integers generated based off UNIX time, and are guaranteed to be unique. ID's are returned as strings to prevent integer overflow. EPOCH time starts in 2017 for WhatNow's snowflakes (1483228800000).