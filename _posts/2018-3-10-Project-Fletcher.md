---
layout: post
title: Project Fletcher
---


{% include py_vis.html %}

### Objective & Motivation

The primary objective of my fourth project at Metis was to analyze and categorize trending topics on twitter. 

This is a useful and worthwhile venture because of the growing consumerization of health and healthy products. It is increasingly profittable to market and create items which are wholesome and healthier for consumers. At the same time, there is a proportionate increase in demand for knowledge and quality information. Consumers want to be healthy, and they want to be knowledgeable about what is actually healthy, especially in a time when they are bombarded with products which claim to fallin this category. Consequently, we've begun to see an uptick in health-related content in the form of blogs, podcasts, and articles. 

Traditional fitness industry giants such as chain gymns are even attempting to get in on this trend, hiring dieticians and knowledgeable professionals to produce online content for their members. Discovering emerging trends in health and fitness can give individuals and organizations in this space a great advantage by predicting what types of products and information their consumers will value most. As a personal trainer and health writer, I've personally seen the conversations on social media directly impact my work; people will often ask about trendy new diets or forms of exercise. As someone operating in this space, it's important that I be informed about trending topics in order to guide my clients through making effective and sustainable lifestyle choices.

### Metholds & Tools

For this project I utilized a plethora of tools in an attempt to distinguish trending topics on twitter. In an effort to segment topics I firstly had to transform text data witha variety of approaches, including TFIDF and count vectorization. From there, I was able to use these formatted tweets as inputs into a variety of topic and clustering models. These models included LDA, NMF, Word2Vec, as well as K-means and hierarchical clustering. Among these, LDA and Word2Vec generated the most interpretable and useful results.


### Results 

By visualizing our Word2Vec model in a two-dimentional space using t-SNE, we can better recognize certain patterns in the data. The figure allows us to observe these patterns more intuitively as the proximity of words to one another reflects their similarity within the context of the Word2Vec model, which was trained on the ~100,000 tweets I gathered. Gensim's Word2Vec model has several useful features, among them is the 'similarity' feature which allows us to input a word in the model's dictionary and returns a list of the most similar words, with their respective 'similarity' value from 0-1. 

The more data the model has, generally the better it gets at distinguishing relationships and similarities. Although my model could certainly improve with more tweets/health- related text to train on, it faired surprisingly well at recgonizing patterns and distinguishing similarity among words in health-related topics.


### Conclusions & Future Work


