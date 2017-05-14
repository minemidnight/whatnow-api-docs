#Users
Users are the base of the app. Users each have a profile and can create or participate in parties.

#User Object
|Field|Type|Description|
|---|---|---|
|id|snowflake|the user's id|
|username|string|the user's username|
|avatar|string|link to avatar on CDN|
|verified|boolean|whether or not the user has verified their email|
|email|string|email of user|

#Get User
**GET** /users/{user.id}
Returns a user object for a given user

#Modify User
**PATCH** /users/{user.id}
Modify a user. Returns the updated user object on success
######Valid Paramaters
|Field|Type|
|---|---|
|username|string|
|avatar|integer|
|verified|boolean|

#Get Current Parties
**GET** /users/{user.id}/parties
Returns the [parties](party.md) a user has posted
