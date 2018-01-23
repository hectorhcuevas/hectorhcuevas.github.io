---
layout: post
title: Project Benson 
---

# Week 1 & Project Benson
   Week 1 at Metis concluded with the presentation of our cohort's first project, Project Benson. This project entailed gaining familiarity with Python's data exploration capabilities through analysis of New York City's [MTA turnstile data](http://web.mta.info/developers/turnstile.html).   

# Objective
  The objective of Project Benson was to help optimize placement of street teams for WomenTechWomenYes (WTWY); an organization that seeks to increase women's involvement in the tech industry. The street team's goal was to collect emails outside of subway entrances, invite people to the annual gala taking place in early summer, and ultimately gain donations for WTWY's cause. Our team was tasked with analyzing MTA turnstile data to offer insight into the optimal placement of these street teams.  
## Our Approach
  With the objective of gaining support for WTWY's cause, our team sought to target the demographics which we believed would be most sympathetic to the organization's goals. We figured areas in the city with a high concentration of tech companies would be a logical target, being that these tend to be progressive areas in which our target demographic would be more willing and able to contribute to such a cause. Furthermore, we specifically wanted to find out which areas had the highest amount of funding for tech and compare those to our list of frequented subway stops in order to target potential large donors as well. With that in mind, we wanted to target subway stops which had the following factors in common:    
* High overall traffic level  
* Located in an area with the highest concentration of tech companies   
* Located in an area with the highest rates of funding for tech companies  

### Methods & Analysis  
 
  For the turnstile data we also wanted to be strategic in regards to what time period we analyzed. Being that the gala would take place in early summer, it seemed ideal to look at the most recent trends in the months leading up to the event. We were able to scrape and clean data which spanned 90 days from March-May of 2017. Then, to get a broad perspective of subway traffic trends we were able to group entries by station and look at the aggregate entries for each station during the full 90 day span of the data.  
   
  From the aggregate data, we wanted to look at the most trafficked stations only. Figure 1 demonstrates our results for the top 15 stations with the most entries. Most of these stations are concentrated in the Midtown area of Manhattan, with a smaller cluster in lower Manhattan near the financial district and a few others anomalies which are much farther north, though still in Manhattan. As we compared these preliminary results with our data from Build in NYC, it was clear that there was a good deal of overlap between heavily trafficked subway stops and clusters of tech companies. In fact, most of our top 15 stops were located within the 4.5 mile region cited as having the highest concentration of tech companies. (INSERT FIGURE WITH MAP) When we zoom in to individual zip codes and look at those with the highest funding for tech ventures, we again see significant overlap. Because these areas overlap to a large extent with our areas of high tech company density, we also see a few station names crop up on both lists. Our team took note of such stations and decided to zoom in on a single stop for further analysis.
   
![alt text](/Users/hector/Downloads/Entries_total.png)
   
   GRD_CNTRL: Grand Central Station is undoubtedly a consistently heavily trafficked area. It is also conveniently located within our 4.5 mile region previously mentioned. Additionally it is located just blocks from 10016 and 10018 in midtown, two areas on the top 10 list for highest tech funded zip codes. For these reasons, we wanted to use Grand Central as a test case for further analysis. One further point of consideration for our team was that different stations might have varying levels of traffic by day of the week or hours of the day (with the latter being more likely). In Grand Central, March-May of 2017 in particular, weekdays dominated over weekends, with relatively consistent levels through the week and a peak on Thursdays. When we examine traffic on an hourly basis it seems that late evenings are most trafficked in Grand Central Station, with noticeable peaks in early morning and early evening hours being more consistent with rush hours in the city.   

![alt text](/Users/hector/Downloads/GRND_CNTRL.png)
    
### Conclusions
   Which Sations are recommended, why? In the end my team came up with the following list of recommended stations:  
* 34th St-Penn 
* 23rd St 
* 42nd St Grand Central
* 42nd St Times Sq
* Fulton St
* Canal St  
  
   Based on the feedback our team receives, by knowing the amount of volunteers and what their availability is we can further optimize our placement of street teams. The next approach would be to take into account traffic volume at specific stations and for different times of day and days of the week at those stations. 



