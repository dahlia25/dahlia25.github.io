---
layout: post
title: Yelp Search Querying with Project Benson
---
# Project Benson: How to query with Yelp's API

## Introduction

Project Benson enabled the opportunity to work with the NYC MTA turnstile data. The MTA turnstile data can be found [here](http://web.mta.info/developers/turnstile.html).The Yelp API was also used as an external source for more data support. This post will focus on how to utilize and leverage Yelp's API.

### Install the Yelp API module

For first-timers, the *yelpapi* module needs to be installed to be able to query through Yelp. This can be done in the following two ways:

```
pip install yelpapi
```

Or if you prefer using Anaconda:

```
conda install yelpapi
```

### Get an API Key from Yelp

In order to obtain an API key from Yelp:

1. Create a Yelp account.
2. Create an app; this will allow you to obtain an API key.
3. Note the Request GET url; you will need to use this url in your Python Notebook.

### Importing YelpAPI

*All work will be shown using Jupyter Notebook, Python 3.*

Import the *YelpAPI* module and *requests*:

```
from yelpapi import YelpAPI
import requests

response = requests.get('https://api.yelp.com/v3/businesses/search')

api_key = '<put API key here>'

yelp_api = YelpAPI(api_key)

response = yelp_api.search_query(categories = ['restaurants'], location = 'New York')
```

The coordinates (i.e. latitude and longitude) of specified NYC subway stations could be found by inputting stations names into the *location* parameter. 

Yelp's **search_query** function is used to search for nearby businesses for a given location/address. It will output a dictionary with lists of all nearby businesses.

A function was defined to pass a list of locations/addresses to obtain the coordinates for the passed list:

```
def get_long_lat(location_list):
    longitude = []
    latitude = []
    for loc in location_list:
        response = yelp_api.search_query(location = loc)
        longitude.append(response['businesses'][0]['coordinates']['longitude'])
        latitude.append(response['businesses'][0]['coordinates']['latitude'])
    return(longitude, latitude)

locations = ['ASTORIA DITMARS', 'YORK ST', '14 ST-UNION SQ', 'NEWARK C', 'MYRTLE AV', '1 AV, NY', 'W 4 ST-WASH SQ', 'BEDFORD AV', 'GRAND CENTRAL - 42 ST', '34 ST - HERALD SQ']

result = get_long_lat(locations)

df = pd.DataFrame()
df['location'] = locations
df['longitude'] = result[0]
df['latitude'] = result[1]
```

The output of the code mentioned above should produce a pandas dataframe like this:

| location | longitude | latitude |
| --- | --- | --- |
| ASTORIA DITMARS | -73.909217 | 40.775323 |
| --- | --- | --- |
| YORK ST | -73.993416 | 40.702615 |
| --- | --- | --- |
|14 ST-UNION SQ | -73.991055 | 40.734267 |
| --- | --- | --- |

### What did we do with the coordinate data?

The obtained coordinates were used to map out all nearby restaurants near all specified NYC subway stations to achieve desired results.

### Summary

Yelp's API can be used to query many different things. Yelp offers different types of queries. A list of different queries can be found [here](https://www.yelp.com/developers/documentation/v3/business).
