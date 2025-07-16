# SportsProject


Premier League Team Analysis & Scouting Project:

In this project we can find 9 datasets and 8 notebooks that analyze Premier League players and teams from different perspectives. The datasets include statistics on player performance, possession, salaries, team stats and fixtures. The objective of this project is to explore different techniques to cluster player roles, compare players in terms of performance and salary, and assist scouting processes by identifying younger or cheaper players with similar performance.

## Datasets

All data is stored in the `data` folder. The main datasets used are:

- `player_stats.csv`: General statistics per player (minutes, goals, assists, etc.).
- `player_salaries.csv`: Annual salaries for each player.
- `player_possession_stats.csv`: Possession-related statistics per player (touches by zone, progressive passes, etc.).
- `team_stats.csv`: General stats per team.
- `team_possession_stats.csv`: Team-level possession distribution and progression.
- `standings.csv`: Current league standings.
- `fixtures.csv`: Match calendar and results.
- `team_salary.csv`: Aggregated team salary data.
- `player_salaries_with_expected.csv`: Salaries with a new column containing predicted salary from ML models.

## Notebooks

The following Jupyter notebooks are part of the project:

### `team_analysis.ipynb`
This notebook analyzes team-level metrics like possession, expected goals (xG), and performance relative to team salaries. It allows comparing teams based on how they play and how efficiently they perform in relation to their payroll.

### `interesting_graphics.ipynb`
Generates visual visualizations of player behavior and zone-based touches. One of the main plots is a stacked horizontal bar chart showing the percentage of touches in defensive, middle and attacking thirds per player.

### `cluster_features_toghether.ipynb`
Clusters all players using multiple statistical dimensions combined. After normalization, dimensionality reduction and KMeans clustering are applied to identify distinct player profiles.

### `cluster_individual_features.ipynb`
Clusters players using individual groups of statistics (e.g., passing stats only, or attacking stats only). This helps explore how players group based on specific skillsets.

### `player_type.ipynb`
Uses the clustering results to assign players to predefined profiles or types. This is useful to classify players and understand their tactical role within the team.

### `salary_performance.ipynb`
Builds machine learning models to predict a player's expected salary based on their statistics. The idea is to detect overpaid and underpaid players. The models used include:
- Random Forest Regressor
- XGBoost Regressor
- CatBoost Regressor

The best performing model is used to add a column to the dataset with predicted salary. The difference between actual and predicted salary is used to identify market inefficiencies.

### `player2Buy.ipynb`
Implements a recommendation system to find similar players to those in a specific team, with the condition that the alternative players are either younger or have a significantly lower salary. The algorithm uses K-Nearest Neighbors (KNN) on normalized stats and filters candidates based on minutes played, position, age and salary constraints. Another approach uses the predicted salary instead of actual salary to find undervalued players.

### `data_preparation.ipynb` *(assumed or implied)*
Handles column cleaning, merging and preprocessing of the datasets. All data manipulation steps prior to modeling and clustering are done here.

## Objective

The objective of this project is to explore different techniques for:
- Clustering player profiles based on multiple stat categories
- Comparing players with similar profiles but different cost (age or salary)
- Predicting salary from performance to detect overpaid or undervalued players
- Understanding team-level styles and efficiency using stats and visualizations

## Tools and Libraries

The project is implemented using Python and the following libraries:
- Pandas and NumPy for data manipulation
- Matplotlib and Seaborn for visualization
- Scikit-learn for clustering, normalization and regression
- XGBoost and CatBoost for boosted regression models

## How to Use

1. All datasets are already available in the `data` folder. No external downloads are required.
2. You can start by opening `team_analysis.ipynb` or `player2Buy.ipynb` for high-level analyses.
3. Use the `cluster_*` and `salary_performance.ipynb` notebooks to explore player profiling and market inefficiencies.
4. The notebooks are independent but share a common `df_dict` structure to load datasets.