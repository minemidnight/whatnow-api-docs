#Parties

Parties are the main function of the app. Users post parties for other users to show up to them. A party is deleted a week after it was hosted.

#Party Object
|Field|Type|Description|
|---|---|---|
|id|snowflake|the party's id|
|host|snowflake|user id of the party host|
|name|string|the name of the party|
|time|integer|the time the party starts (in ms)|
|location|string|the location of the party|
|description|string|the description of the party|
|premium|boolean|if a party has paid for extra advertising|
|price|integer|price a user has to pay to participate in the party (upon arriving)|
|thumbnail|string|link to CDN image of thumbnail for party|

#Get Parties
**GET** /parties

Returns an array of parties


######Query String Paramaters
|Field|Type|Description|Default|
|---|---|---|---|
|limit|integer|maximum number of parties to return (1-20)|20|
|after|snowflake|get parties after this party id|absent|
|premium|boolean|if all parties returned are premium|false|
|pricemax|integer|get no parties above this price|absent|
|pricemin|integer|get no parties less than this price|0|

#Get Party
**GET** /parties/{party.id}

Returns a party object

#Create Party
**POST** /parties

Creates a party


######JSON Paramaters
|Field|Type|Description|
|---|---|---|
|host|snowflake|user id of the party host|
|name|string|the name of the party|
|time|integer|the time the party starts (in ms)|
|location|string|the location of the party|
|description|string|the description of the party|
|premium|boolean|if a party has paid for extra advertising|
|price|integer|price a user has to pay to participate in the party (upon arriving)|
|thumbnail|base64 image data|thumbnail for the party|

#Modify Party
**PATCH** /parties/{party.id}

Modifies a party. Returns the new party object

######JSON Paramaters
|Field|Type|Description|
|---|---|---|
|name|string|the name of the party|
|time|integer|the time the party starts (in ms)|
|location|string|the location of the party|
|description|string|the description of the party|
|premium|boolean|if a party has paid for extra advertising|
|price|integer|price a user has to pay to participate in the party (upon arriving)|
|thumbnail|base64 image data|thumbnail for the party|

#Delete Party
**DELETE** /parties/{party.id}

Deletes a party. Returns a 204 on success

