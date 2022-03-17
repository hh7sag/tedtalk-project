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
+ The column 'ratings' has string data type. However, one special thing about this column is that each row has a dictionary inside the string which has the keys as emotions and values as the count of viewers for each emotion. In this case, I use read_json to extract this column to seperate columns with each emotion as column name and the count as values in that column. 

![image](https://user-images.githubusercontent.com/97778235/158616770-2ff1c84a-2f3c-4f86-b16e-023799361144.png)

+ After cleaning the ratings, create a new dataset name 'ted' with specific columns like 'comments','duration','film_date','languages','main_speaker','name', 'published_date','ratings', 'speaker_occupation','tags',	'title', 'views', 'Year_Month_filming', 'Year_Month_publishing','Year','transcript', 'Funny',	'Beautiful','Ingenious',	'Courageous',	'Longwinded','Confusing','Informative','Fascinating','Unconvincing','Persuasive','Jaw-dropping','OK',	'Obnoxious','Inspiring'

+ There are 14 emotions overall that can be divided into positive and negative: 
Positive videos: 'Beautiful','Inspiring','Funny','Fascinating','Ingenious','Jaw-dropping','Courageous','Persuasive','Informative','OK'
Negative videos: 'Longwinded','Unconvincing','Confusing','Obnoxious'

It is done for cleaning data part. Then, moving on to explorative data analysis part

### Explorative data analysis
Question 1: What factors make a good/bad quality TED Talk?
+ To answer that question, I need to create 3 new columns of positive, negative and ok based on the count number of ratings along with 2 news column called ratio_good/view and ratio_bad/view describing the ratio between ratings and views and 1 column of comment to View Rate
+ Use quantitle to divide the group of positive/negative videos will be used for 2 remaining questions. This is based on like to view rate in this picture below:

Good videos are defined with positive/view from 60th-90th quantile

Bad videos are defined with negative/view from 10th-30th quantile

![image](https://user-images.githubusercontent.com/97778235/158620467-f851036b-1fed-4c41-b3fc-cf6fe790f930.png)

+ Then, create a correlation matrix to see what factors affecting positive/negative views, which I define:

+ Weak correlation: 0-0.3
+ Moderate correlation:0.3-0.7
+ Strong correlation: 0.7-1

![image](https://user-images.githubusercontent.com/97778235/158621794-ac94d7ac-3c59-43cc-9cfd-1b93bafe8eb3.png)

Question 2: What topics appear the most in top good/bad quality videos?

I clean the text data for good along with bad videos and create a dictionary to count each words from 'tag' column. Tag column has string data type combining sevaral sub-topics inside. After cleaning, sort the data to see which topics appear the most in tag columns. From the top topic, I analyze the trend, speaker occupation and top sub-topics associated with top-topic for good videos only.

![image](https://user-images.githubusercontent.com/97778235/158626499-ebf34eb9-e878-451b-bddb-02a3f29490c0.png)


Question 3: What emotional rating represents TED videos with positive and negative ratings?

For this question, I create a pivot_table to check the emotions to see any trend through time (by yearly and monthly) along with speaker's occupation for both positive and negative videos.  

![image](https://user-images.githubusercontent.com/97778235/158626627-262e8a93-06a1-4f51-ac4a-ae971ef90253.png)
Pie chart of positive videos

![image](https://user-images.githubusercontent.com/97778235/158626771-0121b158-c471-43dc-a620-02fa0c6e94c2.png)
Pie chart of negative videos
 
## Results
After analyzing, here are some insights that I found for the 3 big questions above:

1. **What factors make a good/bad quality TED Talk?**
+ From correlation chart, we can conclude that positive/view and negative/view has a slight positive correlation with the number of positive and negative. Moreover, views have a strong positive correlation with positive videos while negative correlation with negative videos 
=> Videos get more views, the more postive ratings and less negative ratings in the videos
+ Also, comments have a positive correlation with positive ratings and negative correlation with negative ratings => Videos get more comments, the more postive ratings and less negative ratings in the videos. However, the duration timestamp shows no correlation with the positive/negative ratings

2. **What topics appear the most in top good/bad quality videos?**
+ Top 15 topics including technology, science, global, issues, culture, design, health, business, tedx, entertainment, change, art, social, in which technology takes the lead in all topics
+ Technology peak for 3 years from 2008-2011
+ Good-quality videos have speakers whose occupations are: Inventor, Entrepreneur, Artist
+ Top sub-topics associated with technology are design along with science

3. **What emotional rating represents TED videos in positive and negative ways?**
+ Top emotion ruling positive videos is inspiring, meanwhile top emotion ruling negative video is unconvincing
+ Both positive and negative videos whose speaker's occupation are writer, designer
+ Inspiring: 2010-2012 (March) as peak time
+ Unconvincing: 2010 (July) as peak time
+ These emotions tend to get lower from 2015 onwards...

## Data Visualization
For more information, please find my Google Colab and Google Data Studio as following links:
+ Google Colab: https://colab.research.google.com/drive/19_MCNK0tMyA3XmlUkITw8gDMSwjhHrYN#scrollTo=mBZzhAQ17GiR
+ GDS Dashboards: https://datastudio.google.com/u/0/reporting/4333faa2-8bed-4740-be71-bef16a2c2753/page/p_3nu0n867qc

