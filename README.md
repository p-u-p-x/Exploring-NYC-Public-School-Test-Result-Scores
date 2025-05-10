# Exploring-NYC-Public-School-Test-Result-Scores

## Table of Contents
 
 - [Project Overview](#project-overview)
 - [Data Source](#data-source)
 - [Tools](#tools)
 - [Data Cleaning](#data-cleaning)
 - [Data Analysis](#data-analysis)
 - [Exploratory Data Analysis](#exploratory-data-analysis)
 - [Results and Findings](#results-and-findings)
 - [Recommendations](#recommendations)
 - [Limitations](#limitations)
 - [References](#references)

## Project Overview

This project examines SAT performance across New York City public schools using the schools.csv dataset. The analysis explores key trends in reading, math, and writing scores, offering insights valuable to educators, policymakers, researchers, and parents. Through data-driven exploration, the project aims to highlight school performance patterns that can inform decision-making in education.

## Data Source

The dataset used in this project, schools.csv, contains SAT performance data for NYC public schools.The dataset includes scores for reading, math, and writing, helping analyze trends in school performance.

## Tools

This project utilizes Python for Exploratory Data Analysis (EDA), leveraging the following libraries:
- pandas – Data manipulation and preprocessing
- numpy – Numerical operations
- matplotlib & seaborn – Data visualization
- scikit-learn – Statistical analysis and preprocessing
- Jupyter Notebook – Interactive code execution

## Data Cleaning
- Handling missing values – Identified and imputed/nullified missing SAT scores.
- Data type corrections – Converted numerical columns to appropriate formats.
- Duplicate removal – Eliminated redundant entries for consistency.
- Feature engineering – Created new meaningful variables where necessary.
- Outlier detection – Addressed anomalies in SAT score distributions.
- Standardization – Ensured uniform formatting for categorical and numerical data.

## Data Analysis 

## Exploratory Data Analysis
- Which NYC schools have the best math results?
- What are the top 10 performing schools based on the combined SAT scores?
- Which single borough has the largest standard deviation in the combined SAT score?


1. Finding schools with the best math scores.
   Subset the data to find the schools with math scores of at least 80%,       considering the maximum possible score is 800 and save this as a pandas     DataFrame called best_math_schools.

```python
best_math_schools = schools[schools["average_math"] >= 640][["school_name", "average_math"]].sort_values("average_math", ascending=False)
```
2. Identifying the top 10 performing schools.
   Find the 10 best performing schools based on the total score across the     three SAT sections.
 
 - Creating a column for average scores.
```python
schools["total_SAT"] = schools["average_math"] + schools["average_reading"] + schools["average_writing"]
```
 - Sorting and limiting the data
```python
top_10_schools = schools.sort_values("total_SAT", ascending=False)[["school_name", "total_SAT"]].head(10)
```
3. Locating the NYC borough with the largest standard deviation in SAT         performance.
   Find out the number of schools, average SAT, and standard deviation of    SAT for the NYC borough with the largest standard deviation, rounded to    two decimal places.

 - Grouping the data by borough
```python
boroughs = schools.groupby("borough")["total_SAT"].agg(["count", "mean", "std"]).round(2)
```
 - Filtering for the largest standard deviation
```python
largest_std_dev = boroughs[boroughs["std"] == boroughs["std"].max()]
```
 - Renaming columns
```python
largest_std_dev.reset_index(inplace=True)
```

## Results and Findings

## Recommendations

## Limitations

## References 
