
# Movie-Industry-Correlation-Analysis (1986–2016)  
Exploratory Data Analysis on Commercial and Critical Success Factors

---

## Project Overview

This case study explores trends and correlations in a dataset of **6,820 movies** released between **1986 and 2016**. The primary objective is to uncover **patterns and relationships** that explain what makes a movie successful — both commercially (box office) and critically (ratings, votes).

The dataset includes both **numerical** and **categorical** variables such as:

- Budget  
- Gross Revenue  
- IMDb Ratings  
- User Votes  
- Genre  
- Director, Writer, and Lead Actor/Actress  

Through visualizations and correlation analysis, the project answers key business and analytical questions that can assist production companies, marketers, and investors in making data-driven decisions.

---

## Questions Explored

- 📈 Does a higher budget correlate with higher revenue?
- 🍿 Is there a relationship between IMDb scores and box office performance?
- 🔍 Which features have the strongest correlations with movie success?
- 🌍 Do production companies or countries significantly influence outcomes?

---

## Tools & Technologies

- **Pandas**, **NumPy** – for data handling and transformation  
- **Matplotlib**, **Seaborn** – for visual analytics and plots  
- **Jupyter Notebook** – for code organization and reporting  

---

## Dataset Structure

| Column       | Description                         |
|--------------|-------------------------------------|
| `name`       | Name of the movie                   |
| `budget`     | Budget of the movie (0 if unknown)  |
| `gross`      | Gross revenue earned                |
| `company`    | Production company                  |
| `country`    | Country of origin                   |
| `director`   | Movie director                      |
| `writer`     | Writer of the script                |
| `star`       | Lead actor or actress               |
| `genre`      | Main genre of the movie             |
| `rating`     | Content rating (e.g., R, PG)        |
| `score`      | IMDb user rating                    |
| `votes`      | Number of user votes                |
| `released`   | Release date (YYYY-MM-DD)           |
| `runtime`    | Duration in minutes                 |
| `year`       | Year of release                     |

---

## Objective

The goal is to **calculate correlation coefficients** and **visualize relationships** between variables to:

- Identify strong predictors of commercial success  
- Detect key features that influence critical reception  
- Provide strategic insights into movie production and distribution  

---

### ✅ Data Quality Steps Performed:
- **Import data**:
          import os
          import json

          # Ensure the file variable points to the correct kaggle.json file
          # Ensure the file variable points to the correct kaggle.json file
          kaggle_json_path = r'C:\Users\bashi\Downloads\kaggle (1).json'  # Update this path if needed

           # Make .kaggle directory and move the file there
           os.makedirs(os.path.expanduser('~/.kaggle'), exist_ok=True)
           os.system(f'cp "{kaggle_json_path}" ~/.kaggle/')
           os.system('chmod 600 ~/.kaggle/kaggle.json')


           import kagglehub

           # Download latest version
           path = kagglehub.dataset_download("danielgrijalvas/movies")

           print("Path to dataset files:", path)

           # Importing necessary libraries
           import pandas as pd
           import numpy as np
           import matplotlib.pyplot as plt
           import seaborn as sns

            # Construct the full path to the CSV file
            csv_file_path = os.path.join(path, "movies.csv")

             # Load the CSV file into a pandas DataFrame
             movies = pd.read_csv(csv_file_path)
- **Header Correction**: Ensured proper column names were assigned during data import.
             # Check the columns of the DataFrame
             print("Columns in the DataFrame:")
             print(movies.columns)

             Output:
             Columns in the DataFrame:
             Index(['name', 'rating', 'genre', 'year', 'released', 'score', 'votes',
                    'director', 'writer', 'star', 'country', 'budget', 'gross', 'company',
                    'runtime'],
                   dtype='object')

             They had already proper column names
  
- **Data Types**: Verified all columns had the correct data types (e.g., numeric, datetime, categorical).

                # Display data types of the columns
                print("\nData types of the columns:")
                print(movies.dtypes)
- **Missing Values**: Checked for and flagged missing or null entries for critical fields like `budget`, `gross`, and `score`.
- **Duplicate Records**: Confirmed that there were no duplicated movie entries in the dataset.
- **Initial Summary**: Generated basic statistical summaries to identify any data distribution issues or outliers.

These validation steps helped ensure that the data was reliable for meaningful visualizations and correlation analysis.

---

