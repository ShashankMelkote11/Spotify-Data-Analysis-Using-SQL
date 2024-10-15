# Spotify SQL Project 
Author: Shashank Melkote
Project: Spotify Data Analysis using SQL
[Click Here to get Dataset](https://www.kaggle.com/datasets/sanjanchaudhari/spotify-dataset)

![Spotify Logo](https://github.com/najirh/najirh-Spotify-Data-Analysis-using-SQL/blob/main/spotify_logo.jpg)

## Table of Contents
 - Project Overview
 - Dataset Description
 - SQL Queries
 - Exploratory Data Analysis (EDA)
 - Questions Answered
 - Technologies Used
 - How to Run the Project
 - Future Enhancements

## Overview
This project is a SQL-based data analysis of a Spotify dataset. The dataset contains information about various tracks, including audio features like danceability, energy, and liveness, as well as popularity metrics such as views, likes, and comments. The goal is to perform Exploratory Data Analysis (EDA) and answer specific business questions using SQL.

## Dataset Description

The dataset contains information on tracks from Spotify, including:
 - Artist details
 - Track and album metadata
 - Audio features (danceability, energy, etc.)
 - Popularity metrics (views, likes, comments)
 - Platform-specific information like streams, official video, and most_played_on

''''
-- create table
DROP TABLE IF EXISTS spotify;
CREATE TABLE spotify (
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
    licensed BOOLEAN,
    official_video BOOLEAN,
    stream BIGINT,
    energy_liveness FLOAT,
    most_played_on VARCHAR(50)
);
''''

## SQL Queries


The project includes a variety of SQL queries, such as:
 - Basic filtering and grouping
 - Aggregating functions like COUNT, SUM, AVG
 - Sorting data with ORDER BY
 - Removing invalid data with DELETE
 - Retrieving specific subsets of data for insights
---

## Exploratory Data Analysis (EDA)
### Key Insights from EDA:

 - Total number of artists: SELECT COUNT(DISTINCT artist)
 - Album types: SELECT DISTINCT album_type
 - Maximum and minimum track durations: MAX() and MIN()
 - Tracks with more than 1B views: SELECT * WHERE views > 1000000000
 - Total number of comments for licensed tracks: SUM(comments) WHERE licensed = 1


## Technology Stack
- **Database**: Microsoft SQL Server
- **Tools**: Microsoft SQL Server Management Studio (SSMS)

## How to Run the Project
 - Clone the repository.
 - Import the dataset into your SQL Server.
 - Run the provided SQL queries using Microsoft SQL Server Management Studio (SSMS).
 - Explore the results of each query, modifying them as needed for deeper insights.


## Next Steps
 - Add more complex queries for deeper insights, such as trend analysis on track popularity over time.
 - Integrate the SQL analysis with visualization tools like Tableau or Power BI for better representation of insights.
 - Clean the dataset further by addressing missing values or other inconsistencies.
