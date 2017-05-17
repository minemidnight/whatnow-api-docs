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

Creates a user then returns a user object


#####JSON Parameters
|Field|Type|Description|Required|
|---|---|---|---|
|username|string|the user's username|true|
|email|string|email of user|true|
|password|sha512 string|hashed password of user|true|

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
|password|sha512 string|

#Delete User
**DELETE** /users/{user.id}

Deletes a user. Returns a 204 on success

#Get User Parties
**GET** /users/{user.id}/parties

Returns the [parties](party.md) a user has posted

#Login
**GET** /users/{user.id}/login

Returns a boolean whether or not the password is correct

######Query String Paramaters
|Field|Type|
|---|---|
|password|sha512 string|

