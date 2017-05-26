#Snowflakes

Snowflake to timestamp (ms)

```
(id / 4194304) + 1420070400000
```

Test if a snowflake _may be_ valid. This does not mean this snowflake exists, or is necessarily valid but the possibility is high
```
^\d{17,21}$
```

#Avatar Data

Data format example:
```
data:image/jpeg;base64,BASE64_ENCODED_JPEG_IMAGE_DATA
```

Ensure you use the proper header type (image/jpeg, image/png, image/gif) that matches the image data being provided.

#Usernames

Usernames not matching the following regex will be invalid:
```
^[A-Za-z0-9_]{4,32}$
```
