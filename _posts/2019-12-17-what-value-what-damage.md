---
title: What Value? What Damage?
tags: [folium, python, choropleth, mapping, disaster relief, real estate, Leaflet.JS, Flask, Heroku]
image: /assets/img/whatvaluewhatdamage.png
style: fill
color: green
description: Creating an interactive choropleth map to display data
---
## Extracting Building Values from Zillow
_Dylan Bailey, Albert Wong, Justin August_, General Assembly Data Science Immersive Fall 2019, SF Campus

## Problem statement

- During a disaster, it is important to model and estimate the potential or forecasted effect of the event, including the projected/forecasted damage.
- Existing indicators of forecasted damage include number of structures within the affected area, number of people in the area, number of households, demographics of the impacted population, etc.
- This project will add an additional indicator: the value of the properties in the affected area. Property values can be estimated according to the market price of houses.
- In this project, the students will leverage property market prices published in different real-estate websites (e.g. Zillow), according to zip codes.

## Data

Sourcing the data for a project like this involved investigating various APIs. Initially our thought was to directly use the [Zillow](http://zillow.com) API. However there are few key limitations:
1. Zillow limits searches to exact addresses, no fuzzy searching or searching by ZIP code only
2. Zillow limits your requests

To address concern 1 we sourced several sample addresses from [OpenAddresses](https://openaddresses.io/). Then for each ZIP code we would fetch the information from the API, aggregate and average them. However while doing this we ran into issue 2 - the API limiting. After some attempts to stage requests, create representative samples, and other statistical methods we realized that there was a need to find another source of data. We stumbled across the [Zillow Research Data at QUANDL](https://www.quandl.com/data/ZILLOW-Zillow-Real-Estate-Research) which made this project come to life. By having an easily queriable, often updated source of data for each ZIP code we were able to progress forward.

Various metadata were needed (ie: rough housing density estimates, rough population estimates) which we found in the [`uszipcode` Python Module](https://uszipcode.readthedocs.io/index.html). This was the most easiliy accessible, stable source of data for this information. Additionally shape files for each ZIP code were sourced from the [US Census](https://www.census.gov/data.html). As an aside - ZIP codes are not geographic areas. They are mail routes as defined by the USPS and mail quantity. As such there are some ZIP codes that only cover PO Boxes that have no shape and thus do not show up on our map.

Data is fetched dynamically from QUANDL based on the age of the data. QUANDL data is updated every week so if the data is older than a week, new data will be fetched. A few issues persist in this demonstration version:
- Some zip codes do not correspond to geographic shapes and those cannot be fetched.
- Zip codes that Zillow does not have data for cannot be fetched


## Damage Modeling

### Damage Functions

Dylan did the bulk of the research in gathering the damage modeling functions. These functions are inserted into the program such that they are easily updatable and changeable.

#### Hurricane Function

- Taken from [research paper](http://digitalcommons.calpoly.edu/cgi/viewcontent.cgi?article=1119&context=crp_fac) by Michael R. Boswell, Robert E. Deyle, Richard A. Smith, and E. Jay Baker at Florida State University 
- Linear Regression model from historical hurricane damage costs and uses 20 independent variables from population, house value, geography and wind.
- Data for population in each zipcode from uszipcode
- Scale for wind was taken from the Saffir-Simpson Hurricane Scale

#### Flood Damage

- Created from [FEMA estimates from 2017 on flood damage estimates](https://www.fema.gov/media-library-data/1499290622913-0bcd74f47bf20aa94998a5a920837710/Flood_Loss_Estimations_2017.pdf)
- Uses table from FEMA estimates for the three categories of houses to calculate damage to each house
- Data for number of houses in each zip-code from us zip-code
- Damage is calculated for each type of house in the zip code (Assumes each house in a zip code is the same category of house.

#### Tornado Damage

- Damages are estimated from [fujita scale for tornados] (https://www.spc.noaa.gov/faq/tornado/f-scale.html)
- Percentage of damage to house estimated and multiplied by the average Zestimate of the houses in each tier.
- Percentage of zip code hit by a tornado is calculated from the area an average tornado covers (1.081 sq miles) divided by the sq miles of the zip code.
- Zestimate for low, medium, and top tier from Quandle based on Zillow data.
- Number of houses in each zip-code from us zip-code

## FLASK Implimentation

Albert handled the bulk of the [Flask](https://www.fullstackpython.com/flask.html) implimentation. We wanted to create a website to allow our user to input zip codes to generated a map with home values and damage estimates. This is where Flask comes in. We have all of our python scripts to generated our map with detail informations on zip codes, but we needed it in html format. Flask allows us to run our scripts and integrate it into HTML templates we created. Anytime our user inputs zip codes they are sent to our python scripts on Flask, it is return back to Flask and sent into our html templates.

## Heroku Implimentation

Post-course Justin created a live web app hosted via [Heroku](http://heroku.com). It is hosted here: [What Value? What Damage? on Heroku](https://what-value-what-damage.herokuapp.com/)

## Future Features

We envisioned several future features that could be developed and improved given time, more data and funding to do the research. These included: 

- Earthquake damage simulator
- Fire damage simulator
- “Drop a pin” functionality
- Improve existing metric functions
- More robust home data using multiple inputs
- Full Leaflet.js implementation
- Aggregate damage estimates for all zip codes

To see our presentation and demostration please use the following links:

- [What Value? What Damage? on Heroku](https://what-value-what-damage.herokuapp.com/)
- [Watch a Video of the App in Action!](media/app_demo.mp4)
- Presentation
	- [Video](media/presentation.mp4)
	- [PDF](media/Damage%20Estimate%20by%20Zipcode.pdf)
	- [Slides](https://docs.google.com/presentation/d/1RO0ZZt118jAWgInrZFqbA0gMPzDycVqmgpj8uQTybpY/edit#slide=id.p)