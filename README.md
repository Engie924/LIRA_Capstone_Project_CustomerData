# LITA_Capstone_Project_CustomerData
Documentation of my Incubator Hub Capstone Project in Data Analysis on Customer segmentation for a subscription service.

### Project Title: Capstone Project

[Project Overview](#project-overview)

[Objectives](#objectives)

[Data Sources](#data-sources)

[Tools Used](#tools-used)

[Methodology](#methodology)

[Exploratory Data Analysis](#exploratory-data-analysis)

[Data Analysis](#data-analysis)

[Dashboard Visualization](#dashboard-visualization)

### Project Overview
---

This project aims to analyze customer data for a subscription service to identify segments and trends. The goal is to gain insights into customer behavior, track subscription types/patterns, and identify key trends in cancellations and renewals. The final deliverable is to creat a Power BI dashboard that presents these findings in a clear and actionable way.

### Objectives
---
My objectives are to: 
- Understand customer behavior and preferences.
- Identify the most popular subscription types.
- Analyze customer churn and retention rates.
- Track subscription durations and renewal patterns.
- Visualize key insights through an interactive Power BI dashboard.

### Data Sources
---
The primary data source used is the Customer Dataset provided by the Github which contains customers' information such as Customer ID, Customer Name, Region, Subscription Type, Start Date, End Date and so on.

### Tools Used
---
- Microsoft Excel: 
  1. For Data Cleaning
   2. For Analysis
   3. For Data Summary
- SQL - Structured Query Language for Quering Data 
- Power BI - For Data Visualization of insights found in Excel and SQL
- GitHub for Portfolio Building

### Methodology
---

#### Data Cleaning and Preparation

At the initial phase of data cleaning and preparation, i prepared the following actions:
1. Clean and validate the data to ensure accuracy.
2. Handle missing values and outliers.
3. Transform the data into a suitable format for analysis.

#### Excel

- I utilized Excel pivot tables to analyze customer data and identified initial trends.
- I also calculated key metrics such as average subscription duration and popular subscription types.

#### SQL Queries

- Executed SQL queries to answer specific questions and extract deeper insights.
- Used aggregate functions, and filtering techniques to analyze the data.

#### Power BI Dashboard

I imported the cleaned and analyzed data into Power BI and created visualizations to represent key findings on:
- Customer segmentation by region and subscription type
- Subscription duration distribution
- Churn rate over time
- Top-performing and underperforming regions
- Revenue trends by subscription type
- Interactive slicers to enable dynamic analysis


### Exploratory Data Analysis
---
EDA involves the exploring of the Data to answer some questions about the data.

**Excel** 

After cleaning the data in Excel, i started the analysis and dashboard creation and the following steps were carried out:

- Analyzing customer data using pivot tables to find subscription patterns by region and subscription type.
- Calculating average subscription duration and identify the most popular types.
- Creating visualizations to explore trends and outliers.



 ### Data Analysis
 ---

 **Insights with SQL**
 
 With my dataset loaded into SQL Server, i crafted queries to pull out critical insights such as:
 
 Retrieving the total number of customers from each region.
 ```SQL
SELECT Region, COUNT(*) AS Total_Customers
FROM[dbo].[LITA CUSTOMER DATA]
GROUP BY Region
```
Finding the most popular subscription type by the number of customers.
```SQL
SELECT top 1 SubscriptionType, COUNT(*) AS Total_Customers
FROM[dbo].[LITA CUSTOMER DATA]
GROUP BY SubscriptionType
ORDER BY Total_Customers DESC
```
Finding customers who canceled their subscription within 6 months.
```SQL
SELECT CustomerName FROM[dbo].[LITA CUSTOMER DATA]
WHERE Canceled = 0
  AND DATEDIFF(day, SubscriptionStart, SubscriptionEnd) <= 180;
```
OR
```SQL
select CustomerName from[dbo].[LITA CUSTOMER DATA]
where Canceled = 1
AND DATEDIFF(MONTH, SubscriptionStart, SubscriptionEnd) <= 6;
```
Calculating the average subscription duration for all customers.
```SQL
SELECT AVG(SubscriptionDuration) AS Average_Subscription_Duration
FROM[dbo].[LITA CUSTOMER DATA];
```
Finding customers with subscriptions longer than 12 months.
```SQL
SELECT CustomerID, CustomerName, SubscriptionStart, SubscriptionEnd
FROM[dbo].[LITA CUSTOMER DATA]
WHERE SubscriptionDuration > 365;
```
Calculating total revenue by subscription type.
```SQL
SELECT SubscriptionType, SUM(Revenue) AS Total_Revenue
FROM[dbo].[LITA CUSTOMER DATA]
GROUP BY SubscriptionType;
```
Finding the top 3 regions by subscription cancellations.
```SQL
SELECT TOP 3 Region, COUNT(*) AS Subscription_Cancellations
FROM[dbo].[LITA CUSTOMER DATA]
WHERE Canceled = 0
GROUP BY Region
ORDER BY Subscription_Cancellations DESC;
```
Finding the total number of active and canceled subscriptions.
```SQL
SELECT
  SUM(CASE WHEN Canceled = 1 THEN 1 ELSE 0 END) AS Active_Subscriptions,
  SUM(CASE WHEN Canceled = 0 THEN 1 ELSE 0 END) AS Canceled_Subscriptions
FROM[dbo].[LITA CUSTOMER DATA];
```

### Dashboard Visualization
---

**Excel Dashboard Overview**

![Customer Data Pivot](https://github.com/user-attachments/assets/48153f54-c382-4235-8ee7-97cc2fea4d3a)

**Power BI Dashboard**

This repository contains the code, data, and visualizations for a customer segmentation project. The goal was to understand customer behavior, identify trends, and create a Power BI dashboard to present the findings. By analyzing customer data using Excel, SQL, and Power BI, i was able to gain valuable insights into subscription patterns, churn rates, and revenue trends. The dashboard provides a comprehensive overview of customer segments, allowing for data-driven decision-making and targeted marketing strategies.



