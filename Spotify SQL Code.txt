
--Spotify SQL Project by Shashank Melkote

-- create table
DROP TABLE IF EXISTS Spotify;
CREATE TABLE Spotify (
    artist VARCHAR(255),
    track VARCHAR(255),
    album VARCHAR(255),
    album_type VARCHAR(50),
    danceability FLOAT,
    energy FLOAT,
    loudness FLOAT,
    speechiness FLOAT,
    acousticness FLOAT,
    instrumentalness FLOAT,
    liveness FLOAT,
    valence FLOAT,
    tempo FLOAT,
    duration_min FLOAT,
    title VARCHAR(255),
    channel VARCHAR(255),
    views FLOAT,
    likes BIGINT,
    comments BIGINT,
    licensed FLOAT,
    official_video FLOAT,
    stream BIGINT,
    energy_liveness FLOAT,
    most_played_on VARCHAR(50)
);

SELECT * FROM Spotify..SpotifyDataset


--EDA
SELECT COUNT(*) FROM SpotifyDataset

SELECT COUNT(DISTINCT artist) as Total_Artists FROM Spotify..SpotifyDataset 

SELECT DISTINCT album_type FROM SpotifyDataset

SELECT MAX(duration_min) as MAXIMUM FROM SpotifyDataset
SELECT MIN(duration_min) as MINIMUM FROM SpotifyDataset


--As MIN DURATION WAS 0, Deleting the Songs

DELETE FROM SpotifyDataset 
WHERE duration_min = 0

SELECT * FROM SpotifyDataset 
WHERE duration_min = 0

SELECT DISTINCT most_playedon FROM SpotifyDataset



--Q1. Retrieving the names of all tracks with more than 1B streams

SELECT * FROM SpotifyDataset 
WHERE views > 1000000000


--Q2. List all the albums and their repective artists

SELECT DISTINCT(album),artist From SpotifyDataset
Where Album is not null
ORDER BY 1


--Q3. Get Total number of comments where licensed = TRUE

SELECT SUM(Comments) as TotalComments From SpotifyDataset Where Licensed = 1


--Q4. Find all tracks where albumtype = single
SELECT * FROM SpotifyDataset
Where Album_type = 'single'


--Q5. Count the number of songs by each artist

Select Artist, COUNT(*) as TotalSongs
FROM SpotifyDataset
Group by artist
Order by 2 Asc

------------------------------------

--Q6. Calculate the average Danceability of tracks in each album

Select album, AVG(danceability) as average_danceability FROM SpotifyDataset
Group by Album
Order by 2 desc



--Q7. Find the top 5 tracks with the highest energy
Select TOP 5 track, MAX(EnergyLiveness) as Liveness FROM SpotifyDataset
Group by track
Order by 2 Desc


--Q8. List all tracks along with their views and likes where official video = true

SELECT track, SUM(views) as Total_Views, SUM(likes) as total_likes FROM SpotifyDataset
WHERE official_video = 1
Group BY Track
ORDER BY 2 DESC


--Q9. For Each album, claculate the total views of all associated tracks

SELECT Album, SUM(Views) as Total_Views from SpotifyDataset
Group by ALbum
Order By 2 Desc


--Q10. Retrieve the track names that have been streamed on spotify more than youtube

SELECT track, stream,  most_playedon from SpotifyDataset
WHERE most_playedon = 'Spotify'
Order by 2 desc