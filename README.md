# MachineLearning_SongPopularity
ECS171 Machine Learning Group14 Group Project

# Description
Dataset: https://www.kaggle.com/datasets/joebeachcapital/top-10000-spotify-songs-1960-now/code

MachienLearning_SongPopularity is designed to predict a song's popularity based on 
different attributes. We hope this project can help people understand how a song's popularity 
is calculated on Spotify, and hopefully improve a song's popularity based on some of the 
attributes.

# Model to Be Utilized

**Random Forest Model**

Random Forest is chosen for its capability to handle both numerical and categorical features, making it a versatile choice for this dataset.
Encoding: Label Encoding is used for 'Artist Name(s)' and 'Album Artist Name(s)' instead of One-Hot Encoding for efficiency reasons. Label Encoding is chosen for these features, as One-Hot Encoding would result in an excessive number of columns. Certain data columns were removed to improve model performance after encoding.
Objective: The Random Forest model is employed to classify songs into five popularity categories ('0-20', '21-40', '41-60', '61-80', '81-100') based on the provided features.

**Polynomial Regression**

By using polynomial regression, we can model the relationship between the independent variables and the popularity of the songs. This helps us to identify the factors that are important for song popularity and to help us make predictions about the popularity of the songs. Additional preprocessing is converting the dataframe imported using pandas to numpy arrays and data should be reshaped, so the data can be used to be split into train, test and validate. Use the sets to build a model and refine its accuracy.

**K-means Clustering**

We can use K-means clustering which is unsupervised learning. We felt K-means clustering is a good model that can be used to predict the data since there are multiple features that need to be modeled to predict the popularity of the song. The additional data preprocessing is required to remove all the labels from the data since unsupervised learning does not need labeled data. We are still really sure about this because we haven't gone through unsupervised learning a lot in class.


# Data Preprocessing

**Imputation:**

For numerical values, we will replace the missing values with the random values within the scope. For non-numerical values, we will use different strategies based on different features. Some possible strategies are removing the observation(missing too many attributes), replacing it with the most common value in that feature, and introducing a new category called "Unknown"...

**Data Scaling**

For the random forest models, it is usually not important to scale the data. However, Tempo is significantly greater than all the other numerical values, which I will apply normalization to it.

**Data Encoding**

For the Random Forest model, we are using Label Encoding for Artist Name(s) and Album Artist Name(s) instead of One Hot Encoding since 
One Hot Encoding would take more than 7000 columns while Label Encoding would take less. Furthermore, some data columns would be removed 
so the model would perform better. 


**Data transformation**

Not necessary for the random forest model.


# Data Exploration

The original data contains a total of 35 features and 10k data. After inspecting the data, we kept 22 features and removed the rest of the features(Track URI, Album URI, Artist URI...) due to irreverence.

Remaining Features: Track Name, Artist Name(s), Album Name, Album Artist Name(s), Album Release Date, Explicit, Added By, Added At, Artist Genres, Danceability, Energy, Key, Loudness, Mode, Speechiness, Acousticness, Instrumentalness, Liveness, Valence, Tempo, Time Signature, Album Genres(data are empty for this field)

Target Feature: Popularity

Track Name, Artist Name(s), Album Name, Album Artist Name(s): These can be relevant to a song's popularity, as they provide information about the song, artist, and album, which can influence popularity.

Album Release Date: This is often relevant, as the release date can affect a song's popularity, especially in the context of trending and new releases.

Explicit: This indicates whether a song contains explicit content, which may affect its audience and popularity.

Popularity: Target, scale from 0-100

Artist Genres: These can be relevant, as the genre of a song can influence its popularity.

Danceability, Energy, Key, Loudness, Mode, Speechiness, Acousticness, Instrumentalness, Liveness, Valence, Tempo, and Time Signature: These audio features (from Spotify's audio analysis) can be highly relevant to popularity, as they describe the musical characteristics of a song.

# Data Encoding for Random Forest Model

In this method, we split the data into 5 categories, 0 ~ 4 represents 0 ~ 20, 21 ~ 40, 41 ~ 60, 61 ~ 80, and 81 ~ 100. We tend to use this model to predict which categories will the value fall into because we think this is more reasonable than using the model to predict the exact value.

For encoding the date, we use label encoding instead of One Hot encoding, since there will be more than 7000 columns if we use One Hot encoding. 

# Build the Basic Random Forest Model
We use RandomForestClassifier as our estimatetor. The train-test ratio is 80:20. After training our first model, we can get a training score of 99% and a test score of 33%. Since there is a large gap between training and testing scores, the current model falls into the overfitting issue.

# Build the Decision Tree Model/SVM Model

For numerical values, we will replace the missing values with the random values within the scope. For non-numerical values, we will use different strategies based on different features. Some possible strategies are removing the observation(missing too many attributes), replacing it with the most common value in that feature, and introducing a new category called "Unknown"...

For encoding, we used the same encoding as the first version of our Random Forest Model which was label encoding.

We use DecisionTreeClassifier as our estimator. The train-test ratio is 80:20. After training the model, the training accuracy resulted
in 99% while the test accuracy resulted in 29%. Comparing the two accuracies, the training accuracy is much higher which would 
result in overfit but also would mean the model has a difficult time in generalizing. 

In addition, we created an SVM model to further test the data. This was done with the SVC classifier as the estimator. The data is then scaled 
with StandardScaler and transformed using a fitting scaler to ensure they are in the same scale. After training the model, the training accuracy resulted in 44% while the test accruacy resulted in 36%. The gap between training and testing is much lower than the Decision Tree Model but it could potentially cause an overfit since training accuracy is higher than testing accuracy.
