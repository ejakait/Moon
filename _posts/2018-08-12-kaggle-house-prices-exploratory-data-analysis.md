---
title: Kaggle House Prices - Part 1
layout: post
date: 2018-08-12 00:00:00 +0000
excerpt: 'This is the first post in series that goes through the House Prices: Advanced
  Regression Techniques Kaggle Dataset with the goal of learning and practicing machine
  learning techniques.'
tags:
- Data Science
- Kaggle
- Regression
- Python
- Jupyter
- EDA
- Feature Engineering
feature: "/uploads/indiana2.png"
comments: 'true'

---
> _Very little is needed to make a happy life; it is all within yourself, in your way of thinking._
>
> **_Marcus Aurelius_**

![](https://kaggle2.blob.core.windows.net/competitions/kaggle/5407/logos/front_page.png)

### Problem and Approach

This is the first post in series that goes through the [House Prices: Advanced Regression Techniques](https://www.kaggle.com/c/house-prices-advanced-regression-techniques) Kaggle [Dataset](https://www.kaggle.com/c/house-prices-advanced-regression-techniques/data) with the goal of learning and practicing machine learning techniques.

#### Wanna Follow

If you prefer less setup, I would suggest you take a look at Microsoft Azure Notebooks. It has most of what we will be using already installed and it runs Jupyter Lab.

### The Process

![](/uploads/embiid.jpg)

**Generally, the approach to a machine learning problem is**:

1. Understanding the data and the problem
2. Exploratory Data Analysis and Data Cleaning
3. Feature Engineering and Feature Selection
4. Model Selection and Comparison
5. Model Optimization
6. Interpretation of results

#### Understanding the data and the problem

Well lets start from the very beginning, by understanding the problem. Ideally, we would be more experienced in real estate to better inform this part of the process, however this is often not the case and we most frequently find ourselves dealing with a new field. That said, taking a high level look at the task, we need to predict the final price of houses located in Ames, Iowa based on their 79 features.

If we take a look at the data set as we will soon do, we can draw a few conclusions. First, because we are looking at a [labeled dataset](https://stackoverflow.com/questions/19170603/what-is-the-difference-between-labeled-and-unlabeled-data), it narrows down our machine learning techniques to Supervised Machine Learning which breaks down to either Regression or Classification. 

The choice of machine learning techniques is reliant on your data and its characteristics as well as the expected outcome. 

Though the exact model is not chosen at this point we can get general idea of the class of supervised machine learning techniques we can use by looking at our target variable, '_SalePrice_' or the final price of a house.

We can take a look at the dataset using Jupyter and Python Pandas. The data is stored in a CSV file so we will use the pandas read_csv function. Pandas can be installed using pip like so,

    pip install pandas

First we import the pandas module as 'pd' so we don't have to type pandas every time we call a function from it.

    import pandas as pd

Next we can import the dataset using the aforementioned function read_csv to create a [data frame](https://github.com/mobileink/data.frame/wiki/What-is-a-Data-Frame%3F) and assign it to a variable. The [data](https://www.kaggle.com/c/house-prices-advanced-regression-techniques/data) provided comes in two files a training set which will be used to help our model learn and a test set that will be used to evaluate how well the chosen model performed.

    df_train = pd.read_csv('train.csv')
    df_test = pd.read_csv('test.csv')

We can now performs some operations on the imported data. 

    # Showing the first five entries of the training dataset
    df_train.head() 

The output,

![](/uploads/khpp-dftrain-head-1.PNG)

We can tell a few things already from this small snapshot. We we have columns with missing values. It is also apparent that our data comes in varying types, both numerical and categorical.

    df_train.info()

the output here is a description of the data:

![](/uploads/khpp-dftrain-info.PNG)

In pandas this is represented as data types, integers and floats which are our numerical features and categorical features with the object type. Even so, the difference isn't always obvious, some numerical features might actually be categorical and vice versa, so it pays get an understanding of the description of every feature.