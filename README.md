
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
