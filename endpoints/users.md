# Users
Users are the base of the app. Users each have a profile and can create parties. Any user id can replaced with @me to represent the user that the token in use belongs to.

# User Object
| Field | Type | Description |
| --- | --- | --- |
| id | snowflake | the user's id |
| username | string | the user's username |
| email | string | email of user |
| avatar | string | CDN image file |
| verified | boolean | whether or not the user has verified their email |
| mfa | boolean | if the user has multi-factor authentication enabled |

## Example User Object
The email field is only returned when a user is interacting with theirselves.
```
{
	"id": "69190438279446528",
	"username": "minemidnight",
	"email": "john.smith@example.com",
	"avatar": "155112606661607425.png",
	"verified": true,
	"mfa": true
}
```

# Get User
**GET** /users/{user.id}

Returns a user object for a given user. If the user is not the user that the token in use belongs to, the `email` field in the user object will be absent.

### Example Response Body
```
{
	"code": 50000,
	"message": "Success",
	"user": { user object }
}
```

##### Possible JSON Codes
| Code | Description |
| --- | --- |
| 50000 | The request was fulfilled successfully |
| 50026 | The requested user was not found |

# Modify User
**PATCH** /users/{user.id}

Modify a user. Returns the updated user object on success. If the user is not modified it returns a HTTP status code of 304 with no body. If the password is changed, the response has a `token` field instead of the `user` field, and the token used for this request is no longer valid. Users can only edit their own account.

### Example Response Bodies
M"FA turned on": 
```
{
	"code": 50000,
	"message": "Success",
	"user": { user object },
	"otpURL": "otpauth://totp/john.smith%40example.edu?secret=MR4FWVTOG4XE43CRLURUY6R6O45F4VCQHB3G6YLHPA6CYU3BLIVA&issuer=WhatNow"
}
```

Password not changed:
```
{
	"code": 50000,
	"message": "Success",
	"user": { user object }
}
```

Password changed:
```
{
	"code": 50000,
	"message": "Success",
	"token": "z596Ujkcsi77n3AYk0QFc6Z2xFcGytQzpICtJarHw8AFdFxvKhJU7Fxub257+j02y/1TA5nxycPQs92CS/Bayg=="
}
```

#### JSON Parameters
| Field | Type |
| --- | --- |
| username | string |
| mfa | boolean |
| avatar | base64 image data |
| password | string |

##### Possible JSON Codes
| Code | Description |
| --- | --- |
| 50000 | The request was fulfilled successfully |
| 50027 | Attempt to edit a user that is not the user corresponding to the token in use |
| 50008 | The new password is less than 6 or more than 256 characters long |
| 50028 | Multi-factor authentication is already enabled for the user |
| 50029 | Multi-factor authentication is already disabled for the user |
| 50020 | The image data provided is not valid (see [Reference](../reference.md)) |
| 50010 | A MFA code (6-digit authentication code) is required |
| 50011 | The MFA code was invalid |

# Delete User
**DELETE** /users/{user.id}

Deletes a user. Returns a HTTP status code of 204 with no body on success.

##### Possible JSON Codes 
| Code | Description |
| --- | --- |
| 50027 | Attempt to delete a user that is not the user corresponding to the token in use |
| 50010 | A MFA code (6-digit authentication code) is required |
| 50011 | The MFA code was invalid |
| 50026 | The requested user was not found | 

# Get User Parties
**GET** /users/{user.id}/parties

Returns an array of [parties](parties.md) a user has posted

### Example Response Body
```
{
	"code": 50000,
	"message": "Success",
	"parties": [{ party object }, { party object }]
}
```

##### Possible JSON Codes
| Code | Description |
| --- | --- |
| 50000 | The request was fulfilled successfully |
| 50026 | The requested user was not found | 