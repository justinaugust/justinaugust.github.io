---
title: Who's Serving Who?
tags: [altair, vega, vega-lite, python, mapping, education, data analysis, social justice, equity, Flask, Heroku]
style: border
color: primary
description: Creating a visual tool to find a school that best suits your child
---

[<img src="/assets/img/wsw_ss.png">](https://who-serving-who.herokuapp.com/)

## General Assembly DSI Capstone Project
_Justin August_, General Assembly Data Science Immersive Fall 2019, SF Campus

## Context

Oakland Schools in 2019 face many challenges and thus so do parents and students when deciding where to send their child. Due to the low overall achievement of Oakland's schools, each student is eligible to request placement in another school. Historically the "desirable" schools have been located in predominately affluent, whiter areas of the city with those students' outcomes skewing the overall results.

How and where should parents of color and other traditionally marginalized groups look to find a school that has high student outcomes for children like their own?

What exists now is the seedling of a larger project that I hope to grow over time. Details for the larger project are:

|Goal / Outcome|Audience|Metrics|
|---|---|---|---|---|---|---|
|Create a model that can predict a child's probability of achieving different success metrics at each school. Based on widely aggregated data such as socioeconomic indicators, learning differences, gender/sex, race/ethnicity, etc. Turn this into a web app where you can enter this information in - or exclude some - to find out the probability of schools serving your child well based on an outcome of your choosing.|Parents, Students|GPA, College Acceptance, Reading levels, Math Levels, High Stakes Tests, SAT/ACT Scores, High School graduation rates|

|Data Source|Pros|Cons|Reasonability|
|---|---|---|---|
|State school information, ??|Content Knowledge, usable, important|Lots of data, perhaps too mission critical for some?|Initial Component|

After beginning the code and working with the data and my timeline for my academic program some revisions were made to the project. Features were shrunk down to include only 2018 CAASSP data, to create an interactive online map, to include an SQL backend using [SQLAlchemy](https://www.sqlalchemy.org/) and [PostGRES](https://www.postgresql.org/), and have two sets of maps - one dynamic and one static.

## Data
Data was gathered primary from the California Department of Education's [Research Files](https://caaspp-elpac.cde.ca.gov/caaspp/ResearchFileList?ps=true&lstTestYear=2019&lstTestType=B&lstCounty=00&lstDistrict=00000&lstSchool=0000000). These are the standardized, official research files provided by the State to be used for projects like this. I included metada from [National Center of Education Statistics](https://nces.ed.gov/ccd/schoolsearch/), which included details regarding school location and other information. Additionally a shape file was sourced from [the City of Oakland](https://data.oaklandnet.com/Property/City-of-Oakland-City-Limits/9bhq-yt6w). To store the data it was converted from `csv` files into my `PostgresSQL` backend.

#### PostgresSQL Structure

After loading in the data, the structure was as follows:

|Name|Description|
|---|---|
|who serving who|DB containing tables|
|caaspp metadata|Table containing metadata of schools such as addresses, lat/long, charter status, etc|
|caaspp_2019 entities| Table describing entities with results (districts, schools)|
|caaspp subgroups| Table with descriptive data for demographic subgroups|
|caaspp tests|Table with descriptive data for CAASPP Tests|
|caaspp_2019|Main table with results for each entity by test, subgroup and grade|


## Intersectional Analysis Equity Scoring

When looking at evaluating the schools, the initial plan was to create a "Balanced Equity Score" based on impact of demographic on outcome. For example:
- If being a girl raises average reading score by 10% and being White raises it by 20% how would reflect the impact on potential achievement at a school?

Currently I am unable to pursue this due to two main reasons:
- Assumption of equal distribution creates false confidence in outcomes
- Per-student scoring and demographic information needed to accurately calculate

This is a ***high priority*** for me in this project and will be pursuing it as I go forward.
Currently the "Balanced Equity Score" is created by:
1. Averaging proficiency levels of all grades in school level (ie: 3rd, 4th, 5th in Elementary).
2. Averages proficiency levels of demographics to create “Equity Score"

For example:
- 50% of girls are proficient
- 60% of White students are proficient
The algorithm assumes 55% of white girls are proficient. It is understood that this is ***ideal*** for long-term, production usage and does not reflect the myriad of ways in which identities interact to produce outcomes. Future iterations hopefully include a Balanced Equity Score based on a predictive model that uses demographics as inputs alongside other metadata about the school.

## Visualization

[Altair](https://altair-viz.github.io/) was used to create interactive visualizations. It provides a wrapper for Python to create [Vega](https://vega.github.io/vega/) visualizations. Vega and Vega-Lite allows for interactive and complex visualizations with transformations of data native to the syntax and are embeddable in web pages and apps. Two types of maps were created:
- School Level
- Intersectional Identity

### School Level Maps

<img src="/assets/img/school_level.png" width="300" style="float: right;">

- Show performance in the whole district
- Can see performance differences change dynamically
- Able to drill down by components of the “Equity Score”
- More of an exploratory tool
- Demographic Selectors
- School Selectors
- Dynamically changes
- Shows % of Students in that Demographic Meeting or Exceeding State Standards

<hr style="clear: both">

### Intersectional Identity Maps

<img src="/assets/img/intersectional.png" width="300" style="float: right;">

- Allow you to customize it “for you”
- Easily shareable
- Use the “Equity Score” which can be updated in the future to include more components
- User Inputs:
	- School Level
	- Demographic Information
- Shows “Equity Score”
- Shareable by links
- 
<hr style="clear: both">

## Web Access
Web access was a two-stage process. First it was demo'd locally using  [Flask](https://www.fullstackpython.com/flask.html). Using this I was able to create a fully interactive web app. Then I used [Heroku](http://heroku.com) to launch it live on the web. Heroku allows for deployment of Flask-based Python apps to the web and features native Postgres support. You can demo the app here: [Who's Serving Who on Heroku](http://who-serving-who.heroku-app.com).


## Future Plans

### Moving Slow & Not Breaking Things
The reality is that technologies and apps such as this are often written by people who look like me (White, Straight, Cis-Men) without much thought about impacts that are unintended. My goal in making this was to be thoughtful about the disparate impacts it could have.

|Pros|Cons|
|---|---|
|Increased access of information to parents |Increased segregation of students|
|Matching students to schools | Justification for school closures|
|Uses an Intersectional Identity first approach | Does not address underlying issues of different achievement levels|
| |Currently based solely on high stakes testing |

In order to address some of these concerns, there are many features that I want to add:

### Immediate Feature Additions
- Historical trendlines for proficiency scores
- GreatSchools API Information
- School Level reports

### Long-Term Feature Additions
- Inclusion of non-High Stakes test metrics
	- Attendance
	- Teacher Tenure
	- Staff Makeup
	- Pedagogical Outlook
- Mobile-friendly
- Commute Calculation

For more information please [email Justin](mailto:justinaugust+whoservingwho@gmail.com). 

## Media Demonstration Links
- [Google Slides](https://docs.google.com/presentation/d/1DCa1Db2Y9ZnPJ1c0GazXoVGmBHjDkCz7hdzOmm3LE64/edit?usp=sharing)
- [App Website](https://who-serving-who.herokuapp.com/)
