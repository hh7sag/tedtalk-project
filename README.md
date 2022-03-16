# tedtalk-project
Ted Talk videos dataset is a project which I love to dig down since there are lots of videos with different emotions across the website. This project is mainly created using Google Colaboratory writing in Python language

![image](https://user-images.githubusercontent.com/97778235/158612371-8e9dfe14-82f3-40dc-ae7e-750f50a0c35e.png)

## Overview
TED Talk stands for Technology, Entertainment and Design, which provides media platform for speakers with different backgrounds to speak about macro-level topics. For me, it has tremendous sources to improve my English listening skills a lot when I was young. The dataset is sourced from Kaggle website (www.kaggle.com), which has 17 columns and 2550 videos which have 2 datasets for overview data and transcript data. In this project, I only focus on the overview data

![image](https://user-images.githubusercontent.com/97778235/158615693-ddcdb4db-eaf8-4332-8997-145b8e1c620b.png)

## Problem Statement
There are 3 questions needed to be discussed during the project:
1. What factors make a good/bad quality TED Talk? 
-> Figure out criteria for good/bad quality video on Youtube: rating/view columns,views, comments, timestamps
2. What topics appear the most in top good/bad quality videos?
-> Figure out top topics that cover the good/bad quality
3. What emotional rating represents TED videos with positive and negative ratings?
-> Figure out top emotional ratings appearing in top good/ bad quality videos 

## Methodology

### Clean the data for ratings
The column 'ratings' has string data type. However, one special thing about this column is that each row has a dictionary inside the string which has the keys as emotions and values as the count of viewers for each emotion. In this case, I use read_json to extract this column to seperate columns with each emotion as column name and the count as values in that column. 

![image](https://user-images.githubusercontent.com/97778235/158616770-2ff1c84a-2f3c-4f86-b16e-023799361144.png)

After cleaning the ratings, create a new dataset name 'ted' with specific columns like 'comments','duration','film_date','languages','main_speaker','name', 'published_date','ratings', 'speaker_occupation','tags',	'title', 'views', 'Year_Month_filming', 'Year_Month_publishing','Year','transcript', 'Funny',	'Beautiful','Ingenious',	'Courageous',	'Longwinded','Confusing','Informative','Fascinating','Unconvincing','Persuasive','Jaw-dropping','OK',	'Obnoxious','Inspiring'

There are 14 emotions overall that can be divided into positive and negative: 
Positive videos: 'Beautiful','Inspiring','Funny','Fascinating','Ingenious','Jaw-dropping','Courageous','Persuasive','Informative','OK'
Negative videos: 'Longwinded','Unconvincing','Confusing','Obnoxious'

It is done for cleaning data part. Then, moving on to explorative data analysis part

### Explorative data analysis
Question 1: What factors make a good/bad quality TED Talk?
+ To answer that question, I need to create 3 new columns of positive, negative and ok based on the count number of ratings along with 2 news column called ratio_good/view and ratio_bad/view describing the ratio between ratings and views and 1 column of comment to View Rate
+ Use quantitle to divide the group of positive/negative videos will be used for 2 remaining questions. This is based on like to view rate in this picture below: 
++ Good videos are defined with positive/view from 60th-90th quantile
++ Bad videos are defined with negative/view from 10th-30th quantile

![image](https://user-images.githubusercontent.com/97778235/158620467-f851036b-1fed-4c41-b3fc-cf6fe790f930.png)




## Result
## Data Visualization
