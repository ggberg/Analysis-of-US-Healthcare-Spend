# ![] Project 3 - Classifying Reddit Posts

---

## Problem Statement

Given students' changing attitudes on unethical behaviors, and given corporations' increasingly-rigorous job applicant screening processes, are models based on natural language processing sophisticated enough to distinguish the linguistic nuances between ethical, unethical, and illegal behaviors posted online?  Could these models be the basis for more sophiticated job screeing tools in the future, and therefore put already ethically at-risk students at even more more of a disadvantage for employment. What are the implications and actions for educators?

---

## Executive  Summary

A recent study by professors at California State University, San Marcos and San Francisco State University, found that students' who were more open to cheating at school also were more open to unethical behavior later on in their jobs and careers. In addition, the study found that 'group-oriented' students had a more relaxed attitude toward cheating than more 'individualistic' students. (1)

A report by Career Builder.com found that up to 70% of businesses use social media as a screening tool for job applicants and new hires.(2)  Top reasons for job denial include: 
- Provocative/inappropriate content, photos, videos = 40%
- Alcohol and drug use = 36%
- Descrimination againse race,gender, religion = 31%
- Illegal and criminal behavior = 30%

Is machine learning sophisticated enough to distinguish linguistic nuances between ethical, unethical, and illegal behaviors posted online and how does this affect students and educators?

A high-level study was conducted on Reddit posts spanning the 'Life Pro Tip' , the 'Unethical Life Pro Tip', and the 'Illegal Life Pro Tip' subreddit groups using the following modelling techniques to determine the predictive capabilities of machine learning. 
- CountVectorizer / TfidfVectorizer
- Logistic Regression
- Naïve Bayes: Binomial/ Multinomial
- Support Vector
- Decision Tree

---

## Data  Dictionary

Online posts sraped from following subreddits:
- LifeProTips='https://www.reddit.com/r/LifeProTips.json'
- UnethicalLifeProTips='https://www.reddit.com/r/UnethicalLifeProTips.json'
- IllegalLifePro Tips='https://www.reddit.com/r/IllegalLifeProTips.json'

|Feature|Type|Subreddit/dataset|Description|
|---|---|---|---|
|title|string |Regular'Ethical'/Unethical/Illegal Life Pro Tips|Title of the post|
|selftext|string|Ethical/Unethical/Illegal|Body of the text|
|subreddit|string/int|Ethical/Unethical/Illegal|Identifier for specific subreddit|
|author|string|Ethical/Unethical/Illegal|Author of post|
|num_comments|int|Ethical/Unethical/Illegal|Number of comments per post|
|score|int|Ethical/Unethical/illegal|Score (thumbs up) per post|
|is_self|string|Ethical/Unethical/Illegal|Reddit indicatro of type of post|
|created_UTC/timestamp|date/time|Ethical/Unethical/Illegal|Timestamps for post|


---

## Results

Three sets of data were run:
- Data 1 = Predicting Unethical vs Ethical posts
- Data 2 = Predicting Illegal vs Unethical posts
- Data 3 = Predicting Illegal vs Ethical posts

Overall results concerning all 3 data sets:
- Titles more accurate than selftext
- Tvec more accurate than Cvec
- Stopwords not an influence - even when creating custom stopword list
- LogReg most accurate model!
- Multinomial Naïve Bayes slightly less accuracy than LogReg but consistently higher Specificity
- Support Vector similar accuracy to LogReg, but with higher overfit and HUGE Time/CPU cost.
- Decision Tree (even with up to 90 levels) ran surprisingly quickly, but had slightly less accuracy than LogReg and had the highest overfit.

Results for best fit models:

|Dataset|Reddit|Baseline|Best model|Results|
|---|---|---|---|---|
|Data1|Unethical vs Ethical|54%|Tvec and LogReg| Accuracy 78%|
|Data2|Illegal vs Unethical| 52%| Tvec and LogReg|Accuracy 76%|
|Data3|Illegal vs Ethical|52%|Tvec and LogReg|Accuracy 90%|

---

## Conclusions and Recommendations

Simple modeling yields reasonable accuracy in predicting if a post and its associated behavior can be categorized as unethical or illegal.  More data sourced, additional feature engineering, and more modelling tecniques will increase accuracy.  It is reasonable to assume employers are capable of screening students and new job candidates based on machine learning nuanced language.

Recommendations:
- Expand on current study to : ensure modelling accuracy, and to refine how online groups influence students’ ‘collectivism’
- Advise University Career Services to enact stricter guidance to graduating students about cleaning and maintaining social profiles.
- Approach University staff to urge more overall education in Ethics.  Ethics is standard study for many disciplines, medical, legal, business, theology.  Increased education in ethics at an earlier stage can begin to curb unhealthy attitudes toward scholastic cheating.


(1)https://www.sciencedaily.com/releases/2019/11/191127121235.htm
(2)https://www.cnbc.com/2018/08/10/digital-dirt-may-nix-that-job-you-were-counting-on-getting.html
