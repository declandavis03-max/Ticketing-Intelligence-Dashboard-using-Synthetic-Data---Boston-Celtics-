# Ticketing and Intelligence Dashboard for the Boston Celtics
Hi! This project is  multi-page Power BI analytics dashboard using AI-generated ticketing, social media, and fan survey data. Used modeled datasets in MySQL, SQL joins, and DAX measures to analyze relationships between fan engagement, revenue, and game demand. 

## Table of Contents

- [Introduction](#Introduction)
- [Data](#Data)
- [Technical Stack](#technical-stack)
- [Overall Insights](#Overall-Insights)


# Introduction

The goal was to replicate how a professional sports organization might analyze:
- Fan satisfaction (NPS & experience scores)
- Opponent-driven revenue performance
- Social media engagement impact on ticket demand

The project demonstrates end-to-end analytics capabilities using:
- MySQL (Data modeling + SQL queries)
- Power BI (Dashboard development + DAX calculations)
- AI-generated synthetic datasets

End to End Analytics Pipeline:
```
Data Creation --> SQL Database --> SQL Joins and Queries --> Dashboard Deisgn --> Overall Insights
```

On top of the project scope, this was one of my first porjects I have created from the ground up. I have gained insightful knowledge on how to work with datasets, write productive queries to gain information, and work with Power BI to turn those insights into visualizations to properly display information. I am pleasently pleased with this project, and am hopeful to build more projects with much greater detail! Open to any singihts on how to imporve my processes!

# Data 
Used AI generated data from Chat GPT. Prompted CHAT GPT to create four datasets. Datasets are all CSV files and have over 100 rows of data each set:
1) fans.csv
2) social_metrics.csv
3) survey.csv
4) ticket_sales.csv

# Technical Stack

### Step 1: Data Generation
Used AI to generate Synthetic Data of realistic fan datasets
- Fan Data: Name, Age, City, Email, Fan_ID, Season Ticket Holder (Yes or No)
- Social Media Metrics: Date of Post, Engagement Rate, Followers, Posts, Video Views
- Survey Data: Fan_ID, Game Satisfaction, NPS, Parking Satisfaction, Comments
- Ticket Sales Data: Game_ID, Attendence, Date, Opponent, Ticket Sales

### Step 2: SQL Database
- Data Base Creation
  The data sets were created into a MYSQL database: 
  
      -CREATE DATABASE IF NOT EXISTS ticketing_analytics;
      USE ticketing_analytics;

  This ensured all projects were isolated in a structure schema.

  Table Design: Two Tables were created to support ticketing and social analytics:
  ```
  sql
    CREATE TABLE social_metrics (
        date DATE,
        followers INT,
        engagement_rate FLOAT,
        posts INT,
        video_views INT
    );
    
    CREATE TABLE ticket_sales (
        game_id INT PRIMARY KEY,
        date DATE,
        opponent VARCHAR(100),
        attendance INT,
        revenue FLOAT
    ); 


Why this Works?
  - Explicit data types ensure clean modeling.
  - game_id acts as a primary key.
  - Date serves as the relational join key between ticket and social data.
  - This structure mimics how professional sports organizations store event-level data.

### Step 3: Data Ingestion

CSV files were directly imported into MySQL.

```sql
LOAD DATA INFILE '.../social_metrics.csv'
INTO TABLE social_metrics
FIELDS TERMINATED BY ','
ENCLOSED BY '"'
IGNORE 1 ROWS;

LOAD DATA INFILE '.../ticket_sales.csv'
INTO TABLE ticket_sales
FIELDS TERMINATED BY ','
ENCLOSED BY '"'
IGNORE 1 ROWS;
```
What this Shows:
- Basic ETL (Extract, Transform,Load)
- Structured data ingestion
- Preparing analysis-ready relational tables

### Step 4: SQL Joins and Queries
To analyze the relationship between digital engagement and ticket performance, a relational join was performed:
  ```sql
  SELECT
      t.date,
      t.opponent,
      t.attendance,
      t.revenue,
      s.engagement_rate,
      s.video_views,
      s.posts
  FROM ticket_sales t
  JOIN social_metrics s 
      ON t.date = s.date;

```
What this Join Achieves: 
- Aligns game-day revenue with social engagement metrics
- Enables direct correlation analysis
- Produces a unified dataset for Power BI modeling
- Reduces transformation complexity inside the BI layer

# Dashbboards Built

# Overall Insights 




