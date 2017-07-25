# Receiving Data (REST)

All responses besides OAuth2 responses will have a "message" field holding a human-readable response about the request. Responses (which are not empty nor OAuth2) have the "code" field holding a code representing exactly what happened, because many HTTP error codes are repeated.

# Snowflakes

Snowflake to timestamp (ms)

```
(id / 4194304) + 1483228800000
```

Test if a snowflake _may be_ valid. This does not mean this snowflake exists in WhatNow, but it does mean it may represent a valid ID.
```
/^\d{17,21}$/
```

# Avatar Data

Data format example:
```
data:image/jpeg;base64,BASE64_ENCODED_JPEG_IMAGE_DATA
```

Ensure you use the proper header type (image/jpeg, image/png, image/gif) that matches the image data being provided.

# Usernames

Usernames not matching the following regex will be invalid:
```
^[A-Za-z0-9_]{4,32}$
```

# CDN Images

All avatars and other images on WhatNow will be hosted on the CDN (base url: `cdn.whatnowapp.com`). Any time this data is present in a response, it will return the file (name.ext) of an image on the CDN. For example, an avatar of a user would be `317876126770790400.png` in an API response, so the link would be http://cdn.whatnowapp.net/317876126770790400.png for the image src.

# Ratelimits

Ratelimiting is done by IP. An IP is not allowed more than 5 requests in 5 seconds, or it will get a response with the JSON code 50003.