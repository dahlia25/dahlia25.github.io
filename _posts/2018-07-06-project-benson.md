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
```


