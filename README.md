# Amazon-Fine-Food-Reviews
Dataset : https://www.kaggle.com/snap/amazon-fine-food-reviews
          This dataset consists of reviews of fine foods from amazon. The data span a period of more than 10 years, including all ~500,000           reviews up to October 2012. Reviews include product and user information, ratings, and a plain text review. It also includes               reviews from all other Amazon categories.
* Step1: Data Pre-processing is applied on given amazon reviews data-set.And Take sample of data from dataset because of computational             limitations
* Step2: Time based splitting on train and test datasets.
* Step3: Apply Feature generation techniques(Bow,tfidf)
* Step4: Apply Logistic Regression algorithm using each technique.
* Step5: To find lambda using gridsearch cross-validation and random cross-validation
* Step5: L2 regularization


Conclusion:
|       Model       |Vectorizer|   SearchCV   |Best penalty|Optimal lambda|Training error|Test error|Accuracy| F1  |recall|precision|
|-------------------|----------|--------------|------------|-------------:|-------------:|---------:|-------:|----:|-----:|--------:|
|Logistic Regression|BoW       |GridSearchCV  |l2          |        1.0000|       0.00504|     20.46|  0.7954|76.53| 76.32|    76.76|
|Logistic Regression|BOW       |RandomsearchCV|l2          |        0.0036|       0.98678|     16.38|  0.8362|80.59| 79.51|    82.21|
|Logistic Regression|TF-IDF    |RandomsearchCV|l2          |        0.4245|       0.00504|     20.04|  0.7996|76.94| 76.66|    77.27|
|Logistic Regression|TF-IDF    |GridSearchCV  |l2          |        1.0000|       0.00000|     21.90|  0.7810|68.75| 67.20|    84.09|
