---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Wanderlust API! You can use our API to access Wanderlust API endpoints, which can get information on events and locations.

This example API documentation page was created with [Slate](https://github.com/lord/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Events

## Get All Events

```shell
curl "http://dev.wanderlust.cloud/api/fetch_events_new"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
[
  {
    "_id": "5af18fede09d6f69cc0fba17",
    "rawID": "9862347",
    "source": "eventim",
    "sourceType": "primary",    
    "title": "Backstageführung Disneys Der Glöckner Von Notre Dame",
    "type": "other",
    "otherType": "other",
    "classification": {
      "subTypes": [],
      "genres": [],
      "tags": [],
      "language": "DE"
    },
    "image": "https://www.eventim.de/obj/media/DE-eventim/teaser/222x222/2018/backst...",
    "score": {
      "isScored": false
    },
    "city": "STUTTGART",
    "country": "germany",
    "countryCode": "DE",    
    "performers": [{
      "name": "Venice Band",
      "sourceImage": null,
      "artistID": "5af08c9a39e6306bc0b3b5e"
    }],
    "venue": {
      "name": "YARD CLUB / Die Kantine",
      "address": "Neusser Landstr. 2",
      "sourceInfo": {},
      "venueID": "5af08c9a39e6306bc0b3b5e"
    },
    "location": {
      "type":"Point",
      "coordinates":[8.5499,49.3203]
    },
    "wanderCityID": "639db1baccebf2ef08cc38a2c5da604f",
    "startDate": "2018 - 05 - 11 19: 00: 00.000",
    "startTime": "17:00",
    "localTimezoneOffset": 60,
    "serverTimezoneOffset": -180,    
    "endDate": null,
    "endTime": null,
    "description": {
      "html": "Schauen Sie hinter die Kulissen einer großen Musicalproduktion und sch..."
    },
    "URL": "https://www.eventim.de/tickets.html?affiliate=WFA&fun=evdetail&doc=evd...",
    "currency": "EUR",
    "maxPrice": "19.50",
    "minPrice": "19.50",
    "eventStatus": "on sale",
    "sync": {
      "citySynced": true,
      "artistsSynced": false,
      "venueSynced": true,
      "locationInfo": {
        "source": "event",
        "precision": "city"
      },
      "cityHasNoCoordinates": false
    }
  }
]
```

This endpoint retrieves some events.

### HTTP Request

`GET http://dev.wanderlust.cloud/api/fetch_events_new`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
param1 | false | -----
param2 | true | -----

### Result Parameters

Parameter | Type | Description and/or examples
--------- | ------- | -----------
_id | ObjectId | ID of event in events collection
rawID | string | Internal ID in the event source
source | string | event source name 
sourceType | string | primary, secondary
title | string | event title
type | string | music/sport/other
otherType | string | for "other" types of events. Can be: comedy,musicals/clubbing/dance/classical/other
**classification** | object | >>>
image | string | url to event image. should be https
**score** | object | TODO >>>
city | string | event city (as in event)
country | string | event country (as in event of based on country code)
countryCode | string | event country code (as in event of based on country)
**performers** | array of objects | >>>
---|---|---
>name | string | performer name (as in event). can be artist, sport team or anything else
>sourceImage | string | url to event image. should be https
>artistID | ObjectId | ID of event in artists collection
---|---|---
**venue** | object | >>>
---|---|---
>name | string | performer name (as in event)
>address | string | venue address (as in event)
>*sourceInfo* | object | all venue info from event (if present)
>venueID | ObjectId | ID of event in venues collection
---|---|---
**location** | object | >>>
---|---|---
>type | string | always "Point" for mongo reasons
>coordinates | array | first longitude (-180 to 180), than latitude (-90 to 90)
---|---|---
wanderCityID | string | encoded city id from cities collections 
startDate | string | UTC date+time (optional)
startTime | string | local time 
localTimezoneOffset | integer | time offset of event location in minutes
serverTimezoneOffset | integer | time offset of server in minutes
endDate | string | end date
endTime | string | end time 
**description** | object | can have properties: html and/or txt >>>
---|---|---
>html | string | html description from event
>txt | string | txt description from event
---|---|---
URL | string | link to event 
currency | string | currency (usually 3 letters) 
maxPrice | string | maximum price of the event
startTime | string | minumim price of the event
eventStatus | string | status of the event, can be "on sale" or "cancelled"
**sync** | object | object with flags (we tryed to sync and had some non error result) >>>
---|---|---
>citySynced | boolean | is city synced 
>artistsSynced | boolean | is artist synced
>venueSynced | boolean | is venue synced
>*locationInfo* | object | info how we had found location  >>>
*---*|*---*|*---*
>>source | string | event/venue/city
>>precision | string | exact/city - if we have city precision it can be upgrade with additional searches
*---*|*---*|*---*
>cityHasNoCoordinates | boolean | true if we have found the city in our cities collection, but there were no coordinates there
---|---|---


**classification object**

Parameter | Type | Description and/or examples
--------- | ------- | -----------
subTypes | array | subtypes based on event info like 'Opera'
genres | array | genres based on event info like 'Rock'
tags | array | tags based on event info like 'Festival'

**score object**

Parameter | Type | Description and/or examples
--------- | ------- | -----------
isScored | boolean | is this event scored by us

<aside class="warning">
Work in progress
</aside>
