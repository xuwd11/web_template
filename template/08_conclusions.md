---
nav_include: 6
title: Conclusions
notebook: 08_conclusions.ipynb
---

## Contents
{:.no_toc}
*  
{: toc}

## Conclusions

In this project, we implemented and benchmarked several widely used models for recommender systems on 6 different size of datasets sampled from [Yelp academic dataset](https://www.yelp.com/dataset/challenge). We tested several baseline models, collaborative filtering models and content filtering models, and explored several strategies of building ensemble models. Our regression based baseline model performed best on test set among baseline and collaborative filtering models we tried. We found the performance of matrix factorization based latent factor models is generally better than that of neighborhood methods, which is presumably due to the sparsity of the dataset. We recommended random forest for the construction of ensemble estimator from predictions of base estimators. Finally, we demonstrated our models perform robustly on different size of datasets.
<br><br>

## Future work

### Address potential drawbacks in content filtering models

Although the test $R^2$ of our content filtering models is very high, we found the most siginificant predictors are average ratings of user and restaurant instead of user or restaurant profiles, which is fishy. We then realized our assumption that average ratings of user and restaurants are always available might be incorrect since a lot of users / restaurants only sent / recieved one rating, which questioned the validity of our content filtering models.

One potential solution to this issue is to obtain average ratings of users or restaurants by learning from data in the training set as what we did in baseline (mean) model rather than using the average ratings in the user and business tables directly. We expected the test $R^2$ to be lower if we process data in this way. To improve the performance of content filtering models, we need to figure out how to acquire more useful features from user or restaurant profiles.
<br><br>

### Improve the efficiency of SVD-ALS models

We noticed the fitting time of 2 SVD-ALS models we implemented was much longer than other algorithms we tested. And we believed it was mainly due to defects in our implementation since we implemented the algorithms in python, which might not be efficient enough. We could try implementing the algorithms in cython and utilizing parallel computing strategies to speed up computation.
<br><br>

### Take temporal dynamics into account

All models we built in this project were static. We could account for temporal effects such as the change of a restaurant's popularity or user preferences. We could also incorporate incremental learning strategies for our models.
<br><br>

### Implement the user interface of recommender systems

We could implement an user interface which recommends restaurants for users based on the predicted ratings.