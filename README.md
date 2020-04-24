# Subreddit Classification Project

## Problem Statement
Reddit is a large platform with millions of submissions and hundreds if not thousands of subreddits. Each subreddit has its own topics and personality. Is it possible to create a classification model that can decipher between two separate subreddits. The subreddits in question is 'CasualConversation' and it's sister subreddit 'SeriousConversation'. Can a machine learning model be created to know the difference between these two similar subreddits.

## Executive Summary
Looking through this notebook you can see all the information you need to find on how I came to my conclusion. The data was created by pulling the information from Pushshift's Reddit API (https://github.com/pushshift/api). The dataset was then created from my initial pull and then I cleaned and parsed the data to fit it into a model.


Below you can see all the resources and the work that was done on the data. It includes:
1. 5 jupyter notebooks
2. The data sources I created and the cleaned csv.
3. The Pushshift API I used
4. The subreddits I referenced
5. A data dictionary
6. The procedure and methodology
7. The conclusion

## Contents:

- [Code] 
- [Data Gathering](01_Data_Gathering.ipynb)
- [Data Cleaning and EDA](02_Data_Cleaning_EDA.ipynb)
- [Further Cleaning](03_Further_Cleaning.ipynb)
- [Modeling](04_Modeling.ipynb)
- [More Data Visualization](05_Visualizations.ipynb)
- [Project 3 Reddit Classification PPT](Project_3_Reddit_Classification.pdf)

## Data sources:
- [Original Reddit Dataset](Datasets/big_reddit_list.csv)
- [Reddit Dataset with Feature Engineered columns](Datasets/reddit_list_with_feature_engineering.csv)
- [Reddit Dataset with added sentiment analysis](Datasets/reddit_cleaned_title_and_selftext.csv)


##  References
- [Pushshift's API](https://github.com/pushshift/api)
- [CasualConversation](https://www.reddit.com/r/CasualConversation/)
- [SeriousConversation](https://www.reddit.com/r/SeriousConversation/)



Feature|    Type|    Dataset|Description|
-------|--------|-----------|-----------|
**author**|object|Reddit Dataset with added sentiment analysis|The username of the author who made reddit submission|
**id**|object|Reddit Dataset with added sentiment analysis|The id of the redditer who posted|
**num_comments**|integer|Reddit Dataset with added sentiment analysis|The number of comments post recieved|
**score**|integer|Reddit Dataset with added sentiment analysis|The score of the reddit post|
**created_utc**|integer|Reddit Dataset with added sentiment analysis|The epoch time of the reddit post|
**title**|object|Reddit Dataset with added sentiment analysis|The title of the reddit post|
**selftext**|object|Reddit Dataset with added sentiment analysis|The body of the post|
**subreddit**|integer|Reddit Dataset with added sentiment analysis|The subreddit the post came from. CasualConversation: 0, SeriousConversation: 1|
**char_count_title**|integer|Reddit Dataset with added sentiment analysis|The character count of the title of the reddit post|
**word_count_title**|integer|Reddit Dataset with added sentiment analysis|The word count of the title of the reddit post|
**char_count_selftext**|integer|Reddit Dataset with added sentiment analysis|The character count of the selftext of the reddit post|
**word_count_selftext**|integer|Reddit Dataset with added sentiment analysis|The word count of the selftext of the reddit post|
**title + selftext**|object|Reddit Dataset with added sentiment analysis|Feature engineered column of the title and selftext columns combined|
**clean_title**|object|Reddit Dataset with added sentiment analysis|The title of the reddit post, but stopwords have been removed|
**clean_selftext**|object|Reddit Dataset with added sentiment analysis|The body of the post, but with stopwords removed|
**clean_title_+_selftext**|object|Reddit Dataset with added sentiment analysis|Feature engineered column of the title and selftext columns combined, but stopwords have been removed|
**neg**|integer|Reddit Dataset with added sentiment analysis|The negative sentiment analysis of the reddit posts|
**neu**|integer|Reddit Dataset with added sentiment analysis|The neutral sentiment analysis of the reddit posts|
**pos**|integer|Reddit Dataset with added sentiment analysis|The positive sentiment analysis of the reddit posts|
**compound**|integer|Reddit Dataset with added sentiment analysis|The positive sentiment analysis of the reddit posts|


## Procedure/Methodology
Starting out with no dataset I had to create my own. Using Pushshift's API I originally pulled 20,000 submissions. Once I had something to start working with I immediately made it into a csv so not to keeping pulling from the API. I used the epoch time as a way to pull submissions that were recently submitted.

After doing some data cleaning I realized pretty quickly that I would need to pull more data. There were tons of empty values, but not only were there many empty values there were tons of submissions that had been removed. Fortunately these subreddits were quite popular and it is very easy to gather more data. So I went back to gather 10,000 more submissions total the number of submissions to 30,000. Once I finished removing the null values and 'removed' submissions I was left with about 22,000 submissions to clean and model.

I continued to clean the data and added some more columns to learn more about the data I was working with. I feature engineered a column of the title and selftext so it was easier to put through a countvectorizer. After that feature engineering I then cleaned all the text columns and removed odd characters and stopwords. I also created columns with the sentiment analysis of the submissions. 

Once I had some data to work with I started to plot it and graph it to see if there were any trends and maybe other things I could learn about the data.

I ran the data through many different models including Logistic Regression and a Naive Bayes model.

After running those models I noticed that I would need to gather more data. I was able to get a model to perform at about 80% on the testing data. I think if I could do this again I would be a little more aggressive with the amount of data I pull and try to work with. I also would be a lot better with the cleaning of the data. There were some minor errors left in the data. For example leaving the title of the subreddit inside the posts. There were also many different models that could have been tried like TFIDF and SVMs. Overall happy with how it turned out.

# Conclusion

In conclusion I was able to create a model that performed at about 80% success rate. The biggest things that differentiated the two subreddits were the kinds of topics. 'SeriousConversation' tended to have more conversations that seemed to be more personal. Topics including sex, religion, and death. Due to what is currently happening in the world 'CasualConversations' were more revolved around the topic of COVID-19. Those topics included quarentine, staying home, and isolation. The model was somewhat successful, but there was definitely room for improvement. 
