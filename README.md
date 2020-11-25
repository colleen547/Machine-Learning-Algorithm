# Final-Project---Team-9

Team 9: Chris Hauck, Colleen Banzhof, Ken Njema, Eric Lewiston

## Origin of Global Music

***

Website Link: TODO

Our goal is to use machine learning to attempt to predict where a song originated from by using various characteristics of that song. The data set we're using contains 1095 tracks from 33 different countries, and only includes traditional, ethnic or 'world' only. Western music is not included as it's reach and influence is global.

## Data Origin

***

This song data was generated using a program called [MARSYAS](http://marsyas.info/) (Music Analysis, Retrieval and Synthesis for Audio Signals). MARSYAS is an open source audio processing framework. For more information on how the data was generated, visit the link below.

[Link to data set](http://archive.ics.uci.edu/ml/datasets/geographical+original+of+music)

Data set citation:

Fang Zhou, Claire Q and Ross. D. King
Predicting the Geographical Origin of Music, ICDM, 2014

## Data Cleaning

***

The existing data itself requried no cleaning. Instead, we had to add to the existing data by finding the country. Instead of providing the country, the data set provides the latitude and longitude of the capital for a given country.

We expected that attempting to predict an exact country would be too granular, and instead we opted to break the world up into region and sub-region delinations. This process is based on the United Nations [UN M49](https://en.wikipedia.org/wiki/UN_M49) area codes.

We obtained the UN M49 area codes using Pandas read HTML function, along with [all countries, their two letter country code, and their given area codes](https://en.wikipedia.org/wiki/List_of_countries_by_United_Nations_geoscheme).

Using the Google geocoding API, we obtained the two letter country code for the given coordinates. This two letter code was compared to our UN area code dataframe to find the region and sub-region for each country.

### Inconsitencies

* For the UN M49 system, South America is the only continent that doesn't contain any subregions.

* The UN doesn't recognize Taiwan as a country, but our data set does. We decided to manually assign Taiwan in the Asia/East Asia region/sub-region.

### To reproduce cleaning

* Use NewPythonData environment for data cleaning
* Add config.py file to project directory
  * Add to config.py: gkey = 'Your geocoding api key here'
* Launch and run all of Global Regions.ipynb
* Launch and run all of Clean Data.ipynb
