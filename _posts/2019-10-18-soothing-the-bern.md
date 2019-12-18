---
title: Soothing The Bern
tags: [External Post, Medium, Politics, Sanders, Feel the Bern, Democratic Primary]
style: border
color: warning
description: Currently Bernie Sanders is losing estimated delegates rapidly — approximately 50% already. This points to him not being the nominee in 2020. What will his supporters do in the general election?
---
### /r/SandersforPresident 2016 / 2020 Classification Project
_Justin August_, General Assembly Data Science Immersive Fall 2019


<img src="https://cdn-images-1.medium.com/max/800/1*JPByuN3ffBFUUrc9IkVnJQ.png">

In 2016 after Bernie Sanders did not win the nomination for the Democratic party, Donald Trump was elected. We know that Hilary Clinton lost by only 77 electoral votes even thought she received 2.8 million more individual votes, that fewer than 80% of Sanders’ supporters voted for her and that 1 in 10 of them actually voted for Trump.

<img class="graf-image" data-image-id="1*44-M-CacdKCcgtUj3l113A.png" data-width="1356" data-height="406" src="https://cdn-images-1.medium.com/max/800/1*44-M-CacdKCcgtUj3l113A.png">

<img class="graf-image" data-image-id="1*qrYJg7S7slnjS-meXIVLyQ.png" data-width="1504" data-height="712" src="https://cdn-images-1.medium.com/max/800/1*qrYJg7S7slnjS-meXIVLyQ.png">
<blockquote>Currently Bernie Sanders is losing estimated delegates rapidly — approximately 50% already. This points to him not being the nominee in 2020.</blockquote>


<img class="graf-image" data-image-id="1*bCz36fNV08DBuKgCqfiIDQ.png" data-width="600" data-height="371" src="https://cdn-images-1.medium.com/max/800/1*bCz36fNV08DBuKgCqfiIDQ.png">

A question this raises is what Sanders’ supporters will do in 2020 and how can Democrats respond.

* Can a difference be detected between Bernie Sanders’ supporters in 2016 and 2020 based on Reddit posts to /r/Sandersforpresident.
* What might explain those differences?
* And again — what does this mean for Democrats in 2020?<

To answer this I analyzed the over 300,000 posts to /r/Sandersforpresident from the start of his 2016 campaign until election day 2016 and then from the start of his campaign in 2019 up to the current day. Natural Language Processing was used to detect differences between the two timeframes. There is clearly a detectable difference between the posts made during the 2016 and current campaign.

<img class="graf-image" data-image-id="1*eBSXsYU8vUkjDQocNSlawA.png" data-width="1346" data-height="432" src="https://cdn-images-1.medium.com/max/800/1*eBSXsYU8vUkjDQocNSlawA.png">

<blockquote>This brings up a new point: why is there a difference and what might it mean?</blockquote>
An analysis called Vader was used to detect the positive or negative sentiment of each set of posts. In doing so I was able to detect a difference and classify the posts by sentiment.

<img class="graf-image" data-image-id="1*G-IEfWGkEgGqsjodNnOsQA.png" data-width="1266" data-height="698" src="https://cdn-images-1.medium.com/max/600/1*G-IEfWGkEgGqsjodNnOsQA.png">

The sentiment is clearly lower than the previous campaign. If we assume that high rates of frustration and anger will lead to folks staying home on election day — or voting against the Democrats this is not great news.

When combining the score of the post with the sentiment we get a modified score where positive and negative values of the sentiment score are amplified by multiplying it by the score of the post. Thus a high scored negative post will appear more negative, a highly scored positive post will appear more positive.

<img class="graf-image" data-image-id="1*vYg-SNAl5oPNMX4q-0TszA.png" data-width="1264" data-height="752" src="https://cdn-images-1.medium.com/max/600/1*vYg-SNAl5oPNMX4q-0TszA.png">

This implies two things. The sentiment as magnified by the score is far more variable this year. This could mean that minds are not made up as to what their sentiment and overall feeling is. Sentiment is no worse than last time around — in fact it is nearly perfectly aligned.


## Recommendations

***LISTEN***
- Sanders’ supporters were widely dismissed last time post-convention. It was assumed they would step in line with Democrats. As our earlier statistics show, this did not happen. There are reasons for this and Democrats must be willing to hear them if they want to move forward without repeating 2016.

***REPAIR***
— Listening is a reparative and restorative act. So is change and outreach. There are still hard feelings in the Sanders camp after 2016 and there will probably even more this time around. Warren is beginning to climb upwards very steadily and her similarity in campaign to Sanders’ own can be used positively to appeal to them if framed correctly.
***BUILD***
— The Sanders Movement will continue past the Democratic nomination. By building connections and inroads Democrats have the ability to leverage a network of trust with individuals that they currently may not enjoy. This is critical to getting out the vote in 2020.

## Media Links
- [Google Slides](https://docs.google.com/presentation/d/1TZV8NVPswMl2Ymy6X5-u5bdhoyQTKfAg1AmTA_nRbLg/edit#slide=id.g63cbdd7274_0_20)