---
layout: post
title: Classifying Diabetics
---

# Project-McNulty
Project McNulty was the culmination of weeks 4-6 at Metis. During this time we refined our machine learning modeling skills and added several classification algorithms to our arsenal. For this project in particular, I utilized logistic, gradient boost, random forest. and several other types of classification models. Tree based models performed best for this project, I will explain why this might be as well as discuss the basic functioning throughout this post. 

# Objective 
The objective of this project is primarily to classify individuals into two categories: those who are diabetic or pre-diabetic, and those who are non-diabetic. Tens of millions of Americans are diabetic or pre-diabetic, but worse still is the fact that most are not even aware of their condition. More broadly the objective of this analysis is to explore the possibilities of preventative care and empower individuals to objectively examine and take control of their health. 

## Data 
The data was gathered from the 2012-2013 NHANES survey conducted by the CDC, which asks many health and lifestyle related questions in addition to tracking diatery consumption over two days. For my final sample, I focused my analysis on roughly 9,000 individuals and their respective responses for questions related to levels of phyisical activity, demographics, and consumption habits to see if we could correctly classify diabetics based on these environmental features alone.
![Fig 1](/images/Project3_Diabetes/Dtree.png)
![Fig 2](/images/Project3_Diabetes/Features.png)
![Fig 3](/images/Project3_Diabetes/GB_cm.png)
![Fig 4](/images/Project3_Diabetes/RocCurve.png)


