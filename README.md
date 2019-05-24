#  Identifying Users Dealing with Mental Health Issues

---

### Problem Statement

According to the National Alliance on Mental Illness, one in five adults in the U.S. experiences some form of mental illness each year. Of those affected by a mental health condition, research suggests that half develop the condition by age 14 and three quarters by age 24. A 2018 study on mental health in college students revealed that the number of students seeking help for mental health problems like depression, anxiety, and panic attacks has risen considerably between 2009 and 2015. This health issue in young adults is only complicated by the prevaling technology of the social media age. A 2018 study in the Journal of Social and Clinical Psychology is one of the first to show a causal link between the use of social media and negative effects on well-being, primarily depression and loneliness. With more young adults spending significant time on sites like Facebook, Reddit, and Google, we must take care to ensure that the mental well-being of users is being taken into account.

The goal of this analysis is to use natural language processing techniques and text classification methods to identify users on social sites that may be dealing with mental health issues, or even contemplating harming themselves. We collected reddit submissions from two support subreddits: r/depression and r/SuicideWatch. Both of these subreddits are intended to provide community to individuals coping with mental health issues. The primary questions of interest are the following:
- Can we identify the language/ language themes that are common for people dealing with depression?
- Can we indentify the language/ language themes that are common for people that are contemplating self harm?
- Can we accurately distinguish between individuals struggling with depression vs those that intend to harm themselves?

These findings could be leveraged by social media sites or large publishers to identify at-risk users based on their public posts/comments. Once identified, proactive measures such as providing them targeted ads to resources, testing new content types to positively engage with them, or even reaching out to them directly with chat bots are potential responses for supporting these users.

---

### Executive Summary

Using Natural Language Processing techniques and a Logistic Regression model, we were able to accurately classify 73% of reddit submissions based on the text data (training accuracy was 77%). The words that were most predictive of a submission being from the depression subreddit included 'start', 'bed', 'motivation', and 'work'. The words that were most predictive of a submission being from the SuicideWatch subreddit included 'attempt', 'pill', 'family', and 'life'.

---

### Data Overview
The subreddit post we're obtained via the reddit PushShift API. 10,000 submissions were collected from each subredditover a two week period in March of 2019.

[Pushshift documentation](https://www.reddit.com/r/pushshift/)

---

### Key Findings

- After preprocessing the text using TF-IDF Vectorizer and a dimensionality reduction technique known as Singular Value Decomposition, the simple logistic regression model produced the highest accuracy score on the data. When explicit, self-identifying terms like 'depression' and 'suicide' were removed from the model, the test accuracy fell just slightly from 72% to 68%

- The model with the second best performance was a Random Forest model which had a 72% accuracy on th test data (83% accuracy on the training data). RandomizedSearch was used to obtain the ideal hyperparameters. While the model performance was on par with that of the Logistic Regression model, the computational time was significantly higher.

- The Naive Bayes Classifier had the worst accuracy on the data (80% test accuracy, 59% train accuracy). Additionally, unlike the Logistic Regression and Random Forest models, the Naive Bayes Classifier was signifcantly more accurate on classifiying submissions from the suicidewatch subreddit compared to the depression subreddit.

- Though analysis of language themes or 'topics' using Latent Semantic Analysis and matrix decomposition methods was attempted on the data, the resulting topics were not easily distinguishable from one another.

---

### Summary & Recommendations


Based on the analysis we see that even when controlling for explicit or self-indentifying language subreddits were able to be identify the respective reddit posts with reasonable accuracy. We recommend trying to improve the accuracy by testing additional modeling techniques such as XGBoost and Support Vector Machines. We recommend providing the production model to social sites like Facebook and Twitter so that they can test the effectiveness on their respective platforms. One use case could be to do an A/B test where some users that are classified in either of these groups would receive an ad for support resources and the control group would not. Ad effectiveness could be measured through the CTR. Additionally, we recommend leveraging the model feature coefficients (logistic regression) to conduct rule-based ad targeting where a user could potentially receive outreach/support for using a certain number of flagged terms.


---

#### Sources

https://www.healthline.com/health-news/social-media-use-increases-depression-and-lonelinesstables/average-published-undergraduate-charges-sector-2018-19)
https://www.usnews.com/news/best-countries/articles/2016-09-14/the-10-most-depressed-countries
https://www.nami.org/Learn-More/Mental-Health-Conditions/depression

 
