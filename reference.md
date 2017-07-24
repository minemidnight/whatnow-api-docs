# Receiving Data (REST)

All responses will have a "message" field holding a human-readable response about the request. Any successful responses will always have the "data" field with the result. All errors are communicated through HTTP error codes.

# Snowflakes

Snowflake to timestamp (ms)

```
(id / 4194304) + 1420070400000
```

Test if a snowflake _may be_ valid. This does not mean this snowflake exists, or is necessarily valid but the possibility is high
```
^\d{17,21}$
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

All thumbnails, avatars and other pictures necessary will be hosted on the CDN (base url: `cdn.whatnow.com`). Any time this data is present, it will return the file (name.ext) of an image on the CDN. For example, an avatar of a user holds the data `317876126770790400.png`, so the link would be http://cdn.whatnow.com/317876126770790400.png for the real image.
