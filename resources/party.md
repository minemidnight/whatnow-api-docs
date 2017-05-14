#Parties
Parties are the main function of the app. Users post parties for other users to show up to them.

#Party Object
|Field|Type|Description|
|---|---|---|
|id|snowflake|the party's id|
|host|snowflake|user id of the party host|
|name|string|the name of the party|
|time|integer|the time the party starts (in ms)|
|location|string|the location of the party|
|description|string|the description of the party|

#Get Parties
**GET** /parties
Returns an array of parties

######Query String Paramaters
|Field|Type|Description|Default|
|---|---|---|---|
|limit|integer|maximum number of parties to return (1-20)|20|
|after|snowflake|get parties after this party id|absent|

#Get Party
**GET** /parties/{party.id}
Returns a party object

#Create Party
**POST** /parties
Creates a [party](party.md)

######JSON Paramaters
|Field|Type|Description|
|---|---|---|
|host|snowflake|user id of the party host|
|name|string|the name of the party|
|time|integer|the time the party starts (in ms)|
|location|string|the location of the party|
|description|string|the description of the party|

#Modify Party
**PATCH** /parties/{party.id}

######JSON Paramaters
|Field|Type|Description|
|---|---|---|
|name|string|the name of the party|
|time|integer|the time the party starts (in ms)|
|location|string|the location of the party|
|description|string|the description of the party|

#Delete Party
**DELETE** /parties/{party.id}
Deletes a party. Returns a 204 on success

