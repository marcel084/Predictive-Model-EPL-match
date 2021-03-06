# **Predictive Model EPL match with R**
This project is related to sports analytics and more specifically to the outcome prediction for a soccer game in the English Premier League. A soccer game in this league has three possible outcomes:
- Home Team Victory
- Away Team Victory
- Draw  

These three outcomes are what makes the prediction, for a soccer game in EPL, more complex than for some other sports like baseball or basketball. The main goal for this project is described as follows:
What is the best classification model, in terms of accuracy, to predict an EPL game using data in real time?
## Libraries
The following libraries are required
* `library(RMySQL)`
* `library(RODBC)`
* `library(tidyverse)`
* `library(purrr)`
* `ibrary(magrittr)`
* `library(data.table)`
* `library(caTools)`
* `library(e1071)`
* `library(zoo)`
* `library(class)`
* `library(rpart)`
* `library(nnet)`
* `library(caret)`
* `library(rpart.plot)`

# **The Process**
The process is detailed in the paper enclosed. The code is structured the EPLpredictor.rmd. This Notebook does the following: 
1. a) Scrapping match results using rvest from [FBref](https://fbref.com/en/comps/9/schedule/Premier-League-Fixtures)
1. b) Transforming data into datasets with variables used to predict the outcome in a match
1. c) Exploratory data analysis for feature selection
1. d) Modeling with the variables obtained from general performance for each Team
1. e) Adding variable history performance matches
1. f) Finding the best model. Hyphotesis testing
1. g) Optimizing the best model
1. h) Predicting the next round
# **How it works**
Once the data is scrapped from the website, it is uploded in an RDS hosted in AWS. This way the data is available for training the model without scrapping any time a round is predicted. The database contains 6 tables, each one stores the data from the last 6 seasons in English Premier League.
# **Results**
The values of accuracy were impacted, in almost 20%, by using the previous outcomes between matches for the same teams playing the match to be predicted.  
Running Anova for different values of accuracy obtained for each model and changing the seed, allowed to confirm that there is significant difference between at least one model and the rest.  
According to Tukey test, it could be confirmed that the best model, in terms of accuracy, is the Classification and Regression Trees model with a significant difference statistically proven with the rest of the models.

![Accuracy](https://github.com/marcel084/Predictive-Model-EPL-match/blob/master/Images/Accuracy.png) ![Accuracy1](https://github.com/marcel084/Predictive-Model-EPL-match/blob/master/Images/Accuracy1.png)

# **Predicting the next round**
The model predicted the Round 30 in the season 19-20 for the English Premier League
Away         | Week          | Season      | Home   | Prediction
------------ | ------------- | ----------- |--------| ----------
Arsenal | 30 | 19-20 | Brighton | Home
Burnley | 30 | 19-20 | Manchester City | Home
Chelsea | 30 | 19-20 | Aston Villa | Away
Crystal Palace | 30 | 19-20 | Bournemouth | Draw
Leicester City | 30 | 19-20 | Watford | Home
Liverpool | 30 | 19-20 | Everton | Draw
Manchester Utd | 30 | 19-20 | Tottenham | Draw
Sheffield Utd | 30 | 19-20 | Newcastle Utd | Draw
Southampton | 30 | 19-20 | Norwich City | Home
Wolves | 30 | 19-20| West Ham | Draw
