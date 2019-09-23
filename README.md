# Amazon-Fine-Food-Reviews-Classification-NLP
## Abstract:  
The project aimed at building best working model for classification of positive and negative reviews.  
Apply Logistic Regression algorithm using each technique.

## Dataset:   
The dataset used is https://www.kaggle.com/snap/amazon-fine-food-reviews.  
This dataset consists of reviews of fine foods from amazon. The data span a period of more than 10 years, including all ~500,000                reviews up to October 2012. Reviews include product and user information, ratings, and a plain text review.  It also includes reviews            from all other Amazon categories.

## Procedure to execute classification is as follows:
_Step1_: Data Pre-processing is applied on given amazon reviews data-set.And Take sample of data from dataset because of computational limitations.  
_Step2_: Time based splitting on train and test datasets.  
_Step3_: Apply Feature generation techniques(Bow,tfidf).  
_Step4_: Apply Logistic Regression algorithm using each technique.  
_Step5_: To find lambda using gridsearch cross-validation and random cross-validation.  
_Step5_: L2 regularization.  
_Step6_: Feature Importance for postive and Negative reviews:    
         1. Most Important Feature.  
         2. Bar plot of top 15 Important Features.  
         
### Preprocessing 
Transforming _score_ column by writting "positive" for values greater than 3 and "negative" for values less than or equal to 3.  
Sorting data according to ProductId in ascending order.  
Every datasets contains some unwanted data.Raw data is preprocessed by removing duplication.  
#### Graph of positive and negative reviews after removing duplication:    
![alt text](/Images/Graph.PNG)  
Our data requires some preprocessing before we go on further with analysis and making the prediction model.  
Hence in the Preprocessing phase we do the following in the order below:-  
#### Review Text:
         1 Begin by removing the html tags.  
         2 Remove any punctuations or limited set of special characters like , or . or # etc.  
         3 Check if the word is made up of english letters and is not alpha-numeric.  
         4 Check to see if the length of the word is greater than 2 (as it was researched that there is no adjective in 2-letters).  
         5 Convert the word to lowercase.  
         6 Remove Stopwords.  
         7 Finally Snowball Stemming the word (it was obsereved to be better than Porter Stemming).  
         8 After which we collect the words used to describe positive and negative reviews. 
### Splitting Training and Testing dataset based on Time:
The column Time is based on unix timestamp.The unix time stamp is a way to track time as a running total of seconds and In time technically does not change no matter where you are located on the globe. This is very useful to computer systems for tracking and sorting dated information in dynamic and distributed applications both online and client side. https://www.unixtimestamp.com/ .  
So here,time conversion is not necessary to process on amazon data.
### Methods used to convert text into vector:  
   **1** Bag of Words      
   **2** Tf-idf      
### Optimal Lambda for Logistic Regression:
**_lambda_LR_** is written function to calculate the optimal lambda value for Logistic Regression.
GridsearchCV and RandomsearchCV method are used to obtain optimal lambda with L2 penality,different scoring options ( e.g,accuracy,precision,recall and F1-score) and broad range of lambda.  
Best parameter lambda and penalty for which model performs very well is obtained. 
#####         Below snap is of Confusion matrix for TF-IDF with RandomSearch CV & L1 regularization:
  ![alt text](/Images/Confusion.PNG)
### Feature Importance for Logistic Regression:

## Conclusion:
|       Model       |Vectorizer|   SearchCV   |Best penalty|Optimal lambda|Training error|Test error|Accuracy| F1  |recall|precision|
|-------------------|----------|--------------|------------|-------------:|-------------:|---------:|-------:|----:|-----:|--------:|
|Logistic Regression|BoW       |GridSearchCV  |l2          |        1.0000|       0.00504|     20.46|  0.7954|76.53| 76.32|    76.76|
|Logistic Regression|BOW       |RandomsearchCV|l2          |        0.0036|       0.98678|     16.38|  0.8362|80.59| 79.51|    82.21|
|Logistic Regression|TF-IDF    |RandomsearchCV|l2          |        0.4245|       0.00504|     20.04|  0.7996|76.94| 76.66|    77.27|
|Logistic Regression|TF-IDF    |GridSearchCV  |l2          |        1.0000|       0.00000|     21.90|  0.7810|68.75| 67.20|    84.09|

* Above Table shows the performance of trained and tested model with Logistic Regression.  
* Confusion matrix and scoring metrics values for TF-IDF with RandomSearch CV & L1 regularization is comparatively best with other trained model.  
* After comparing the developed models, Logistic Regression model with TF-IDF with RandomsearchCV ,l1 regularization works the best to predict the polarity of reviews among all models.  
