---
layout: post
title: Classifying Diabetics
---

# Project-McNulty
&nbsp;&nbsp;&nbsp;&nbsp;Project McNulty was the culmination of weeks 4-6 at Metis. During this time we refined our machine learning modeling skills and added several classification algorithms to our arsenal. For this project in particular, I utilized logistic, gradient boost, random forest, and several other types of classification models. Tree based models performed best for this project, I will explain why this might be as well as discuss their basic prcoess throughout this post. 

## Objective 
&nbsp;&nbsp;&nbsp;&nbsp;The objective of this project was primarily to classify individuals into two categories: those who are diabetic or pre-diabetic, and those who are non-diabetic. Tens of millions of Americans are diabetic or pre-diabetic, but worse still is the fact that most are not even aware of their condition. More broadly the objective of this analysis is to explore the possibilities of preventative care and empower individuals to objectively examine and take control of their health. 

## Data 
&nbsp;&nbsp;&nbsp;&nbsp;The data was gathered from the 2012-2013 NHANES survey conducted by the CDC, which asks many health and lifestyle related questions in addition to tracking diatery consumption over two days. For my final sample, I focused my analysis on roughly 9,000 individuals and their respective responses for questions related to levels of phyisical activity, demographics, and consumption habits to see if we could correctly classify diabetics based on these environmental features alone.

## Overview

&nbsp;&nbsp;&nbsp;&nbsp;I took advantage of several different tools for this project in addition to the basic python libraries utilized in my previous projects, relying primarily on:
 
 * PSQL for data storeage  and handling
 * Flask for hosting a web-based app for the project
 * D3 for visualizations hosted by my flask web app
 * scikit-learn: classification models
 
 &nbsp;&nbsp;&nbsp;&nbsp;Among the models I tried, the following performed best in terms of having the highest AUC scores: 
 
 
 | Model        | AUC           | 
| ------------- |:-------------:| 
| Gradient Boost Classifier | 0.8758 |
| Logit Classifier | centered | 0.8749 |
| Random Forest Classifier | 0.8665 |
| SVC Classifier | 0.8161 | 0.7993 |
| Naive-Bayes Classifier | 0.7461 |

&nbsp;&nbsp;&nbsp;&nbsp;I will utilized the logit classifier for further interprability of my results, but as is evident from the area under the curve (AUC) score, the gradient boost classifier performed best in terms of correctly classifying diabetic individuals. AUC is a standard metric used to evaluate classification models. It essentially gives an approximation to the proportion of test data which is correctly classified by the model. It's derived directly from the receiver operating characteristic curve; which, in turn is the graphical plot that illustrates the diagnostic ability of a binary classifier system as its discrimination threshold is varied. The curves as plotted in the figure below.
 
![Fig 1](/images/Project3_Diabetes/RocCurve.png)

&nbsp;&nbsp;&nbsp;&nbsp;The diagonal line can be thought of as a curve for a model based on randomly guessing whether or not an individual is diabetic. Its AUC is .5, so we can expect this kind of model to be %50 accurate. As one might expect, my models performed well above that level of accuracy. Gradient boost having performed best, I will focus the rest of my analysis primarily on this model and describing how decision tree ensembles work. Below is the basic structure of a single decision tree in my gradient boost model, with a much lower depth than was actually used in order to simplify for this visualization.

![Fig 2](/images/Project3_Diabetes/Dtree.png)

### Overview of Decision Tree Ensembles
&nbsp;&nbsp;&nbsp;&nbsp;Decision trees operate by asking a series of yes/no questions. If the type of question it is asking is continuous (i.e, BMI) then it will establish a cutoff point at which to segment the sample population. In the figure above, for example, the first question asks whether or not an individual has a BMI above 25.7. It's perhaps no coincidence that those aligns closely with the BMI threshold for being overweight (25). This is because the tree is optimizing questions which provide the best information for segmenting and correctly classifying individuals. It will ask the most pertinent questions first; in this example asking about BMI, then caloric intake, age, various metrics for levels of physical activity, etc. Of course this is only one of tens (or in some cases hundreds) of trees working as an ensemble to arrive at a final decision, but each tree will tend to ask similar questions with order being shuffled around a bit at various levels. The classifier even has a built-in metric which tells us which features are used most for segmentation. Below is a plot of my top features, with their score corresponding to how frequently a question related to that feature was used by the decision tree.
![Fig 3](/images/Project3_Diabetes/Features.png)
### Further Analysis of Results
&nbsp;&nbsp;&nbsp;&nbsp;Finally, let's take a look at how the model actually classified individuals in terms of diabetic/non-diabetic. A summary is given by the confusion matrix below. 

![Fig 4](/images/Project3_Diabetes/GBCM.png)

&nbsp;&nbsp;&nbsp;&nbsp;Note that not only did the model have high accuracy and have high rates of true positives and true negatives (TP/TN, the diagonal darker-red squares), it also did a particularly good job at minimizing false negatives (FN). This is important specifically for this type of classification because it is especially important that we not classify someone as non-diabetic when they in fact are. 

## Conclusions

&nbsp;&nbsp;&nbsp;&nbsp;From this analysis and the results of my project I came to several conclusions regarding the correct classification of diabetic pr pre-diabetic individuals. There was certainly correlation with dollars spent eating out, as well as with BMI, carb (particularly sugar) and fat intake. Demographic issues certainly played a role (particularly age), but these it seems mostly worked to compound the effects of poor health and consumption habits. It should be no surprise that the macronutrient balance in the average diet within my sample was disproportionately heavy on carbohydrates and fats, with minimal protein. It seems this imbalance might also be related to eating out, as these foods tend to be more processed and disproportionately consist of fatty, starchy, or sugary food and drink.

