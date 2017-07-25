# Create Account
**POST** /register

Returns a new token via the `token` field on success.

### Example Response Body
```
{
	"code": 50000,
	"message": "Success",
	"token": "z596Ujkcsi77n3AYk0QFc6Z2xFcGytQzpICtJarHw8AFdFxvKhJU7Fxub257+j02y/1TA5nxycPQs92CS/Bayg=="
}
```

#### JSON Body
| Field | Type | Description |
| --- | --- | --- |
| username | string | the username of the account you are creating |
| email | string | the email of the account you are creating |
| password | string | the password of the account you are creating |

##### Possible JSON Codes
| Code | Description |
| --- | --- |
| 50000 | The request was successfully fulfilled |
| 50023 | No username was provided |
| 50024 | The username was invalid (did not match necessary regex) |
| 50005 | No email was provided |
| 50007 | The email is not a valid address or is not a .edu email or the email is already in use |
| 50006 | No password was provided |
| 50008 | Password is either less than 6 characters or more than 256 characters |
| 50025 | There was an error sending a verification email |