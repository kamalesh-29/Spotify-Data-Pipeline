
 🎧 Spotify Data Analytics Pipeline



This project builds a complete Spotify Data Pipeline that extracts track metadata using the Spotify Web API, transforms it using Python, and loads the data into a MySQL database for performing music analytics. Ideal for beginners and students learning Data Engineering.



 📌 Features

- 🎶 Extract Spotify track metadata using the Spotify Web API
- ⚙️ ETL: Extract → Transform → Load process
- 💾 Store structured data in MySQL database
- 📂 Export track data to CSV for easy viewing
- 🐍 Built with Python and popular libraries like Pandas and Spotipy


⚙️ Tech Stack

| Layer       | Tool/Tech             |
|-|--|
| Programming | Python                |
| Database    | MySQL                 |
| API         | Spotify Web API       |
| Libraries   | Pandas, Spotipy, MySQL Connector |



🖥️ Installation Steps

1. Clone the Repository

```bash
git clone https://github.com/kamalesh-a/spotify_data_analytics.git
cd spotify_data_analytics
```
2. Create a Virtual Environment (Optional)

```bash
python -m venv venv
source venv/bin/activate        On Windows: venv\Scripts\activate
```

 3. Install Required Libraries

```bash
pip install spotipy pandas mysql-connector-python
```

 4. Set Spotify API Credentials

- Visit: [Spotify Developer Dashboard](https://developer.spotify.com/dashboard)
- Create a new app and note your `Client ID` and `Client Secret`
- Export credentials as environment variables:

```bash
export SPOTIPY_CLIENT_ID='your-client-id'
export SPOTIPY_CLIENT_SECRET='your-client-secret'
```

> On Windows, use `set` instead of `export`.

 5. Set Up MySQL Database

- Install MySQL and start MySQL server
- Open MySQL and run the schema file:

```bash
mysql -u root -p
CREATE DATABASE spotify_analytics;
USE spotify_analytics;
SOURCE spotify.sql;
```



 🚀 How to Use

 ▶️ Extract Data

```bash
python spotify.py
```

This script will connect to the Spotify API and download metadata like track name, artist, album, popularity, etc.

 💾 Load Data into MySQL

```bash
python spotify_mysql.py
```

This will insert the cleaned and formatted data into your MySQL database.

 🔗 Use URLs from File

Make sure `track_urls.txt` contains valid Spotify track URLs, then:

```bash
python spotify_mysql_urls.py
```

This will run the full ETL process for each URL.



 📊 Sample SQL Queries

```sql
-- Top 10 Most Popular Artists
SELECT artist_name, AVG(popularity) AS avg_popularity
FROM tracks
GROUP BY artist_name
ORDER BY avg_popularity DESC
LIMIT 10;
```

```sql
-- Count of Tracks per Artist
SELECT artist_name, COUNT() AS track_count
FROM tracks
GROUP BY artist_name
ORDER BY track_count DESC;
```

