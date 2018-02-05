---
layout: post
title: Predicting Obesity Rates A Global Perspective
---

# Project Luther: Weeks 2-3
&nbsp;&nbsp;&nbsp;Our second and third weeks at Metis were focused on learning the fundamentals of predictive modeling using linear regression. Additionally, data gathering was expanded to web-scraping using Beautiful Soup 4 and Selium. Model selection and generalization methods were also incorporated as essential parts of this project.


# Objective

&nbsp;&nbsp;&nbsp;The objective of my project was predicting rates of obesity in a country based off certain characteristics (mostly socio-economic). Obesity is defined as a BMI (Weight(KG)/Height(m^2) greater than 30. Obesity is an arbitrary yet meaningful measure of someone's body composition. It is neither a trivial nor simply aesthetic problem; being obese has been strongly linked to a multitude of diseases and other health problems. Consequently countries with a large obesity rate must carry the immense costs; primarily in health care, but also in everyday activities like productivity, transportation, waste, etc. In the U.S. alone, obesity- related healthcare expenses account for 21% of total annual healthcare expenses, [about $190 billion and an additional $4.3 billion for obesity-related absenteeism at work](http://www.healthycommunitieshealthyfuture.org/learn-the-facts/economic-costs-of-obesity/).  

&nbsp;&nbsp;&nbsp;While many developed countries (ie USA) are already >35% obese and suffering growing consequences as a result, many developing countries are seeing an exponential growth in obese population. Some even have the dual-problem of feeding starving populations while trying to deal with rising obesity rates. Regardless, many are surprised to learn that today more people die from an over- abundance of food, rather than a shortage. If there is no intervention, this trend will only increase as more countries join the developed world. With [1 in 2 adults globally are projected to be obese by 2050](http://www.telegraph.co.uk/news/uknews/1566436/Half-of-adults-will-be-obese-by-2050.html), and trillions of dollars at stake, it's clearly crucial from a policy perspective to better understand this epidemic.


# Data

&nbsp;&nbsp;&nbsp;Obesity rates, our target variable, were scraped from the web using BeautifulSoup 4. The data was extracted from a table from [Renew Bariatics](https://renewbariatrics.com/obesity-rank-by-countries/).
From there, data were cleaned and stripped of commas, percentage signs, etc. in order to process and run analysis in our pandas dataframe. The end result was a dataframe of 154 countries by name and their respective obesity rates. The remainder of our variables were dependednt and came from a variety of government and NGO sourcers (IMF,CIA,UN, and WHO) and were merged with the initial obesity data by country name.

The remaining dependent variables in my model were:
  * Education (Index)
  * Activity- % of Population Insufficiently Active
  * Region of World (Oceania,Arab States, Europe)
  * log of GDP Per Capita
  * log of Imports
  * Globalization (Index)

&nbsp;&nbsp;&nbsp;Not all regions of the world were found to be particularly useful or statistically significant in my model, hence only Oceania, Arab States, and Europe were taken into account as categorical variables. GDP per capita and imports were both changed via log transformation in order to obtain a more normal distribution of these characteristice, as both can vary by orders of magnitute between countries. Globalization is an index which takes into account social, political, and economic integration between that country and the international community. While these were the variables included in my final model which I'll discuss shortly, I began my investigation with some exploratory data analysis on some of my more noteworthy variables.

## A Global Snapshot

&nbsp;&nbsp;&nbsp;*Figure 1* below gives us a general idea of where obesity is most prevalent. For the purposes of this analysis, we will refer to Arab States, which is inclusive of Middle East and North African states. In regards to the Oceania region which is also included in the analysis, we mean the small pacific islands excluding New Zealand and Australia 

![Figure 1](/images/Global_Map.png)

# Methods 

## Variable Selection
The approach for this investigation began by looking at broad measures of a country's wealth and well-being. From there, I added additional variables which had smaller overall effects but did contribute to the accuracy of predictions. The first dependent variable which came to mind was a measure of a population's activity level.
### Activity Levels
&nbsp;&nbsp;&nbsp;Detailed data on such a broad spectrum of countries is logisticaly difficult to collect, but I made due with a measure of what the [WHO](http://www.who.int/gho/ncd/risk_factors/physical_activity_text/en/) calls 'insufficiently active'; meaning an individual does not meet the minimum standards of activity they've set for individuals to stay healthy. While there was a positive correlation, the interval for which we can correctly predict obesity based only on percentage of population not sufficiently active was less accurate for particularly low and high values. Southeast Asian countries, for example, were found to have some of the highest percentages of their population be insufficiently active, yet these same countries also have some of the lowest obesity rates. It was clear I'd have to look elsewhere  for additional dependent variables in order to more accurately predict obesity as activity level alone made for an insufficient model.

### GDP per capita
&nbsp;&nbsp;&nbsp;As previously mentioned, obesity tends to be a bigger problem in wealthy countries like the US and westen Europe. When comparing relative wealth between countries GDP per capita is a standard measurement, so I decided to use it as a dependent variable to see if wealthier countries tended to have higher obesity rates. GDP per capita and obesity rates are indeed correlated, and appear to be an even better indicater than levels of activity. Still, my model's performance was sub-par, and I felt adding a bit more nuance than simply looking at activity and wealth would help my model make better predictions.

### Education
&nbsp;&nbsp;&nbsp;One thing I particularly wanted to account for was the fact that while some countries have high GDP's, this doesn't necessarily translate into a modern and progressive state. Some countries are extraordinarily wealthy overall but this wealth doesn't get passed on to the entirety of the population or even institutions of governance, education, and other public services. I wanted to account for this by including a more holistic measure of overall development of a country, so I turned next to the human development index. 

&nbsp;&nbsp;&nbsp;HDI indeed made my model more accurate, but one issue with HDI was that it also took health and life expectancy into account, which we can assume are being impacted by obesity rates.  Being that my model was attempting to predict high obesity rates, I found that simply taking the education index from HDI turned out to be a more effective variable to include.

### Summary of Feature Variables
&nbsp;&nbsp;&nbsp;*Figure 2* below demonstrates how well the dependent variables I've discussed predict obesity on their own.

![Figure 2](/images/Subplots.png)

&nbsp;&nbsp;&nbsp;Education turned out to be one of the most impactful coefficients in my model. The slope of my curve was almost entirely predicated on it and GDP per capita. Finally, I included a variable for a country's imports and level of globalization with the idea that countries more integrated with the international community would tend to have preferences similar to those of wealthier (and more obese) countries, and hench might be more likely to be obese themselves. Furthermore, imports might further contribute to obesity by bringing modern gadgets (TVs, computers, etc) that might lead populations to adopt a more sedentary lifestyle. 

&nbsp;&nbsp;&nbsp;In the end, with my other variables accounted for, imports and globalization had a somewhat unexpected effect on obesity rates. Imports had only a slight effect, and to the extent they did effect obesity, the relationship appears to be negative. In regards to globalization, the variable only had a slight effect on two regions; Asia and Arab States. This relationship turned out to be inversely related to obesity for Asian countries, and had the opposite effect for Arab States. One last effect my model took into account was GDP in European countries. For these countries, the effects of GDP per capita were slightly less so than for other regions. In particular when examining the least obese European countries, scandanavian countries like Finland and Sweden along with Switzerland (countries with more progressive/universal healthcare) were well under their projected obesity rates given their levels of wealth, education, and so on. 

&nbsp;&nbsp;&nbsp;*Figure 3* below shows the co-efficients of the variables included in my final model.

![Figure 3](/images/Vars.png)


&nbsp;&nbsp;&nbsp;From this plot we can clearly see the Oceania categorical variable has a potentially huge impact on projected obesity rates. Education appears to have a huge effect also, but keep in mind these variables are using different scales. Education, for example, is a 0 to 1 variable, hence its large coefficient reflects moreso the fact that education is calculated using a less-than-1 decimal than actually having an enormous effect on obesity projections. In other words, our coefficient is telling us that we can expect a theoretical country with an education index of 1 to be about 17.4% more obese than a theoretical country with an index of 0.


## Model Fit 

&nbsp;&nbsp;&nbsp;*Figure 4* below shows the overall fit of my model represented by the black dashed line with the indentity line overlayed with a gray dashed line. 

![Figure 4](/images/y_yhat.png)

The accuracy of the model was given by a cross-validated R-squared, in our case the model scored .885. This means the model was able to explain about 88.5% of the variance we see in obesity rates between countries. We can see the relative high degree of accuracy by the overlap between the identity line and my model's fitted line; they're nearly identical.  

&nbsp;&nbsp;&nbsp;Of course, my model is still far from perfect and in particular is limited by some of the asssumptions it makes. For example, countries which are wealthy and well educated are predicted to have higher obesity rates all else equal- but this is not universally the case. *Figure 5* below shows the residuals of my model's errors plotted against respective fitted values.


![Figure 5](/images/resid_fitted.png)

&nbsp;&nbsp;&nbsp;A couple of noteworthy outliers demonstrate the weakness I mentioned above with my model. Points 3-Singapore and 23-Japan (my two biggest outliers) are both asian countries with particular features which cause my model to make innacurate predictions. These two countries are well educated and have relatively high GDP per capita, and have a relatively high percent of their populations considered insufficiently active. Given this, my model predicted both countries should have obesity rates around 15%, yet Japan and Singapore's actual obesity rates were 3.3% and 6.2% respectively.  
