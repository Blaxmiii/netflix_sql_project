# Netflix Movies and TV shows data analysis using SQL

![Netflix Logo](https://github.com/Blaxmiii/netflix_sql_project/blob/main/download.png)

##Overview

This project focuses on analyzing Netflix Movies and TV Shows data using SQL. The dataset includes information about titles, genres, release years, ratings, countries, and durations. The goal of this project is to explore trends, extract insights, and practice SQL querying skills through real-world data analysis.

##Objectives

-Analyze the distribution of content types(Movies and TV shows).

-Identify the most common ratings for Movies and TV shows.

-List and analyze content based on release years,countries and durations.

-Explore and categorize content based on specific criteria and keywords.

##Dataset

The data for this project is sourced from the kaggle dataset:

-Dataset Name: Netflix Movies and TV Shows

-Source: Kaggle

-Link: https://www.kaggle.com/datasets/rahulvyasm/netflix-movies-and-tv-shows

##Schema

BUSINESS problems and solution

CREATE TABLE netflix(

  show_id VARCHAR(5),
  
  type VARCHAR(20),
  
  title VARCHAR(250),
  
  director VARCHAR(250),
  
  casts VARCHAR(1000),
  
  country VARCHAR(250),
  
  date_added VARCHAR(50),
  
  release_year INT,
  
  rating VARCHAR(20),
  
  duration VARCHAR(50),
  
  listed_in VARCHAR(100),
  
  description VARCHAR(1000)
  
);

SELECT * FROM netflix;

SELECT COUNT(*) AS TOTAL_CONTENT
FROM netflix;

SELECT
  DISTINCT type
FROM netflix;

--11 Bussiness problems

1.count the number of movies vs TV shows

SELECT type,COUNT(*) AS total_type

FROM netflix

GROUP BY type;

2.find the most common rating for MOVIES AND TV shows

SELECT type,

      rating, 
	  COUNT(*),
	  MAX(rating)
	  
FROM netflix

GROUP BY 1,2

ORDER BY 3 DESC;

3.List all movies realesed in a specific year (e.g 2020)

SELECT type,release_year 

FROM netflix

WHERE release_year=2020;
	
4.find the top 5 countries with the most content on netflix

SELECT country,COUNT(show_id)AS total_content

FROM netflix

GROUP BY 1

ORDER BY COUNT(show_id)DESC

LIMIT 5;

5.identify the longest movie

SELECT * FROM netflix

WHERE

    type = 'Movie'
    AND
    duration = (SELECT MAX(duration)FROM netflix)

6.find content added in the last 5 years

SELECT*FROM netflix

WHERE 

    TO_DATE(date_added,'month DD, YYYY') >= CURRENT_DATE -INTERVAL '5 years'

7.find all movies and TV shows by director 'Rajiv Chilaka'

SELECT * FROM netflix

WHERE director = 'Rajiv Chilaka'	

8.count the number of content items in each genre

SELECT

    UNNEST(STRING_TO_ARRAY(listed_in,','))as genre,
	COUNT(show_id)AS TOTAL_CONTENT
	
FROM netflix

GROUP BY 1;

9.list all movies that are documentaries

SELECT * FROM netflix

WHERE listed_in LIKE '%Documentaries%';

10.find all content without director

SELECT * FROM netflix

WHERE director is NULL;

11.find how many movies actor salman khan appeared in last 10 years

SELECT * FROM netflix

WHERE casts ILIKE '%Salman khan%'
    AND
	release_year > EXTRACT(YEAR FROM CURRENT_DATE) - 10;

##Conclusion

-Analyzed Netflix Movies and TV Shows data using SQL.

-Explored trends in genres, ratings, and content types.

-Identified patterns in Netflix content across different countries and years.

-Improved SQL skills including filtering, grouping, joins, and aggregations.

-Gained practical experience working with a real-world dataset.

-Extracted meaningful insights from entertainment data analysis.

##Connect with Me

LinkedIn: https://www.linkedin.com/in/b-laxmi-6b18a1341/

Instagram: https://www.instagram.com/blaxmiii_
	

  




