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

  ## Data Loading
   ```python
   file_path=r"C:\Users\User\Documents\Phase1_Project\Popular_Spotify_Songs.csv"
  with open(file_path, encoding="latin1") as file:
    reader = csv.DictReader(file)
    for row in reader:
        row
  ```
  ## Data Cleaning
  ```python
  df.info()
  ```
  - The data we have has 953 rows representing a unique song with its features, and has 24 columns representing track name, artist name, released year, and stream count. Some columns, such as in_shazam charts and key, have 903 and 858 non-null values, which raises questions about the accuracy of our data. The data has missing values, and we need to clean it to have a clear analysis of the data.
  ```python
  df.isnull().sum()
   ```
  ```python
  df.dropna(inplace=True)
    ```
 - To clean our data, we first check for null values. In the Shazam charts, there are 50 missing values, and the key has 95 missing values. Then we need to drop the missing values. After dropping the missing values, the data now has 817 rows instead of 953. The missing values we dropped, and the data is clear.
 
  ## Data Analysis
  
   ```python
  df.describe()
  ```
  The average stream count for this data is 468.98 million streams. On average, songs in this dataset were released around mid-June. The average release year for this data is 2018, suggesting most hit songs were released around this time. The latest songs from this data are from the year 2023, while the oldest dates to 1930. The streams feature shows high variance, indicating that some songs are extremely popular while others have very few streams. The maximum stream count is 3.5 billion streams, while the lowest 2762 streams, showing a big difference between popular songs and non popular songs.

  ## Data Insights
  Under the data insights, we would like to know the most popular artists on Spotify by streams to highlight the dominant artists in terms of popularity. We also like to know the most streamed songs on Spotify to identify the top hit track in the dataset and provide insight into the ultimate listener preference. We also get the average streams per year to check how the popularity of songs changes over time.
  ### Most popular artists on Spotify
```python
most_popular_artists = (df.groupby("artist(s)_name")["streams"].sum().sort_values(ascending=False))
print("Most popular artists:\n", most_popular_artists.head())
```
   ### Output
 - Most popular artists:
  - Taylor Swift - 11851151082.00
  - Ed Sheeran   - 11051252012.00
  - Bad Bunny    - 8582384095.00
  - Eminem       - 6183805596.00
  - The Weeknd   -  6038640754.00

By identifying the most popular artist, we can see which musicians consistently capture the audience’s attention and hold the largest share of streams. Taylor Swift is the most popular artist in Spotify with 1.18 billion streams, followed by Ed Sheeran with 1.1 billion streams, then Bad Bunny with 858 million streams. Eminem follows with 618 million streams, then The Weeknd with 603 million streams. Taylor Swift captures attention on Spotify and has the most streams.
  
  ### Most-streamed songs on Spotify
  ```python
  top_songs = df.groupby("track_name")["streams"].sum().sort_values(ascending=False).head(5)
  print(top_songs)
```
   ### Output
   track_name
  - Shape of You                -                    3562543890.00
  - Sunflower - Spider-Man: Into the Spider-Verse -   2808096550.00
  - One Dance                    -                   2713922350.00
  - STAY (with Justin Bieber)    -                  2665343922.00
  - Believer                     -                 2594040133.00

  The top 5 most steamed songs on Spotify is Shape of You with 3.5 billion streams, Sunflower with 2.8 billion streams, One Dance with 2.71 billion streams and Stay with 2.6 billion  streams. Shape of You by Ed Sheeran is the most-streamed song on Spotify.
   ### Average streams per year
   ```python
  df = df[df["released_year"] >= 2000]
  avg_streams_per_year = (df.groupby("released_year")["streams"] .mean() .sort_index())
  print(avg_streams_per_year)
```
  ### Output
  - 2010 -  1048400819.17
  - 2011 -   878452623.44
  - 2012 -  1029740974.67
  - 2013 -  1362225297.20
  - 2014 -  1275126822.67
  - 2015 -  910423256.33
  - 2016 -  1135476212.53
  - 2017 -  1497372434.68
  - 2018 -  1349253397.33
  - 2019 -   858923124.44
  - 2020 -   784012453.13
  - 2021 -   548942993.67
  - 2022 -   279439530.51
  - 2023 -  143932389.40
  The average streams per year was the highest between 2012 and 2018, with streams above 1 billion. This shows that during this period, massively popular songs were released. The average   streams per year have also increased since 2000, showing that newer songs tend to get more streams, likely due to the growth of Spotify and the streaming culture. However, some older songs like Yellow	by Chris Molitor still dominate the top streams, creating spikes in certain years.
  
  ## Data Visualizations
   ### Bar chart showing the most popular artists on Spotify by streams
   ```python
   artist_streams = (
    df.groupby("artist(s)_name")["streams"].sum()
      .sort_values(ascending=False)[:10])

 plt.figure(figsize=(12,8))
 plt.bar(artist_streams.index, artist_streams.values, color=("red"))
 plt.title("Top 10 Artists by Total Streams")
 plt.xlabel("Artist")
 plt.ylabel("Total Streams(in billions)")
 plt.show()
```
 Artists like Taylor Swift, Ed Sheeran, The Weeknd appear multiple times to mean that popular artists consistently produce high-stream songs. A song featured by Taylor Swift and Ed Sheeran is likely to hit the chats because they are popular. Same to a son released by The Weeknd and Eminem or Harry Styles.
   ### Trendline showing average streams per release year
   ```python
avg_per_year = df.groupby("released_year")["streams"].mean()
avg_per_year.plot(kind="line", marker=" ")
plt.xlabel("Release year")
plt.ylabel("Average Streams")
plt.title("Average Streams by Release Year")
plt.show()
```
 Songs like Numb and Mr.Brightside released in 2003, had the most streams in average over the years, with both songs having more than a billion streams in 1 year. It is also clear that songs released in 2005 did not get as much streams, hence a sharp drop. There is a huge stream growth in songs released from 2010 to 2020, showing that the most popular songs on Spotify were released during this time. 
  ### Bar chat showing top 10 most-streamed songs
  ```python
top_songs = df.groupby("track_name")["streams"].sum().sort_values(ascending=False)[:10]
plt.figure(figsize=(12,8))
plt.bar(top_songs.index, top_songs.values)
plt.xticks(ha="center", va="bottom",fontsize=9, rotation=90)  
plt.xlabel("Songs")
plt.ylabel("Total Streams(in billions)")
plt.title("Top 10 Most Streamed Songs")
plt.show()
```
Shape of You by Ed Sheeran is the most-streamed song on Spotify with 3.5 billion streams, followed by Sunflower with 2.8 billion streams, One Dance with 2.71 billion streams, and Stay with 2.6 billion streams. 

## Conclusion
In conclusion, the average streams per year tend to increase for newer release years, reflecting Spotify’s growth and the popularity of streaming in the 2010s and 2020s. Most popular artists also have the most streams, meaning the streams are mostly influenced by the popularity of the artist. Popular artists also influence the number of streams, and songs featured with popular artists are likely to have more streams too.
