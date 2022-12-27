# ################ #
# Machine Learning #
# ################ #

+ Supervised learning: teach the model, labeled dataset, (attributes, feature), classification & regression 
+ Feature is an individual measurable property or characteristic of a phenomenon
+ A label is the thing we're predicting-the y variable in simple linear regression. Data can be Numerical or Categorical
+ Unsupervised learning, algos complex than supervised, unlabeled data
+ Decision tree 
    - supervised learning, classification or regression
    - cons small variation in the data sight generate a completely different tree 
    - pros easy and simple to understand & interrupt, Can analyze both numerical and categorical data. 
+ Naive Bayes
    - conditional probability
    - Naive Bayes comes handy since you can train it quickly.
    - You can use it when you have limited resources in terms of CPU and Memory. 
    - It is usually used for Real-time predictions, Multi-class Predictions, Text classification, Spam filtering, and Sentiment Analysis.
+ Linear Regression
+ SVM (Support Vector Machine)
    - SVM is all about identifying the right hyper plane. To decide the right hyper-plane, we need to maximize the distances between the nearest data point (either class) and hyper-plane. 
    - SVM works well with clear margin of separation & high dimensional spaces.
+ Kernel function 
    - Kernal methods provide ways to manipulate data as though it were projected Into a higher dimensional space, by operating on it in its original space.
+ Neural Network
    - Neural Networks have a broad spectrum of data-intensive applications such as,
        1. Process Modeling and Control
        2. Machine Diagnostics 
        3. Target Recognition
        4. Medical Diagnosis 
        5. Credit Rating
        6. Financial Forecasting and so on.
+ Clustering
    - unsupervised learning
    - two Types
        1. K-Means Clustering
        2. Hierarchical Clustering (useful when we don't know the number of clusters required)
+ K-means clustering
    - Iterate until stable (= no object move group):
        * Determine the centroid coordinate.
        * Determine the distance of each object to the centroids.
        * Group the object based on minimum distance (find the closest centroid).
+ Cost Function is used to minimize the squared error, ie. to tells about the accuracy of model.
+ Gradient Descent
    - keep finding the local minima to reach from top to down the hill, where down hill is the most favourable solution
+ Convergence
    - If the learning rate is small then the convergence takes time
    - If the learning rate is high the values overshoot 
    - Initializing the right learning rate is very important.
+ Feature Scaling
    - When there are multiple features and each feature variable has a large magnitude, combining them into model and predicting a value becomes computationally intensive.
    - In scaling, each feature / variable is divided by its range (maximum minus minimum)
    - The result of scaling is a variable in the range of 1
    - This eases the computation intensity to a considerable extent
+ Sigmold/Logistic function 
+ The decision boundary or threshold is the line that separates the area where y = 0 and where y = 1. The hypothesis function creates the decision boundary
+ Optimal Threshold
    - Lower threshold might lead to False Positives
    - Higher threshold leads to many cases not classifying properly
+ Best Practice
    - Use the training set for finding the optimal parameters for the cost function
    - Use the validation set to get the polynomial with the least error 
    - Use the test set for estimating the generalization error
+ Underfitting: high bias
+ Overfitting: high variance
+ How are the predictions far off from the actual values is measured by Bias 
+ To what extent are the predictions for a given point change between various realizations of the model is measured by variance
