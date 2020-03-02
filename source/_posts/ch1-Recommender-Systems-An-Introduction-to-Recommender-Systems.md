title: ' Recommender Systems-ch1 An Introduction to Recommender Systems'
author: nullfan
tags: []
categories: []
date: 2020-03-01 11:14:00
---

# 推荐系统的主要目标：
* Relevance:相关性，推荐和用户相关的
* Novely:和用户历史行为无关，但却是用户兴趣的item
* Serendipity:这个主要用来探索用户可能存在的兴趣的item
* Increasing recommendation diversity:对于top-k的item，如果都是某个类，那么user很可能对这些类都不感兴趣； 但如果这top-k的item来自不同的类，那么用户很有可能对其中某个item感兴趣  

# basic models of recommender systems  
``` 
Collaborative Filtering Models
```
* simple to implememt and easy to explain  

```
Content-Based Recommender Systems
```
* have some advantage for new items when sufficient rating data not available for that item  
* provide obvious recommendations, reduce the diversity of the recommended items  
* not effective at providing recommendations for new users 
*  适用场景：the season and the location of the user; a particular type of festival or holiday  
```
Knowledge-Based Recommender Systems
```
* particularly userful in the context of items that are not purchased very often(luxury goods etc.)  
* inherit some of same disadvantage of content-based systems
