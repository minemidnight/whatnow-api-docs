##WhatNow
WhatNow is an app for listing parties with an extenstive API. The API supports both REST and WebSockets to send and receive data.

##Base URL
The base URL for all API requests is:
```
https://api.whatnow.com
```

##Authorization
All requests via REST should have an `Authorization` header with a token. WebSocket connections should also have an Authorization header.

##Snowflakes
All things with an ID are using snowflakes. Snowflakes are 64bit integers generated based off UNIX time, and are guaranteed to be unique. ID's are returned as strings to prevent integer overflow.
