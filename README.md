# SQLQueries
Assignments using data from the Paris 2024 Summer Olympics

## Table of Contents
- [Introduction](#introduction)
- [Installation](#installation)
- [olympics-postgresql](#olympics-postgresql)
- [OlympicData](#olympicdata)
- [Contributors](#contributors)
- [License](#license)
- [Contact](#contact)

## Introduction

The Paris 2024 Olympics brought together nations from across the globe to celebrate athletic excellence and international camaraderie. Participants from various countries showcased their talents, making this event an unforgettable spectacle.

### Facts about Participating Countries
- Over 200 countries participated in the Paris 2024 Olympics.
- Notable first-time participants included countries like Tuvalu and the Vatican City.
- The United States, China, and Russia had the largest contingents of athletes.

### Most Popular Events
1. 100m Sprint
2. Gymnastics All-Around
3. Swimming 100m Freestyle
4. Soccer
5. Basketball
6. Tennis Singles
7. Boxing
8. Wrestling
9. Weightlifting
10. Marathon

### Most Famous Athletes and Their Countries
- **Simone Biles** (USA) - Gymnastics
- **Caeleb Dressel** (USA) - Swimming
- **Eliud Kipchoge** (Kenya) - Marathon
- **Novak Djokovic** (Serbia) - Tennis
- **Sunisa Lee** (USA) - Gymnastics
- **Naomi Osaka** (Japan) - Tennis
- **Armand Duplantis** (Sweden) - Pole Vault
- **Katie Ledecky** (USA) - Swimming
- **Mutaz Essa Barshim** (Qatar) - High Jump
- **Kevin Durant** (USA) - Basketball

### Goal of SQL Queries
The goal of these SQL queries is to organize data in a manner that allows us to understand the successes of certain individuals and teams at the Paris 2024 Olympics.

### Concepts Utilized
- **SELECT**: Used to specify the columns to be retrieved.
- **FROM**: Indicates the table from which to retrieve data.
- **WHERE**: Filters records based on specified conditions.
- **COUNT**: Returns the number of rows that match a specified condition.
- **ORDER BY**: Sorts the result set by one or more columns.
- **GROUP BY**: Groups rows that have the same values in specified columns.
- **UNION**: Combines the result sets of two or more SELECT statements.
- **JOIN**: Combines rows from two or more tables based on a related column.
- **LIMIT**: Specifies the maximum number of records to return.
- **CASE-WHEN**: Provides conditional logic to return specific values based on conditions.
- **RANK**: Assigns a rank to each row within the partition of a result set.
- **COALESCE**: Returns the first non-null value in a list.
- **CTEs (Common Table Expressions)**: Provides a way to create temporary result sets that can be referenced within a SELECT, INSERT, UPDATE, or DELETE statement.

## Installation

### PostgreSQL

1. **Download the dataset:**
    - `olympics-postgresql.sql`

2. **Transfer the file to iLab machine:**
    - Use `scp` to copy `olympics-postgresql.sql` to your iLab machine. 
      ```bash
      scp olympics-postgresql.sql [YOUR_USERNAME]@ilab.redacted.edu:[YOUR_TARGET_DIRECTORY]
      ```

3. **SSH to the iLab machine:**
    - Connect to the iLab machine using `ssh`. 
      ```bash
      ssh [YOUR_USERNAME]@ilab.redacted.edu
      ```

4. **Importing data into PostgreSQL:**
    - Connect to the PostgreSQL database and import the data. 
      ```bash
      psql -h postgres.redacted.edu -f olympics-postgresql.sql
      ```

5. **Log in to PostgreSQL command line:**
    - Use `psql` to log in. 
      ```bash
      psql -h postgres.redacted.edu
      ```

6. **Check if data is imported correctly:**
    - Use the following command to check the imported data. 
      ```sql
      \dt
      ```
    - The output should say `List of relations` at the top and have `athletes`, `coaches`, `countries`, `gender`, `medal_info`, `medals`, `results`, `teams`, `tokyo_medals`, and `venues` under the `Name` column.

7. **Verify data:**
    - Use the following query to verify the number of rows in the `athletes` table. 
      ```sql
      SELECT COUNT(*) FROM athletes;
      ```
    - The result should return a count of `11110`.

## Olympics-PostgreSQL

A SQL file that creates the initial tables to hold aggregate data that we could use to create our own queries and tables. Data is related to countries and people who participated in the Paris Olympics. It creates tables with these names: `athletes`, `coaches`, `countries`, `gender`, `medal_info`, `medals`, `results`, `teams`, `tokyo_medals`, `venues`.

## Olympics-PostgreSQL

This SQL file creates the initial tables to hold aggregate data that can be used to generate queries and additional tables. The data pertains to countries and individuals who participated in the Paris Olympics. It creates the following tables: `athletes`, `coaches`, `countries`, `gender`, `medal_info`, `medals`, `results`, `teams`, `tokyo_medals`, and `venues`.

## OlympicData

Each query creates specific tables based on the stated columns.

### Part 1

1. **Q1:** Find athletes who play Table Tennis for China. Columns: `code`, `name`, `country_code`, and `birth_date`.
2. **Q2:** Find the 20 youngest athletes. Columns: `athlete_ID`, `athlete_name`, `country_code`, and `birth_date`.
3. **Q3:** List countries with more gold than silver medals in the 2020 Tokyo Olympics. Columns: `country_code`, `gold_medal`, and `silver_medal`.
4. **Q4:** Find USA athletes who won gold medals in individual events. Columns: `name`, `country_code`, `medal_code`, and `event`.
5. **Q5:** List USA teams that won gold medals in team events. Columns: `team_code (code)`, `country_code`, `medal_code`, and `event`.
6. **Q6:** Display the amount of gold, silver, and bronze medals won by the USA in individual events. Columns: `country_code`, `gold_medal`, `silver_medal`, and `bronze_medal`.
7. **Q7:** List the top 10 countries ordered by the number of gold, silver, and bronze medals. Columns: `country_code`, `gold_medal`, `silver_medal`, and `bronze_medal`.
8. **Q8:** Find athletes who have won at least 3 medals in Swimming and the total number of medals they won. Columns: `athlete_name`, `country_code`, and `total_medals`.
9. **Q9:** Calculate the percentage of athletes who participate in multiple shooting events compared to all athletes participating in individual shooting events. Column: `percentage`.
10. **Q10:** List the top 10 countries by total GDP. Columns: `country_code`, `total_gdp`, and `gdp_rank`.

### Part 2

1. **Q1:** Find athletes who play Table Tennis. Columns: `participant_code`, `event_name`, `result`, and `win_count` (1 if win, 0 if loss).
2. **Q2:** Using the results from Q1, calculate the total number of wins for each participant in Table Tennis events. Columns: `participant_code`, `event_name`, and `total_wins`.
3. **Q3:** Rank participants based on the total number of wins from Q2. Columns: `participant_code`, `event_name`, `total_wins`, and `rank_position`.
4. **Q4:** Count the number of times a country has placed in the top 4 in Table Tennis, using the results from Q3. Columns: `country_code` and `top_four_count`.
5. **Q5:** Track the appearances of athletes or teams that finished in the top five on each date. Columns: `date`, `country_code`, and `appearances`.
6. **Q6:** Rank countries based on the number of top-five placements on each date, using the results from Q5. Columns: `date`, `country_code`, `appearances`, and `rank_position`.
7. **Q7:** Identify the highest number of top-five finishes for each event date, using the results from Q6. Columns: `date`, `country_code`, and `appearances`.
8. **Q8:** List the population and GDP per capita rankings for each country. Columns: `country_code`, `population_rank`, and `gdp_rank`.
9. **Q9:** Using the results from Q7 and Q8, find the country with the highest number of top-five finishes each day and their population and GDP per capita rankings. 

## Contributors
Rutgers Computer Science Department

## License
GNU GENERAL PUBLIC LICENSE
Version 3, 29 June 2007

## Contact
vishalsaran2021@gmail.com
