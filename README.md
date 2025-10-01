# Data Analysis on Spotify Data

## Project Goal

This project aims to explore Spotify’s dataset by analyzing track features, artist stream statistics, and streaming patterns to identify the factors that influence a song’s popularity.

## Data Source

This data comes from a Kaggle Competition, which provides details about the data.

## Data Exploration

The data has 953 rows and 24 columns. I used the following columns for my data analysis.
 - Track name
 - Artist's name
 - Artist count
 - Released year 
 - Streams count
 
It contains data analysis on [Popular_Spotify_Songs.csv].  

## Features
- Introduction
- Data cleaning
- Data Analysis
- Visualization
- Data Insights
- Conclusions

## Introduction
- Spotify is a digital music service that gives you access to millions of songs. Artists upload their songs or albums, and people get access to their music through the app. Songs and artists with the most streams generate royalties or investments in exclusive content. Spotify identifies songs with the most streams and also predicts which songs are likely to be hits based on the artist's popularity or time of release. It also understands how listener preferences change over time. This dataset contains the most popular songs in 2023. It shows the spotify stream count,the release dates, the track name, and the artist name. From this dataset, we want to get the most popular artist, the most popular songs, the average streams per year, the songs with the highest stream counts, and which top artists consistently produce hits.

  ## Data Cleaning
  - The data we have has 953 rows representing a unique song with its features, and has 24 columns representing track name, artist name, released year, and stream count. Some columns, such as in_shazam charts and key, have 903 and 858 non-null values, which raises questions about the accuracy of our data. The data has missing values, and we need to clean it to have a clear analysis of the data.
 
  - To clean our data, we first check for null values. In the Shazam charts, there are 50 missing values, and the key has 95 missing values. Then we need to drop the missing values. After dropping the missing values, the data now has 817 rows instead of 953. The missing values we dropped, and the data is clear.
 
  ## Data Analysis
  The average stream count for this data is 468.98 million streams. On average, songs in this dataset were released around mid-June. The average release year for this data is 2018, suggesting most hit songs were released around this time. The latest songs from this data are from the year 2023, while the oldest dates to 1930. The streams feature shows high variance, indicating that some songs are extremely popular while others have very few streams. The maximum stream count is 3.5 billion streams, while the lowest 2762 streams, showing a big difference between popular songs and non popular songs.

  ## Data Insights
  Under the data insights, we would like to know the most popular artists on Spotify by streams to highlight the dominant artists in terms of popularity. We also like to know the most streamed songs on Spotify to identify the top hit track in the dataset and provide insight into the ultimate listener preference. We also get the average streams per year to check how popularity of songs changes over time.

  By identifying the most popular artist, we can see which musicians consistently capture the audience’s attention and hold the largest share of streams.Taylor Swift is the most popular artist in Spotify with 1.18 billion streams, followed by Ed Sheeran with 1.1 billion streams, then Bad Bunny with 858 million streams. Eminem follows with 618 million streams, then The Weeknd with 603 million streams. Taylor Swift captures attention on Spotify and has the most streams.

  The top 5 most steamed songs on Spotify is Shape of You with 3.5 billion streams, Sunflower with 2.8 billion streams, One Dance with 2.71 billion streams and Stay with 2.6 billion streams. Shape of You by Ed Sheeran is the most-streamed song on Spotify.

  The average streams per year was the highest between 2012 and 2018, with streams above 1 billion. This shows that during this period, massively popular songs were released.The average streams per year have also increased since 2000, showing that newer songs tend to get more streams, likely due to the growth of Spotify and the streaming culture. However, some older songs like Yellow	by Chris Molitor still dominate the top streams, creating spikes in certain years.
  
  ## Data Visualizations
