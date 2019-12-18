---
title: What State Next?
tags: [python, data analysis, explanatory data analysis]
style: fill
color: secondary
description: An analysis of SAT & ACT scores & participation rates by State to advocate for a future target market for College Board marketing
---
_Justin August_, General Assembly Data Science Immersive Fall 2019, SF Campus
<img src="/assets/img/wsn/githubtemplate.png" width="75%">

For this project, we were tasked with gathering two years of data for both the SAT & ACT tests, analyzing them and then providing a recommendation to the marketing team for a state to focus marketing energies on to expand into. We needed to collect, clean, analyze and then present our findings.

Data was sourced from 4 places into 4 .csv files and then imported into a Jupyter Notebook. EDA was conducted using PANDAS and matplotlib.

## Description of Data
    
- [2017 SAT Scores](http://github.com/justinaugust/which-state-next/data/sat_2017.csv) ([source](https://blog.collegevine.com/here-are-the-average-sat-scores-by-state/))
- [2017 ACT Scores](http://github.com/justinaugust/which-state-next/data/act_2017.csv) ([source](https://blog.prepscholar.com/act-scores-by-state-averages-highs-and-lows))
- [2018 SAT Scores](http://github.com/justinaugust/which-state-next/data/sat_2018.csv) ([source](https://reports.collegeboard.org/sat-suite-program-results/state-results))
- [2018 ACT Scores](http://github.com/justinaugust/which-state-next/data/act_2018.csv) ([source](http://www.act.org/content/dam/act/unsecured/documents/cccr2018/Average-Scores-by-State.pdf))

| Feature                       | Type   | Dataset    | Description                                                                 |
|-------------------------------|--------|------------|-----------------------------------------------------------------------------|
| state                         | object | both       | The name of the state that the data refers to                               |
| act_participation_rate_2017   | float  | ACT 2017   | The percentage rate of participation                                        |
| act_english_2017              | float  | ACT 2017   | The average score for the English subtest in 2017                           |
| act_math_2017                 | float  | ACT 2017   | The average score for the Math subtest in 2017                              |
| act_science_2017              | float  | ACT 2017   | The average score for the Science subtest in 2017                           |
| act_reading_2017              | float  | ACT 2017   | The average score for the Reading subtest in 2017                           |
| act_composite_2017            | float  | ACT 2017   | The average composite ACT score in 2017                                     |
| act_participation_rate_2018   | float  | ACT 2018   | The percentage rate of participation                                        |
| act_composite_2018            | float  | ACT 2018   | The average composite ACT score in 2017                                     |
| sat_participation_rate_2017   | float  | SAT 2017   | The percentage rate of participation                                        |
| sat_reading_writing_2017      | float  | SAT 2017   | The average score on the Evidence Based Reading and Writing subtest in 2017 |
| sat_math_2017                 | float  | SAT 2017   | The average score on the Math subtest in 2017                               |
| sat_composite_2017            | float  | SAT 2017   | The average composite score on the SAT in  2017                             |
| sat_participation_rate_2018   | float  | SAT 2018   | The percentage rate of participation                                        |
| sat_reading_writing_2018      | float  | SAT 2018   | The average score on the Evidence Based Reading and Writing subtest in 2018 |
| sat_math_2018                 | float  | SAT 2018   | The average score on the Math subtest in 2018                               |
| sat_composite_2018            | float  | SAT 2018   | The average composite score on the SAT in  2018                             |
| sat_participation_rate_change | float  | Calculated | Calculated change in participation rates between 2017 and 2018              |
| act_participation_rate_change | float  | Calculated | Calculated change in participation rates between 2017 and 2018              |


## Context

<img src="/assets/img/wsn/part_rate_change.png" width="450" style = "float:right" />

Education now exists in a post-Common Core landscape. This means there are harder tests, given more regularly leading parents, schools and students to look for ways to lessen the amount of testing. Some states have moved towards exams such as the ACT & SAT as their High School graduation exam. This has led to spikes in participation in states such as Illinois, Rhode Island and Colorado. West Virginia followed suit in 2017.

In finding new states to target you have to look at the legislative landscape as well. Pushes in states such as Illinois, Rhode Island, and Colorado has moved participation to 100%. West Virginia is en route with new legislation. New Jersey and New York are increasing  at a rate of 12% a year - meaning folks in those states are interested in the College Board's product.

## Target State

<blockquote>“Under the court-approved settlement, the state will allow high school juniors and seniors to graduate if they have passing scores on state PARCC exams or other approved standardized tests, such as the SAT, ACT or the military placement exam.”</blockquote>

<img src="/assets/img/wsn/nj_part.png" width="450" style="float: right" />
As of February a court case in New Jersey has [cleared the way](https://www.northjersey.com/story/news/2019/02/15/2879823002/) for the SAT to be a qualifying graduation requirement for High School Students. This, in addition to already being the market leader, NJ having a large population and families being familiar with us makes NJ a prime market for expansion. Clearly, students and parents in New Jersey are in need of a qualifying test for High School graduation.

Moving forward we have the following potential points of analysis and action:
- Existing customer demographic information
- Graduation requirements per state
- Socioeconomic information of SAT test takers
- Destinations for test-takers & list of colleges that accept/don't accept SAT
- Marketing push based on this information
- Lobbying efforts in New Jersey at a legal level

## Links
- [Google Slides](https://docs.google.com/presentation/d/1VXePQ2neN2fO8sqE3214WL8E1D6flrOuWw4Zy6ZILgk/edit?usp=sharing)
- [Github Repo](https://github.com/justinaugust/which-state-next)