---
layout: post
title: How Does Youtube Recommendations Work
date: Nov 10 2020
author: Elizabeth Zhao
tags: [Machine Learning, Recommender Systems]
comments: true
toc: true
---

# Introduction

I have to confess that I spend a lot of time on Youtube. Browsing through Youtube homepage, we can often observe that many of the Youtube videos match our interests/needs. If I click on a video and watch for a longtime, Youtube will think that I enjoy it and keep recommend similar videos. If I searched something on the Internet (not just on Youtube), I would see the relevent videos pop up shortly. Some of the videos may not even match to our current interests, but they are the good ones that Youtube thinks what we like. For instance, the video of "**[Plastic Love](https://www.youtube.com/watch?v=3bNITQR4Uso)** (プラスティック・ラブ)" by [Mariya Takeuchi](https://en.wikipedia.org/wiki/Mariya_Takeuchi) was taking over everyone's Youtube page in 2018. Almost immediately, the song brought a popular hit to the [City Pop](https://en.wikipedia.org/wiki/City_pop) music category. My curiosity of the mysterious algorithm behind Youtube was stemed since then. There is a formal name of the "algroithm", which is called *Recommender Systems*. 

---

<!--**What is *Recommender Systems*?** -->

<!--Recommender System is ...-->

---

# How does Youtube Recommender Systems work? 

The architecture of Youtube recommendtaions was presented in the work by *Covington et al* [1]. According to Convington, there are three major challenges of Youtube recommendtiaons: 

- scale: Youtube has massive user base and contents, but the older recommendations fail to work on such scale
- freshness: Many videos are uploaded per second on Youtube. To keep users updated by the latest videos, they want to balance the new content with "well-established videos".
- noise: Past user behaviors are hard to predict because of sparsity. Thus, Youtube modeled "noisy implicit feedback signals"(*) to deal with the noise issue. 

Instead of using the traditional matrix factorization, Youtube recommendations used deep neural networks.

**Covington did not explain the model in the paper, but I'll make a note to look it up later.*

# System Overview

<img width="436" alt="YTsystem" src="https://user-images.githubusercontent.com/56653390/98744789-52fc8900-2380-11eb-923f-71beb169538d.png">

The overall idea of Youtube recommnedation works like this: Youtube takes <u>millions of video courpus</u> as an <u>input</u>, then candidate generation retreives the videos into hundreds that will feed to ranking.  Eventually, only dozens of videos are recommended to users' phones.



I made an illustration below to help me visualize the overall structure. 

![YTsystem2](https://user-images.githubusercontent.com/56653390/98751379-01f39180-238e-11eb-9314-98857fd75f45.png)

---

> **Precision and Recall**
>
> *Precion* (or *positive predictive value*) is the fraction of relevant instances among the retrieved instances.
> $$
> \textrm{Precion} = \frac{\textrm{true positive}}{\textrm{true positive} + \textrm{false positive} }
> $$
> 
>
> *Recall* (or *sensitivity*) is the fraction of the total amount of relevence that were retrieved
> $$
> \textrm{Recall} = \frac{\textrm{true positive}}{\textrm{true positive} + \textrm{false negative} }
> $$
> <img width = "901" alt = "Precisionrecall" src = "https://user-images.githubusercontent.com/56653390/98752180-a7f3cb80-238f-11eb-86b0-8101236bf809.png" style = "zoom:40%">
>
> 

---

## Deep Candidate Generation Model Architecture



```
<div class=figure>
  <p><img width="801" alt="YTcandid" src="https://user-images.githubusercontent.com/56653390/98745009-b71f4d00-2380-11eb-9198-b38f3686bc74.png" style = "zoom:80%">
  <p>Deep candidate generation model Architecture (*Covington et al* [1])
</div>
```

## Deep Ranking Network Architecture

<img width="787" alt="YTrank" src="https://user-images.githubusercontent.com/56653390/98744863-74f60b80-2380-11eb-96c4-cb93a5c7cdf7.png" style="zoom:80%;" >



# Typical Problems and Solutions

- watch time

  prediction: weightet logistic regression

  

- cold start: they take the users information from other websites too

  

---

# Reference

[1] Covington, P., Adams, J., and Sargin, E. "Deep Neural Networks for YouTube Recommendations". In *Proceedings of the 10th ACM Conference on Recommender Systems* (*RecSys '16*). Association for Computing Machinery, New York, NY, USA, 191–198. DOI:https://doi.org/10.1145/2959100.2959190



[2] Marchal, C. "[How Youtube’s Algorithm Turned an Obscure 1980s Japanese Song Into an Enormously Popular Hit: Discover Mariya Takeuchi’s “Plastic Love”](https://www.openculture.com/2018/10/youtubes-algorithm-turned-obscure-1980s-japanese-song-enormously-popular-hit-discover-mariya-takeuchis-plastic-love.html). *Music*. 2018.



[3] ST. Michel, P. ["Mariya Takeuchi: The pop genius behind 2018's surprise online smash hit from Japan"](https://www.japantimes.co.jp/culture/2018/11/17/music/mariya-takeuchi-pop-genius-behind-2018s-surprise-online-smash-hit-japan/). *The Japan Times*. 2018. 



