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

#Create User
**POST** /users

#####JSON Parameters
|Field|Type|Description|Required|
|---|---|---|---|
|username|string|the user's username|true|
|email|string|email of user|true|

#Get User
**GET** /users/{user.id}
Returns a user object for a given user

#Modify User
**PATCH** /users/{user.id}
Modify a user. Returns the updated user object on success
######JSON Parameters
|Field|Type|
|---|---|
|username|string|
|avatar|base64 image data|
|verified|boolean|

#Get User Parties
**GET** /users/{user.id}/parties
Returns the [parties](party.md) a user has posted
