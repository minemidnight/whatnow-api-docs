# Attempt Login
**POST** /login

Returns the user's token via the `token` field on success.

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
| email | string | the email of the user that you are trying to log in as |
| password | string | the password of the user you are trying to log in as |

##### Possible JSON Codes
| Code | Description |
| --- | --- |
| 50000 | The request was successfully fulfilled |
| 50004 | You have made too many invalid logins |
| 50005 | No email was provided |
| 50006 | No password was provided |
| 50007 | No account is registered under that email |
| 50008 | The password was not correct |
| 50009 | The user is not verified |
| 50010 | A MFA code (6-digit authentication code) is required |
| 50011 | The MFA code was invalid |

##### Ratelimits
Each failed attempt progressively stacks how long you must wait before trying again. Failed attempts will be reset twenty minutes after your most recent failed attempt.

Login timeout is as such:
* 1 failed attempt - 1 second wait
* 2 failed attempts - 2 second wait
* 3 failed attempts - 4 second wait
* 4 failed attempts - 8 second wait
* 5 failed attempts - 16 second wait
* 6 failed attempts - 32 second wait

This continues infinitely. Example failed login response body:
```
{
	"code": 50004,
	"delayTime": 4000,
	"failedCount": 3,
	"message": "3 failed attempts (4 second delay). 3.432 seconds remaining until you may try again.",
	"timeRemaining": 3432
}
```