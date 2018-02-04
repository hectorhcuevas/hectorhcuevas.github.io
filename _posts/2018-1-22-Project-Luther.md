---
layout: post
title: Project Luther 
---
# Weeks 2 and 3 
Our second and third weeks at Metis were focused on learning the fundamentals of predictive modeling using linear regression. Additionally, data gathering was expanded to web-scraping using Beautiful Soup 4 and Selium. Model selection and generalization methods were also incorporated as essential parts of this project.

# Objective

The objective of my project was predicting rates of obesity in a country based off certain characteristics (mostly socio-economic). Obesity is defined as a BMI (Weight(KG)/Height(m^2) greater than 30. Obesity is an arbitrary yet meaningful measure of someone's body composition. In this analysis, obesity rates are a measure of the percentage of a population in a country who is at or over the 30 BMI threshhold. It is not simply an aesthetic or trivial proble; being obese has been strongly linked
to a multitude of diseases and other health problems. Consequently countries with a large obesity rate must carry the immense
costs; primarily in health care, but also in everyday activities like productivity, transportation, waste, etc. While many
developed countries (ie USA) are already <35% obese and suffering growing consequences as a result, many developing countries
are seeing an exponential growth in obese population. Some even have the dual-problem of feeding starving populations while
trying to deal with rising obesity rates. Regardless, many are surprised to learn that today more people die from an over-
abundance of food, rather than a shortage. If there is no intervention, this trend will only increase as more countries join 
the developed world. With 1 in 2 adults globally are projected to be obese by 2050, and trillions of dollars at stake, it's clearly crucial from a policy perspective to better understand this epidemic.

# Methods

Our target variable, obesity rates, were scraped from the web using BeautifulSoup. The data was extracted from a table from [Renew Bariatics](https://renewbariatrics.com/obesity-rank-by-countries/).
From there, data were cleaned and stripped of commas, percentage signs, etc. in order to process and run analysis in our pandas dataframe.
The approach for this investigation began by looking at broad measures of a country's wealth and well-being. As previously mentioned, obesity tends to be a bigger problem in wealthy countries like the US and westen Europe. When comparing relative 
wealth between countries, GDP per capita is a standard measurement, so I decided to use it as a preliminary variable to see
if wealthier countries tended to have higher obesity rates.

GDP per capita and obesity rates are indeed correlated, but I found this to be a rather crude method of describing 'wealth' between countries, so I turned to other well-known indices to capture more of the varience among countries' obesity rates. The first which came to mind was the Human Development Index (HDI). HDI is in many ways a better way of measuring development than GDP per capita, because it takes into account not only wealth (in the form of GNP per capita) but also includes indices for health and education. This means countries that are relatively wealthy for their population size, but not actually developed in terms of having a broad network of institutions to assist, employ, and educate populations (i.e resource-rich countries) have a low HDI relative to GDP per Capita. 

Education turned out to be one of the most impactful coefficients in my model. The slope of my curve was almost entirely predicated on it.At first it appeared I had found the perfect indicator for taking into account wealth and development of a nation, but as I added additional variables, the overall relationship became more nuanced. One reason proposed by previous studies as to the correlation between wealthy, developed countries and higher obesity rates is an increased importation and consumption of processed foods. Furthermore, imports might further contribute to obesity by bringing modern gadgets (TVs, computers, etc) that might lead populations to be more sedentary. 
