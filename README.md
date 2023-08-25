# MachineLearning_SongPopularity
ECS171 Machine Learning Group14 Group Project

# Description
Dataset: https://www.kaggle.com/datasets/joebeachcapital/top-10000-spotify-songs-1960-now/code

MachienLearning_SongPopularity is designed to predict a song's popularity based on 
different attributes. We hope this project can help people understand how a song's popularity 
is calculated on Spotify, and hopefully improve a song's popularity based on some of the 
attributes.

# Model to Be Utilized

Random Forest Model

# Data Preprocessing

**Imputation:**

For numerical values, we will replace the missing values with the random values within the scope. For non-numerical values, we will use different strategies based on different features. Some possible strategies are removing the observation(missing too many attributes), replacing it with the most common value in that feature, and introducing a new category called "Unknown"...

**Data Scaling**

For the random forest models, it is usually not important to scale the data. However, Tempo is significantly greater than all the other numerical values, which I will apply normalization on it.

**Data Encoding**

We will likely use one-hot encoding for most of the categorical data since the categories are 
mostly independent of each other.
One exception is artist genres, which include multiple values for each observation. We 
will use one-hot encoding for each unique genre present in the dataset.


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
