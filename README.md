# Netflix-Data-Visualization
This project analyses Netflix shows and movies through a modular pipeline. Each step of the pipeline such as data preparation, data cleaning, data exploration, and data visualization is handled in separate Jupyter Notebooks. The entire workflow has been automated using Papermill to execute these notebooks sequentially.

# Requirements
- Python 3.x
- R with ggplot2 package

# Project Structure
The pipeline consists of the following files:

### Main_Netflix.ipynb: The master notebook that automates the pipeline using Papermill.
### 01_data_preparation.ipynb: Handles data extraction and initial loading of the Netflix dataset.
### 02_data_cleaning.ipynb: Cleans and preprocesses the data by handling missing values.
### 03_data_exploration.ipynb: Explores the data through descriptive statistics and insights.
### 04_data_visualization.ipynb: Visualizes key insights using plots and charts.
### Netflix_Data_Visualization2.R: Generates a visualization using R.
### Netflix_data: The zipped dataset.
### README.md: Project documentation.

# Dependencies
Make sure you have the following libraries installed:
### import os
### import zipfile
### import pandas as pd
### import matplotlib.pyplot as plt
### import seaborn as sns
### import papermill as pm


# Pipeline Workflow
## 1. Main Pipeline Execution (Main_Netflix.ipynb)
The master notebook executes the pipeline by running each step in sequence. The following Papermill code runs each notebook and captures output:

## 2. Individual Notebook Details
   
### 01_data_preparation.ipynb
#### Input: Netflix_shows_movies.csv
#### Output: output_data_preparation.csv
Tasks:
Unzips and renames the dataset.
Loads the dataset into a DataFrame.
Handles file errors and displays the first five rows of data.

### 02_data_cleaning.ipynb
#### Input: output_data_preparation.csv
#### Output: output_data_cleaning.csv
Tasks:
Checks for missing values and handles them by replacing with "Unknown."
Verifies the cleaning process and saves the cleaned data.

### 03_data_exploration.ipynb
#### Input: output_data_cleaning.csv
#### Output: output_data_exploration.csv
Tasks:
Explore key columns like:
Type: Distribution of TV shows and movies.
Genres: Frequency of the most watched genres.
Rating: Distribution of content ratings.
Release Year: Content release trends over the years.
Country: Top countries producing Netflix content.

### 04_data_visualization.ipynb
#### Input: output_data_exploration.csv
#### Output: Visual plots (saved as PNG files).
Tasks:
Creates bar charts, pie charts, and frequency plots for genre, ratings, and release years.
Saves each plot as a high-resolution image for presentation.
Visualizations created using Python libraries such as Matplotlib, Seaborn, and Pyplot:

Most Watched Genres: A bar chart showing the frequency of popular genres.
Rating Distribution: A bar chart displaying the counts of each rating category.
Content Type Distribution: A pie chart showing proportions of TV shows vs. movies.
Top Release Years: A bar chart highlighting the top years in terms of content production.

# R Integration
One of the visualizations (e.g., Most Watched Genres on Netflix) is replicated in R for practice with cross-tool integration.

# ERRORS
'The NameError: name 'df' is not defined' error can occurs when running modular notebooks that depend on each other but don't pass data between them directly.

NameError: name 'df' is not defined

## Pass Data between Notebooks Using Parameters (Papermill)
Papermill will allow the passage of variables (like a DataFrame's file path) to each notebook as parameters.
Each modular notebook include a cell at the top for parameters to Pass Data between Notebooks e.g.

input_file = "Netflix_shows_movies.csv"
output_file = "output_data_preparation.csv"

## How to Manually Tag Cells in Jupyter Notebook
Open any of the modular notebooks (01_data_preparation.ipynb, 02_data_cleaning.ipynb, etc.).
Right-click on the first cell and choose Add Tag. Assign a tag to the cell, such as parameters, to indicate input parameters for Papermill.
or
Click on Edit, Edit Notebook Metadata and add the  "parameters" tag to the "tags" array. 

{
    "tags": ["parameters"]
}


# Advantages of a Modular Pipeline
Modularity: Each stage of data processing is isolated, making it easier to debug and update.
Reusability: Individual notebooks can be reused across different projects.
Version Control: Changes in each notebook are easier to track.
Parallel Execution: If only one step needs updating, you can run that notebook without re-running the entire pipeline.

# Running the Pipeline
Manual Execution: Run each notebook step-by-step using Jupyter Notebook.
Automated Execution: Use the Main_Netflix.ipynb notebook to automate the pipeline using Papermill.
Outputs
Cleaned Data: output_data_cleaning.csv
Exploratory Data: output_data_exploration.csv
Visualizations: PNG files saved in the working directory.

# Output files -  
Each step will generate a corresponding output notebook which contains both the executed code and outputs
### output_data_cleaning.ipynb
### output_data_exploration.ipynb
### output_data_preparation.ipynb
### output_data_visualization.ipynb

##
### Most Watched Genres on Netflix
### Distribution of Content Type
### Distribution of Ratings on Netflix
### Top 10 Countries Producing Netflix Content
### Top 20 Release Years by Number of Titles


# Error Handling:
The scripts include checks for missing files, empty datasets, and missing columns. If any error is encountered, a descriptive message is printed.

