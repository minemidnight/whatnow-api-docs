# Parties

Parties are the main function of the app. Users post parties for other users to show up to them. A party is deleted a week after it was hosted.

# Party Object
| Field | Type | Description |
| --- | --- | --- |
| id | snowflake | the party's id |
| host | snowflake | user id that posted the party |
| name | string | the name of the party |
| time | integer | the time the party starts (in ms) |
| address | string | the address of the party |
| description | string | the description of the party |
| premium | boolean | if the party host has paid for extra advertising |
| price | integer | price a user has to pay to participate in the party (upon arriving, in USD) |

## Example Party Object
```
{
	"id": "69190438279446528",
	"host": "213401534254415882"
	"name": "super cool party",
	"time": 1500953413570,
	"address": "30 Cool Street, New York City, NY,
	"description": "Cool party with loud music!",
	"premium": false,
	"price": 15
}
```

# Get Parties
**GET** /parties

Returns an array of parties

### Example Response Body
```
{
	"code": 50000,
	"message": "Success",
	"parties": [{ party object }, { party object }]
}
```

#### Query String Paramaters
| Field | Type | Description | Default |
| --- | --- | --- | --- |
| limit | integer | maximum number of parties to return (1-20) | 20 |
| offset | integer | how many parties to offset the results by | 0 |
| premium | boolean | whether or not to only return parties that are premium | false |
| minprice | integer | get no parties less than this price | 0 |
| maxprice | integer | get no parties above this price | 100 |

##### Possible JSON Codes
| Code | Description |
| --- | --- |
| 50000 | The request was successfully fulfilled |
| 50012 | The party limit was less than 1, over 20, or not a number |
| 50013 | The minimum price was less than 0, the maximum price was over 100, the minimum price was more than the maximum price, or one of them was not a number |

# Get Party
**GET** /parties/{party.id}

Returns a party object

### Example Response Body
```
{
	"code": 50000,
	"message": "Success",
	"party": { party object } }
```

##### Possible JSON Codes
| Code | Description |
| --- | --- |
| 50000 | The request was successfully fulfilled |
| 50021 | The party requested was not found |

# Create Party
**POST** /parties

Creates a party

### Example Response Body
```
{
	"code": 50000,
	"message": "Success",
	"party": { party object }
}
```

#### JSON Paramaters
| Field | Type | Description |
| --- | --- | --- |
| host | snowflake | user id of the party host |
| name | string | the name of the party |
| time | integer | the time the party starts (in ms) |
| address | string | the address of the party |
| description | string | the description of the party |
| premium | boolean | if a party has paid for extra advertising |
| price | integer | price a user has to pay to participate in the party (upon arriving) |

##### Possible JSON Codes
| Code | Description |
| --- | --- |
| 50000 | The response was successfully fulfilled |
| 50014 | No party name was given |
| 50032 | The party name was over 32 characters long |
| 50015 | No party time was given |
| 50016 | The timestamp was not a number or not in milliseconds |
| 50017 | No party address was given |
| 50018 | No description was given |
| 50031 | Description is over 600 characters |
| 50019 | Price is not a number, less than 0, or over 100 |

# Modify Party
**PATCH** /parties/{party.id}

Modifies a party. Returns the new party object. If the party is not modified it returns a HTTP status code of 304 with no body. Only parties the user corresponding to the token in use owns can be edited.

### Example Response Body
```
{
	"code": 50000,
	"message": "Success",
	"party": { party object }
}
```

#### JSON Paramaters
| Field | Type | Description |
| --- | --- | --- |
| name | string | the name of the party |
| time | integer | the time the party starts (in ms) |
| address | string | the address of the party |
| description | string | the description of the party |
| premium | boolean | if a party has paid for extra advertising |
| price | integer | price a user has to pay to participate in the party (upon arriving) |

##### Possible JSON Codes
| Code | Description |
| --- | --- |
| 50000 | The response was successfully fulfilled |
| 50032 | The party name was over 32 characters long |
| 50016 | The timestamp was not a number or not in milliseconds |
| 50031 | Description is over 600 characters |
| 50019 | Price is not a number, less than 0, or over 100 |

# Delete Party
**DELETE** /parties/{party.id}

Deletes a party. Returns a HTTP status code of 204 with no body on success.

##### Possible JSON Codes 
| Code | Description |
| --- | --- |
| 50022 | The party is not owned by the user trying to delete it |
| 50010 | A MFA code (6-digit authentication code) is required |
| 50011 | The MFA code was invalid |
| 50021 | The requested party was not found | 
