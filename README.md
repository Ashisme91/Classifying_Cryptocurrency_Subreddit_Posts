# Project 3: Developing a machine learning classifier to identify which         subreddit a submission originated from 


## Background

We work for a cryptocurrency trading platform startup company. In the recent months, the customer service team has received an increasing number of enquries on the the cryptocurrencies available on our platform. On closer look, they found that a large proportion of these enquiries are related to what those cryptocurrencies are and their applications. Faced with increasing workload and resource constraints, the head of customer service has engaged our team to develop a real time chatbot for the company website to automate the process of responding to such simple enquiries. A real time chatbot will not only enable the customer service team to focus on complex enquiries or feedback, it can also help to educate users more timely and accurately on our products and hence enhance their user experience.

## Objectives

In this project, our team will be using data from two subreddits to achieve the following:

1. Understand what type of data are used in the respective posts and use natural language processing (NLP) to analyze the text data in each of the subreddits,

2. Use machine learning (ML) classifiers like Naive Bayes (NB) Multinomial model and Linear Support Vector Machine (SVM) to identify the subreddit a submission is likely to originate from,

3. Evaluate the ML classifiers against our baseline model using accuracy as the key metric. A ML classifier is said to outperform the baseline model if it has a higher accuracy score. The target we are working towards is at least 80% accuracy.

4. Propose a suitable optimal ML classifier that could be used to develop a minimum viable product (MVP) for the chatbot and make other recommendations.

## Executive Summary

On testing, both Naive Bayes (NB) Multinomial model and Linear Support Vector Machine (SVM) coincidentally scored an accuracy of 85.9% and outpeformed the baseline model's accuracy of 65.0%. While both NB Multinomial model and Linear SVM are overfitted (since training accuracy > testing accuracy), the extent of overfitting is lower in NB Multinomial model. This is evident by the smaller gap between training accuracy and testing accuracy in NB Multinomial model. We expect NB Multinomial model would be more stable than Linear SVM when exposed to unseen text data. We believe that the greater stability in NB Multinomial model would outweigh the effects of marignal lower accuracy when compared to Linear SVM. To top it off, NB Multinomial model allows us to study the significance of predictors in our text features but Linear SVM does not. Therefore, we recommend that NB Multinomial model would be suitable than Linear SVM to be used as the classifier in the development of the minimum viable product for the chatbot.


## Key Findings

* Based on the top 10 features to predict a submission originates from r/Bitcoin, 'bitcoin and 'btc' came up at the top of the list. Based on our domain knowledge, the rest of the top features does not seem to have any association or linked to Bitcoin. 

* Based on the top 10 features to predict a submission originates from r/Ethereum, 'ethereum and 'eth' came up at the top of the list. Another word that is specific to Ethereum is 'defi' which stands for decentralized finance. It refers to a collective term for financial products and services that are accessing to anyone who can use Ethereum.

* The length of 'selftext' is less than three times as long as the length of 'title' on average across all submissions, on average. Note that average length of title across all submissions around 7.

* A lot of common words in the titles and posts of the subreddits were found and removed. Given that the length of 'selftext' is less than three times as long as the length of 'title', on average, we believe that forming a new column to combine 'selftext_clean' and 'title_clean' would work better as text features.

* Breakdown of 'post_hint' can explain the absence of 'selftext' in majority (>52.0%) of the submissions. These posts are expressed in the form of a link, image or video. It seemed like humans have a preference to express ideas on Bitcoin and Ethereum through the use of non-text data.

## Conclusion

The MVP chatbot should be piloted to a targeted group of users of our platform to determine if it is effective and productive in classifying and responding to text enquiries accurately. Building a custom model that combines NB model and SVM can deliver a more optimal performance. One potential future development is the expansion in the scope of our algorithm to include more cryptocurrencies by extending the existing binary classifiers to multi-class classifiers. Another potential development is use of sentiment analysis to augment our core text classification. With the productionization of our algorithm, it will be continuously trained through constant interaction with users. Given that a large proportion of our submissions contained non-text data such as links, video and image in their post, it can be useful to apply researach methods such as content analysis to apply and code these non-text documents and their associated texts. 

## Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|title|object|final_dataset.csv|Raw title|
|selftext|object|final_dataset.csv|Raw subreddit post|
|subreddit|object|final_dataset.csv|Name of subreddit|
|is_bitcoin|int|final_dataset.csv|Binary "target" data column indicating 1 for posts in r/Bitcoin and 0 for posts in r/Ethereum|
|title_clean|object|final_dataset.csv|Cleaned title|
|selftext_clean|object|final_dataset.csv|Clean subreddit post|
|title_length|int|final_dataset.csv|Number of items in 'title_clean'|
|selftext_length|int|final_dataset.csv|Number of items in 'selftext_clean'|
|more_text_clean|object|final_dataset.csv|Combination of items in 'title_clean' and 'selftext_clean'|
|final_text_clean|object|final_dataset.csv|more_text_clean with the removal of 'emptypost' item|
