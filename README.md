# MachineLearning_SongPopularity
ECS171 Machine Learning Group14 Group Project

# Description
Dataset: https://www.kaggle.com/datasets/joebeachcapital/top-10000-spotify-songs-1960-now/code

MachienLearning_SongPopularity is designed to predict a song's popularity based on 
different attributes. We hope this project can help people understand how a song's popularity 
is calculated on Spotify, and hopefully improve a song's popularity based on some of the 
attributes.

#Imputation:

Imputation can be done to numeric features where the missing data can be replaced 
with the mean or median of the non-missing data values from that section.
Another Imputation can be done by removing the row or column if there are a lot of missing data values.

#Normalization vs standardization

Normalization would scale a certain value of a feature to be in specific range between 0 and 1 which in the Spotify
data, it cna help bring some of the features in a common range. 
While in standardization, it would be used to center the data near 0 to ensure the features to be similar scales. 
It can ensure the data would have a mean of 0 and have a standar deviation.  

#Data Encoding

One-hot encoding can be applied to columns like "Genre" ann conver them into binary columns if data genre
exist in the row then assgin it as 1 otherwise assign it to be 0. 


#Data transformation

Data transformation that can be used would be normaliztion such that the data that have different scales can be unified. 
Another transformation would standarization where it can set feastures, "Loudness", "Popularity", and others with a
common mean of 0 and a standard deviation of 1.  


# Data Exploration
The original data contains a total of 35 features and 10k data. After inspecting the data, we kept 22 features and removed the rest of the features(Track URI, Album URI, Artist URI...) due to irreverence.

Remaining Features: Track Name, Artist Name(s), Album Name, Album Artist Name(s), Album Release Date, Explicit, Added By, Added At, Artist Genres, Danceability, Energy, Key, Loudness, Mode, Speechiness, Acousticness, Instrumentalness, Liveness, Valence, Tempo, Time Signature, Album Genres(data are empty for this field)

Target Feature: Popularity

Track Name, Artist Name(s), Album Name, Album Artist Name(s): These can be relevant to a song's popularity, as they provide information about the song, artist, and album, which can influence popularity.

Album Release Date: This is often relevant, as the release date can affect a song's popularity, especially in the context of trending and new releases.

Explicit: This indicates whether a song contains explicit content, which may affect its audience and popularity.

Popularity: Target, scale from 0-100

Artist Genres: These can be relevant, as the genre of a song can influence its popularity.

Danceability, Energy, Key, Loudness, Mode, Speechiness, Acousticness, Instrumentalness, Liveness, Valence, Tempo, Time Signature: These audio features (from Spotify's audio analysis) can be highly relevant to popularity, as they describe the musical characteristics of a song.
