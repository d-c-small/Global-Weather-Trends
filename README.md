# Global Weather Trends
Compared global weather trends to weather trends in a major city I lived closest to (San Jose, CA).

## About the Data
This data was pulled from Udacity's "Exploring Weather Trends" Database in the Data Analytics Nanodegree Program using postgre SQL.
Once pulled from the database it was aggregated into an [Excel file](https://1drv.ms/x/s!Ap-1hbhCWewnsiaQmVuEY7nEb4Zk?e=SDLJvj).

### Outline of Steps Taken Using SQL
1. I wrote this query using SQL to view the data and figure out how my country’s name was written
      - SELECT *
      - FROM city_list
      - ORDER BY country;
2. This query was used to view a list of the cities in the United States in order to find the one closest to 
me. Which is San Jose
      - SELECT city
      - FROM city_list
      - WHERE country = 'United States'
      - ORDER BY city;
3. This query was used to view the weather data for San Jose and then I exported the csv into an excel sheet.
      - SELECT *
      - FROM city_data
      - WHERE city = 'San Jose' AND country = 'United States';
4. I wrote this query to view the global weather data. I saw that the global weather data was first 
recorded in 1750 but weather data for San Jose did not start being recorded until 1849 so I decided 
to aggregate the data from the two tables and show global temperatures for the years the average 
temperature was recorded for San Jose.
      - SELECT *
      - FROM global_data;
5. I wrote this query to aggregate the data for San Jose and global average temperatures. I then 
exported the csv into an excel sheet.
      - SELECT city_data.*, global_data.avg_temp AS global_avg_temp
      - FROM global_data
      - JOIN city_data
      - ON global_data.year = city_data.year
      - WHERE city_data.city = 'San Jose' AND city_data.country = 'United States';

### Outline of Steps Taken Using Excel
1. I noticed that the average temperature was in Celsius for both San Jose and Global temperatures. I 
converted the data to Fahrenheit so that I would have a better understanding of the data.

2. I then calculated a 10-year moving average for San Jose as SJ_10yr_MA and Global Weather as 
Global_10yr_MA

3. I converted this data into a table and created a line chart that compares San Jose’s temperatures 
with global temperatures using the moving averages.

![San Jose vs  Global Temperature](https://user-images.githubusercontent.com/100544166/195218865-f555255c-06ec-424a-b46e-cca4dacb377d.png)

## Observations
1. The first observation I made when viewing the data is that San Jose has a higher average 
temperature than the global average temperature. San Jose has consistently been 
recorded as about 10°F hotter each year since 1850 than the average global 
temperature.

2. The second observation I made is that the changes in San Jose’s temperature from 1850 
to 2013 has increased by about 5°F. The increase in temperature for the average global 
temperature from 1850 to 2013 was about 3°F. In 1850 the average temperature was 
56.84 in San Jose and 46.22 Globally. In 2013 the average temperature for San Jose was
61.21 and 49.3 Globally.

3. Looking at the line graph, San Jose’s average temperature is consistently hotter each 
year than the average global temperature. If you look closely at the most recently 
recorded years, you can see the average temperatures for both San Jose and Globally 
increases slightly.

4. The information I have gathered from this data is that while temperatures remained 
fairly consistent throughout the 19th and 20th centuries there does seem to be a larger
increase in average temperatures in the 21st century. The world does appear to be 
getting hotter more rapidly in the 21st century compared to the last couple hundred 
years.

5. This increase in temperature is more clearly seen in San Jose’s average temperature 
with the highest recorded temperature being in 2013 at 61.21°F. This alone is 2°F higher 
than the year prior at 59.09°F. The first time San Jose’s Average Temperature reached 
60°F was in 1996.

