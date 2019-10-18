---
layout: post
title: Post for Project 1
---

This  was our first project, and our task was to gather data about the MTA turnstiles and find how our clients should set up to get the most traffic and to reach the most people.

After downloading one week’s data in NY, our initial step was to ID each turnstile by combining the “Station” and “SCP” values. We then realized that each row gave us an “cumulative” turnstile count rather than what actually happened during that 4-hour window. By taking the difference, we have what is a measure of traffic at the turnstile.

Our dataframe initially very messy and had tons of 0s and negatives, and we also encountered rows that said one turnstile had tens of millions of people going in over some 4 hour window. Upon examination, we realized that the turnstiles that had these absurdly large numbers were almost always the turnstiles that also yielded some negative numbers. So, to deal with this, we did a policy where if any turnstile gave a negative number in that week, we would “distrust” it altogether and remove all its entries for the data in that week. Now, with much cleaner and more precise turnstile data, for each station we got its total by summing across all turnstiles in that station (for each 4 hour window given).

While our initial approach was to find the station with the highest average traffic, we thought that to be more rigorous, we needed a better metric. Our client was going to deploy people to a few subway stations, and they are likely not going to be able to camp there for more than a few hours. So, what we needed to do was to find the stations with the highest average PEAK traffic. Plotting out the traffic for a station:


![test]({{ site.url }}/images/blog1_1.JPG)


We wanted to find the stations with the consistently highest peaks. So we created 7 more dataframes from the above process and put them all together, grouped by station, found their max, and averaged them. Here are our results:

![test]({{ site.url }}/images/blog1_2.JPG)