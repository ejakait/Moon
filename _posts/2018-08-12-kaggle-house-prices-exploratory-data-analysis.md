---
title: Kaggle House Prices - Part 1
layout: post
date: 2018-08-12 00:00:00 +0000
excerpt: ''
tags:
- Data Science
- Kaggle
- Regression
- Python
- Jupyter
- EDA
feature: "/uploads/indiana2.png"
comments: 'true'

---
> _Very little is needed to make a happy life; it is all within yourself, in your way of thinking._
>
> **_Marcus Aurelius_**

![](https://kaggle2.blob.core.windows.net/competitions/kaggle/5407/logos/front_page.png)

In this post we will be getting the lay of the land so to speak while covering Exploratory Data Analysis(EDA) of a Kaggle data set,[ House Prices: Advanced Regression Techniques.](https://www.kaggle.com/c/house-prices-advanced-regression-techniques)

If you want follow along with the exercise, you might need a couple of things,

1. Python3.6
2. Pip
3. Jupyter Notebook

Or,

If you prefer less setup, I would suggest you take a look at Microsoft Azure Notebooks. It has most of what we will be using already installed and it runs Jupyter Lab.

So what is Exploratory Data Analysis anyway and what is its purpose?

The simple answer, exploratory data analysis techniques have been developed to aid in determining important characteristics in the data.

There is a lot more to talk about with EDA such as the types and their importance in gaining a better understanding of our data, but we will discuss them as they arise in the course of tackling tasks in the machine learning workflow.

Well lets start from the very beginning, by understanding the problem. If we take a look at the data set as we will soon do, we can see that it is a [labeled dataset](https://stackoverflow.com/questions/19170603/what-is-the-difference-between-labeled-and-unlabeled-data). This narrows down our machine learning options to Supervised Machine Learning which breaks down to either Regression or Classification. The choice of machine learning techniques is reliant on your data and its characteristics as well as the expected outcome.

We can take a look at the dataset using Jupyter and Python Pandas. The data is stored in a CSV file so we will use the pandas read_csv function. Pandas can be installed using pip like so,

    pip install pandas

First we import the pandas module as 'pd' so we don't have to type pandas every time we call a function from it.

\#import pandas

Next we can import the dataset using the aforementioned function read_csv to create a [data frame](https://github.com/mobileink/data.frame/wiki/What-is-a-Data-Frame%3F) and assign it to a variable. The [data](https://www.kaggle.com/c/house-prices-advanced-regression-techniques/data) provided comes in two files a training set which will be used to help our model learn and a test set that will be used to evaluate how well the chosen model performed. 

    df_train = pd.read_csv('train.csv')
    df_test = pd.read_csv('test.csv')

From the description of the problem,

_'Ask a home buyer to describe their dream house, and they probably won't begin with the height of the basement ceiling or the proximity to an east-west railroad. But this playground competition's dataset proves that much more influences price negotiations than the number of bedrooms or a white-picket fence._

_With 79 explanatory variables describing (almost) every aspect of residential homes in Ames, Iowa, this competition challenges you to predict the final price of each home.'_

we can surmise that our target variable is the final price or SalePrice of a house and that it is a varying numerical figure. This also helps us to figure out what kind of models we can use to solve the problem. Regression is the answer to our problems. If it were a classification problem our target variable would have more discrete outcome for example the iris dataset that involves correctly labeling a flower's species(_Iris setosa_, _Iris virginica_, _Iris versicolor_) based on its characteristics(petal and sepal length/width etc)