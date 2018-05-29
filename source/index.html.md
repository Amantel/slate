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
    "city": "STUTTGART",
    "country": "germany",
    "countryCode": "DE",
    "location": {},
    "wanderCityID": "639db1baccebf2ef08cc38a2c5da604f",
    "startDate": "2018 - 05 - 11 19: 00: 00.000",
    "startTime": "17:00",
    "localTimezoneOffset": 60,
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
    "serverTimezoneOffset": -180,
    "sync": {
      "citySynced": true,
      "artistsSynced": false,
      "venueSynced": true,
      "locationInfo": {
        "source": "exact",
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
classification | object | ---




<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>
