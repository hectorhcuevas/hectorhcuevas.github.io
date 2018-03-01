---
layout: post
title: Classifying Diabetics
---

# Project-McNulty
Project McNulty was the culmination of weeks 4-6 at Metis. During this time we refined our machine learning modeling skills and added several classification algorithms to our arsenal. For this project in particular, I utilized logistic, gradient boost, random forest, and several other types of classification models. Tree based models performed best for this project, I will explain why this might be as well as discuss their basic prcoess throughout this post. 

# Objective 
The objective of this project was primarily to classify individuals into two categories: those who are diabetic or pre-diabetic, and those who are non-diabetic. Tens of millions of Americans are diabetic or pre-diabetic, but worse still is the fact that most are not even aware of their condition. More broadly the objective of this analysis is to explore the possibilities of preventative care and empower individuals to objectively examine and take control of their health. 

## Data 
The data was gathered from the 2012-2013 NHANES survey conducted by the CDC, which asks many health and lifestyle related questions in addition to tracking diatery consumption over two days. For my final sample, I focused my analysis on roughly 9,000 individuals and their respective responses for questions related to levels of phyisical activity, demographics, and consumption habits to see if we could correctly classify diabetics based on these environmental features alone.

## Overview

 I took advantage of several different tools for this project in addition to the basic python libraries utilized in my previous projects, relying primarily on:
 
 * PSQL for data storeage  and handling
 * Flask for hosting a web-based app for the project
 * D3 for visualizations hosted by my flask web app
 * scikit-learn: classification models
 
 Among the models I tried, the following performed best in terms of having the highest AUC scores: 
 
 1. Gradient Boost Classifier
 2. Logit Classifier
 3. Random Forest Classifier
 | Model        | AUC           | 
| ------------- |:-------------:| 
| Gradient Boost Classifier | 0.8758 |
| Logit Classifier | centered | 0.8749 |
| Random Forest Classifier | 0.8665 |
| SVC Classifier | 0.8161 | 0.7993 |
| Naive-Bayes Classifier | 0.7461 |

 I will utilized the logit classifier for further interprability of my results, but as is evident from the area under the curve (AUC) score, the gradient boost classifier performed best in terms of correctly classifying diabetic individuals. AUC is a standard metric used to evaluate classification models. It essentially gives an approximation to the proportion of test data which is correctly classified by the model. It's derived directly from the receiver operating characteristic curve; which, in turn is the graphical plot that illustrates the diagnostic ability of a binary classifier system as its discrimination threshold is varied. The curves as plotted in the figure below.
![Fig 1](/images/Project3_Diabetes/RocCurve.png)

![Fig 2](/images/Project3_Diabetes/Dtree.png)
![Fig 3](/images/Project3_Diabetes/Features.png)
![Fig 4](/images/Project3_Diabetes/GB_cm.png)


