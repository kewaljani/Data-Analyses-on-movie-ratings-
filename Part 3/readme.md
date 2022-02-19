
# Prediction

### 1) Apply dimension reduction methods – specifically a PCA – to the data in columns 421-474. As laid out above, these columns contain self-report answers to personality and how these individuals experience movies, respectively. It is us to you whether you do one PCA each for personality and movie experience, or one overall, but regardless of that, we would like you to:
### a) Determine the number of factors (principal components) that you will interpret meaningfully (by a criterion of your choice – but make sure to name that criterion). Include 
#### a Scree plot in your answer.
#### b) Semantically interpret what those factors represent (hint: Inspect the loadings matrix). 
#### Explicitly name the factors you found and decided to interpret meaningfully in 1a). 


! [correlation matrix](https://github.com/kewaljani/Data-Analyses-on-movie-ratings-/blob/main/Part%203/Sc/Correlation.PNG) 
![Spree Plot](https://github.com/kewaljani/Data-Analyses-on-movie-ratings-/blob/main/Part%203/Sc/1st.PNG)

I found 11 eigen values to be more than 1 so for each eigen value I calculated which Question
contribute the most. By plotting the contribution from loading matrix. I have included the plots in
the Code which I have attached with this file.
So, these were the Questions that contributed the most
Is full of energy
The emotions on the screen "rub off" on me - for instance if something sad is happening I get sad or if
something frightening is happening I get scared
Is reserved
Has an assertive personality
I have trouble following the story of a movie
Has few artistic interests
As a movie unfolds I start to have problems keeping track of events that happened earlier
When watching a movie I get completely immersed in the alternative reality of the film
Gender identity (1 = female; 2 = male; 3 = self-described)
Values artistic/aesthetic experiences
Is ingenious/a deep thinker

### 2 Plot the data from columns 421-474 in the new coordinate system, where each dot represents
A person, and the axes represent the factors you found in 1). Hint: If you identified more than 2 meaningful factors, it is a good idea to create several 2D (X vs. Y) subplots for better interpretability As I identified 11 factors the total plots I will get for each question will be 11*11 that is 121 but I am showing random 9

![subplots](https://github.com/kewaljani/Data-Analyses-on-movie-ratings-/blob/main/Part%203/Sc/2nd.PNG) 

### 3 Identify clusters in this new space. Use a method of your choice (e.g. kMeans, DBScan, hierarchical clustering) to do so. Determine the optimal number of clusters and identify which cluster a given user is part of.

Now after getting all the relevant Questions, I Collected them in on array and used Kmeans library to plot the graph but before that I have to select the optimum number of clusters needed for doing so For that I ran the silhoute scores for cluster from 2-10 and got graph as shown below 

![Sillhout score and K-means plot](https://github.com/kewaljani/Data-Analyses-on-movie-ratings-/blob/main/Part%203/Sc/3rd.PNG)

This sates that the optimum number of cluster which I can select is 2 now I applied the clustering algorithm and got 2 clusters of the data divided in {0: 639, 1: 456}. We can give value of user to the Fitted model and will get output of the cluster the user is part of.

### 4 Use these principal components and/or clusters you identified to build a classification model of your choice (e.g. logistic regression, kNN, SVM, random forest), where you predict the movie ratings of all movies from the personality factors identified before. Make sure to use crossvalidation methods to avoid overfitting and assess the accuracy of your model by stating its AUC.

For Part 4 I am using the principal components that I obtained from the PCA and trained the independent variables. It was hard to get multilabel classification from the data as there are fewer scikit libraries but I found random forest that predict the output as multiclass. I divided the data in 80:20 ratio and then trained the 80% data. I tested the remaining testing data and got the accuracy of 83%

### 5 Create a neural network model of your choice to predict movie ratings, using information from all 477 columns. Make sure to comment on the accuracy of this model.

The input to this neural network is vector of length 77. It produces the output vector of length 400. Each element of a vector represents the movie rating prediction. I have used relu as the non-linearity to delete all the negative values. As movie prediction ratings cannot be negative. I have introduced dropout of probability 0.3 to zero 30 percent neurons. Due to this other neighboring neuron won’t just copy their neighbours. They will learn by themselves instead of just copying. I have used MSE loss in order to find how much far away my prediction is from the correct output. By back propagation and updating weights I am reducing the loss and making my prediction come closer to the correct output. I got an average accuracy of 64%.

### 6  which movies contribute the most to the dataset?

I applied the PCA to the data set on 1-400 columns and repeated the above steps which I performed in PCA and found the most correlated movie rating. So instead of asking the user dataset of all the movies we can ask user these 90 movies to obtain the relevant data or replicate the dataset.

![Movie list](https://github.com/kewaljani/Data-Analyses-on-movie-ratings-/blob/main/Part%203/Sc/last.PNG)


