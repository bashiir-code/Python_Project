
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

                  Data types of the columns:
                  name         object
                  rating       object
                  genre        object
                  year          int64
                  released     object
                  score       float64
                  votes       float64
                  director     object
                  writer       object
                  star         object
                  country      object
                  budget      float64
                  gross       float64
                  company      object
                  runtime     float64
                  dtype: object

released should be changed to datetime:
                 #example (June 13, 1980 (United States))  should be  yyyy-mm-dd
            
                 movies['released'] = movies['released'].str.extract(r'([A-Za-z]+\s\d{1,2},\s\d{4})')
                 movies['released'] = pd.to_datetime(movies['released'], errors='coerce')

- **Missing Values**: Checked for and flagged missing or null entries for critical fields like `budget`, `gross`, and `score`.

                 # see the columns of the DataFrame and how many not null values are in each column 
                 movies.info()

                 | #  | Column   | Non-Null Count | Dtype   |
                 | -- | -------- | -------------- | ------- |
                 | 0  | name     | 7668           | object  |
                 | 1  | rating   | 7591           | object  |
                 | 2  | genre    | 7668           | object  |
                 | 3  | year     | 7668           | int64   |
                 | 4  | released | 7666           | object  |
                 | 5  | score    | 7665           | float64 |
                 | 6  | votes    | 7665           | float64 |
                 | 7  | director | 7668           | object  |
                 | 8  | writer   | 7665           | object  |
                 | 9  | star     | 7667           | object  |
                 | 10 | country  | 7665           | object  |
                 | 11 | budget   | 5497           | float64 |
                 | 12 | gross    | 7479           | float64 |
                 | 13 | company  | 7651           | object  |
                 | 14 | runtime  | 7664           | float64 |

                 We can see that  budget has a lot missing values. gross is the second one that has least not null values.

                  # Check for missing values
                  missing_values = movies.isnull().sum()
                  missing_values = missing_values[missing_values > 0]
                  print(missing_values)

                  | Column   | Missing Values |
                  | -------- | -------------- |
                  | rating   | 77             |
                  | released | 2              |
                  | score    | 3              |
                  | votes    | 3              |
                  | writer   | 3              |
                  | star     | 1              |
                  | country  | 3              |
                  | budget   | 2,171          |
                  | gross    | 189            |
                  | company  | 17             |
                  | runtime  | 4              |

                  # Fill missing values in the 'rating' column with the mode of the column
                  movies.rating.fillna(movies["rating"].mode()[0], inplace = True)

                  # Remove missing values in the 'released' column by dropping rows with NaN values            movies = movies.dropna(subset = ['released'])
  

                   # Fill missing values in the 'score', 'votes', 'runtime', 'budget' and 
                    'gross' columns with the median of the column
                    for col in ['score', 'votes', 'runtime', 'budget', 'gross']:
                         movies[col].fillna(movies[col].median(), inplace=True)

                   # Fill missing values in the 'writer' , 'star', 'company' and 'country' columns with the Unknown string
                    for col in ['writer', 'star', 'company', 'country']:
                           movies[col].fillna('Unknown', inplace = True)

                     
                     # Check if there are any missing values left in the dataset
                     missing_values = movies.isnull().sum()
                     missing_values = missing_values[missing_values > 0]
                     print(missing_values)

- **Duplicate Records**: Confirmed that there were no duplicated movie entries in the dataset.
  
                      # Check duplicate rows in the DataFrame
                       duplicate_rows = movies.duplicated().sum()
                       print(f"Number of duplicate rows: {duplicate_rows}")
  
                       Output:
                        Number of duplicate rows: 0
- **Wrong Data**
               
                      # Check if there any mismatches between the 'year' and 'released' columns

                       z = 0
                       for (x, y) in zip(movies['year'], movies['released']):
                            if x != y.year:
                                     z
                       print(z)

                       Output : 1297   that is huge number of missmatch data

                       # correct the 'year' column based on the 'released' column
                       for (x, y) in zip(movies['year'], movies['released']):
                          if x != y.year:
                              x = y.year
                            

  
- **Initial Summary**: Generated basic statistical summaries to identify any data distribution issues or outliers.


                      #initial summary of the categorical columns
                      movies.describe(include = 'object').T.sort_values(by = 'unique', ascending = False)

 | Column   | Non-Null Count | Unique Values | Most Frequent (Top) |Frequency (Freq) |
| -------- | -------------- | ------------- | ------------------- | ---------------- |
| name     | 7,609          | 7,454         | *Nobody's Fool*     | 3                |
| rating   | 7,609          | 12            | R                   | 3,739            |
| genre    | 7,609          | 19            | Comedy              | 2,228            |
| director | 7,609          | 2,935         | Woody Allen         | 38               |
| writer   | 7,609          | 4,513         | Woody Allen         | 37               |
| star     | 7,609          | 2,785         | Nicolas Cage        | 43               |
| country  | 7,609          | 60            | United States       | 5,453            |
| company  | 7,609          | 2,360         | Universal Pictures  | 377              |



                   # Exclude non-numerical columns before describing and sorting
                   movies.describe(include=[np.number]).T.sort_values(by='mean', ascending=False)

| Column      | Count | Mean       | Std Dev     | Min   | 25%        | 50%        | 75%        | Max           |
| ----------- | ----- | ---------- | ----------- | ----- | ---------- | ---------- | ---------- | ------------- |
| **gross**   | 7609  | 77,632,640 | 164,424,900 | 309   | 4,889,971  | 20,420,288 | 73,906,736 | 2,847,246,000 |
| **budget**  | 7609  | 31,574,220 | 35,818,230  | 3,000 | 14,000,000 | 21,000,000 | 32,000,000 | 356,000,000   |
| **votes**   | 7609  | 88,697     | 163,770     | 7     | 9,300      | 33,000     | 94,000     | 2,400,000     |
| **year**    | 7609  | 2000.5     | 11.14       | 1980  | 1991       | 2001       | 2010       | 2020          |
| **runtime** | 7609  | 107.3 min  | 18.62       | 55    | 95         | 104        | 116        | 366           |
| **score**   | 7609  | 6.39       | 0.97        | 1.9   | 5.8        | 6.5        | 7.1        | 9.3           |


These validation steps helped ensure that the data was reliable for meaningful visualizations and correlation analysis.

---


**Correlation Search**


    Let's examine whether there is a correlation between how much is invested in a film and the revenue it generates.

           # Plotting scatter plot for budget vs gross earnings
           plt.scatter(x=movies['budget'], y=movies['gross'], alpha= 0.5)
           plt.title('Budget vs Gross Earnings')
           plt.xlabel('Budget for Film')
           plt.ylabel('Gross Earnings of Film')
           plt.show()


           Output:
           ![image](https://github.com/user-attachments/assets/5827aff5-e852-4a80-b3df-bb843421345c)

            
             
TODO:
-----
