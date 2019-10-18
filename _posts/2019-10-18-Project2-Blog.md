---
layout: post
title: Project 2 Blog
---

For my second project, I wanted to make it about something that is relevant to me. I was not particularly passionate about movies or American sports. So I decided to choose something that probably no one had studied before: table tennis and badminton players. I played table tennis in high school, and people sometimes joked and insinuated it wasn’t a sport. What constituted a sport? I felt like it had to require stamina, strength, and other measures of athleticism to distinguish it from a game like chess. 

Table tennis and badminton are two sports that aren’t very high profile, and I realized that there were no measures of strength or 100m dash times available on these athletes, and the only way I could find something about them was to go to the official ranking websites, fan made pages, or wikipedia. I scraped data about their rankings, and the features I looked for were age, height, weight, and whether they were left-handed.

The four groups of concern are: Top 200 men’s table tennis players; top 200 men’s badminton players’ top 200 women’s badminton players, and top 100 women’s table tennis players (information about this group is the hardest to find so I stuck with top 100 only).  
To transform the data, I took all their ranks and reversed it: the highest ranked player would have the highest “score” Y column. I standardized the heigh to centimeters and the weight to pounds, and I created a column where if the player is left handed, they would get a 1 and 0 if not. 

I had the choice between LASSO, Ridge, and standard Linear Regression. Because I have so few features, I did not want to run a LASSO regression. LASSO regression will zero out certain columns that overcontribute to high overfitting, and since I only had 4 features, I could not risk losing any one of them. A ridge regression on the other hand, does not zero out any features. 

I scored all four data sets and realized that for all four of them a ridge regression gave me a higher r^2 score than linear regression. I then trained and tested my data, and here were the coefficients:

![]({{ site.url }}/images/blog2_1.JPG)
![]({{ site.url }}/images/blog2_2.JPG)
![]({{ site.url }}/images/blog2_3.JPG)
![]({{ site.url }}/images/blog2_4.JPG)

Notice that height is negatively correlated with success in women’s table tennis—this is due to the game being more focused on speed and agility rather than power—higher leverage comes from a longer body.
Age is more important in badminton, where experience may be playing a higher role; whereas in table tennis the youngers are favored. 
For women’s badminton and men’s table tennis, left handed players are preferred. Notice that in the other two sports, left handed players aren’t not preferred. This perhaps is an testament to the natural advantage of left handers being a rarer kind of opponent. 


I initially planned to scale all four data sets: for each point of height, weight, age, scale it into the z-score, i.e. “how many standard deviations from that group mean.” But seeing that all four data sets have such different results, I decided to present them as such. 