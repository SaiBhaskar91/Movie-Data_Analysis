IMDB Movies Data Analytics Project Project Description
This project analyzes and extracts insights from an IMDB Movies dataset, covering attributes such as ratings, genre, budget, gross income, director, and actors. The goal is to answer key questions about the factors driving movie success, profitability, and ratings distribution.
--- Objectives
Clean and preprocess the raw movie dataset
Identify trends such as:
Highest-grossing films
Top 250 movies by rating
Top directors
Popular genres
Explore financial, creative, and star-related factors influencing movie success
Present findings through visualizations and a summary report
---
🛠️ Tools & Technologies
Category	Tools Used
Data Cleaning & Analysis	Python (Pandas, NumPy)
Data Visualization	Matplotlib, Seaborn
Database	MySQL
Environment	Google Colab / Jupyter Notebook
--- Project Type
Data Analytics / Visualization
Duration: Week 2 – Week 3 (Training Project)
---
Project Workflow
1. Data Cleaning
Checked for missing values using `isnull().sum()`
Calculated missing percentage per column
Applied cleaning rules:
< 40% missing (numerical) → filled using `median()`
< 40% missing (categorical) → filled using `mode()`
> 60–70% missing → column dropped entirely
Checked and removed duplicate records using `drop_duplicates()`
Verified data types using `dtypes` and `info()`
2. Trend Analysis
Highest-Grossing Films — sorted by `Revenue (Millions)` descending
Top 250 Movies by Rating — sorted by `Rating`, filtered by minimum vote threshold for reliability
Top Directors — grouped by `Director`, filtered by minimum movie count to avoid misleading single-movie averages
Popular Genres — `Genre` column split and exploded (since it contained multiple comma-separated values per cell) before counting
3. Correlation Analysis
Explored relationships between `Rating` and other numerical factors:
Factor	Correlation with Rating	Strength
Metascore	0.60	Strong positive
Votes	0.51	Moderate positive
Runtime (Minutes)	0.39	Moderate positive
Revenue (Millions)	0.22	Weak positive
Year	-0.21	Weak negative
Rank	-0.22	Weak negative
Key Insight: Critical quality (Metascore) has a stronger relationship with audience Rating than commercial performance (Revenue) — box office success does not necessarily indicate a critically well-rated film. Data Visualization
Built the following charts using Matplotlib/Seaborn:
Bar chart — Top 10 highest-grossing movies
Histogram — Rating distribution across all movies
Scatter plot — Votes vs Rating (visualizing the 0.51 correlation)
Line chart — Year-wise average rating trend
Bar chart — Top 10 popular genres
 MySQL Integration
Exported the cleaned dataset into a MySQL database table using `to_sql()`
Ran SQL queries to validate and cross-check pandas-based findings (top grossing films, top directors, etc.)
--- Key Findings
Critic scores (Metascore) align closely with audience ratings, suggesting general agreement between critics and viewers
Commercial success (Revenue) is only weakly related to movie quality/rating
A small number of genres and directors dominate the highest-rated and highest-grossing categories
Ratings are largely concentrated in a moderate range, with very few extremely low or extremely high-rated films
---
Recommendations for Stakeholders
Filmmakers/Producers: Prioritize script and direction quality (correlates more strongly with rating) over pure box-office-driven decisions to build long-term critical reputation
Studios: Use director and genre performance trends to guide investment decisions, but validate with minimum sample size (avoid over-indexing on directors with very few films)
Marketing Teams: High vote count correlates with higher ratings — early audience engagement strategies may support stronger long-term reception
---
Project Structure
```
├── movies_raw.csv              # Original dataset
├── movies_cleaned.csv          # Cleaned dataset after preprocessing
├── data_cleaning.ipynb         # Cleaning & preprocessing notebook
├── trend_analysis.ipynb        # Trend & correlation analysis
├── visualizations/             # Saved chart images (.png)
├── mysql_queries.sql           # SQL queries used for validation
└── README.md                   # Project documentation (this file)
```
---
 How to Run
Load the raw dataset: `df = pd.read_csv("movies_raw.csv")`
Run the cleaning steps (missing values, duplicates, dtype checks)
Run trend analysis and correlation analysis cells
Generate visualizations
Export cleaned data to MySQL for query validation
