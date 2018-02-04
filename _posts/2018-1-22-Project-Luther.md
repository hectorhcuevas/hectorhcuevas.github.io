---
layout: post
title: Project Luther 
---
# Weeks 2 and 3 
Our second and third weeks at Metis were focused on learning the fundamentals of predictive modeling using linear regression. Additionally, data gathering was expanded to web-scraping using Beautiful Soup 4 and Selium. Model selection and generalization methods were also incorporated as essential parts of this project.


# Objective

The objective of my project was predicting rates of obesity in a country based off certain characteristics (mostly socio-economic). Obesity is defined as a BMI (Weight(KG)/Height(m^2) greater than 30. Obesity is an arbitrary yet meaningful measure of someone's body composition. It is neither a trivial nor simply aesthetic problem; being obese has been strongly linked to a multitude of diseases and other health problems. Consequently countries with a large obesity rate must carry the immense costs; primarily in health care, but also in everyday activities like productivity, transportation, waste, etc. In the U.S. alone, obesity- related healthcare expenses account for 21% of total annual healthcare expenses, [about $190 billion and an additional $4.3 billion for obesity-related absenteeism at work](http://www.healthycommunitieshealthyfuture.org/learn-the-facts/economic-costs-of-obesity/).While many developed countries (ie USA) are already >35% obese and suffering growing consequences as a result, many developing countries are seeing an exponential growth in obese population. Some even have the dual-problem of feeding starving populations while trying to deal with rising obesity rates. Regardless, many are surprised to learn that today more people die from an over- abundance of food, rather than a shortage. If there is no intervention, this trend will only increase as more countries join the developed world. With [1 in 2 adults globally are projected to be obese by 2050](http://www.telegraph.co.uk/news/uknews/1566436/Half-of-adults-will-be-obese-by-2050.html), and trillions of dollars at stake, it's clearly crucial from a policy perspective to better understand this epidemic.


# Data

Obesity rates, our target variable, were scraped from the web using BeautifulSoup 4. The data was extracted from a table from [Renew Bariatics](https://renewbariatrics.com/obesity-rank-by-countries/).
From there, data were cleaned and stripped of commas, percentage signs, etc. in order to process and run analysis in our pandas dataframe. The end result was a dataframe of 154 countries by name and their respective obesity rates. The remainder of our variables were dependednt and came from a variety of government and NGO sourcers (IMF,CIA,UN, and WHO) and were merged with the initial obesity data by country name.

The remaining dependent variables in my model were:
  * Education (Index)
  * Activity- % of Population Insufficiently Active
  * Region of World (Oceania,Arab States, Europe)
  * log of GDP Per Capita
  * log of Imports
  * Globalization (Index)

Not all regions of the world were found to be particularly useful or statistically significant in my model, hence only Oceania, Arab States, and Europe were taken into account as categorical variables. GDP per capita and imports were both changed via log transformation in order to obtain a more normal distribution of these characteristice, as both can vary by orders of magnitute between countries. Globalization is an index which takes into account social, political, and economic integration between that country and the international community. While these were the variables included in my final model which I'll discuss shortly, I began my investigation with some exploratory data analysis on some of my more noteworthy variables.

## A Global Snapshot

Figure 1 below gives us a general idea of where obesity is most prevalent. For the purposes of this analysis, we will refer to Arab States, which is inclusive of Middle East and North African states. In regards to the Oceania region which is also included in the analysis, we mean the small pacific islands excluding New Zealand and Australia 

![Fig 1](/images/Global_Map.png)

# Methods 

The approach for this investigation began by looking at broad measures of a country's wealth and well-being. As previously mentioned, obesity tends to be a bigger problem in wealthy countries like the US and westen Europe. When comparing relative 
wealth between countries, GDP per capita is a standard measurement, so I decided to use it as a preliminary variable to see
if wealthier countries tended to have higher obesity rates.

GDP per capita and obesity rates are indeed correlated, but I found this to be a rather crude method of describing 'wealth' between countries, so I turned to other well-known indices to capture more of the varience among countries' obesity rates. The first which came to mind was the Human Development Index (HDI). HDI is in many ways a better way of measuring development than GDP per capita, because it takes into account not only wealth (in the form of GNP per capita) but also includes indices for health and education. This means countries that are relatively wealthy for their population size, but not actually developed in terms of having a broad network of institutions to assist, employ, and educate populations (i.e resource-rich countries) have a low HDI relative to GDP per Capita. The only issue with HDI is that it also took health and life expectancy into account, which we can assume are being impacted by obesity rates.  Being that my model was attempting to predict high obesity rates, I found that simply taking the education index from HDI turned out to be a more effective variable to include. The figure below demonstrates how well the dependent variables I've discussed predict obesity on their own.

![figure 2](/images/Subplots.png)

Education turned out to be one of the most impactful coefficients in my model. The slope of my curve was almost entirely predicated on it.At first it appeared I had found the perfect indicator for taking into account wealth and development of a nation, but as I added additional variables, the overall relationship became more nuanced. One reason proposed by previous studies as to the correlation between wealthy, developed countries and higher obesity rates is an increased importation and consumption of processed foods. Furthermore, imports might further contribute to obesity by bringing modern gadgets (TVs, computers, etc) that might lead populations to be more sedentary. 
