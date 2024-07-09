# Football Player Data Analysis

## Project Overview

This project focuses on the analysis of football player data, including cleaning the dataset, categorizing players based on age, and performing various data analysis and visualization tasks. The dataset contains information about players such as their age, height, position, club, and dominant foot.

## Dataset

The dataset `Player Football.csv` contains the following columns:
- `name`: Name of the player.
- `age`: Age of the player.
- `height`: Height of the player in centimeters.
- `position`: Playing position of the player.
- `club`: Club for which the player plays.
- `foot`: Dominant foot of the player (Left/Right).
- Additional columns: The dataset originally included columns for nationality and image, which were dropped during data cleaning.

## Objectives

1. **Data Cleaning**: Handle missing values, remove unnecessary columns, and categorize players based on age.
2. **Data Analysis and Visualization**: Perform various analyses and visualizations to gain insights into the dataset.

## Data Cleaning Steps

1. **Drop Unnecessary Columns**: Removed the `nationality` and `image` columns.
2. **Categorize Age**: Added a new column `age_category` based on the player's age:
   - `Young` for age < 25
   - `Prime` for age between 25 and 29
   - `Experienced` for age between 30 and 34
   - `Veteran` for age >= 35

## Data Analysis and Visualization

1. **Player Position Distribution**:
   - Visualized the distribution of players across different positions using a bar chart.
2. **Average Player Height by Position**:
   - Calculated and visualized the average height of players by their playing position.
3. **Age Distribution of Players**:
   - Created a histogram to show the distribution of player ages.
4. **Number of Players by Club**:
   - Visualized the total number of players in each club using a bar chart.
   - Highlighted the top 10 clubs with the most players.
5. **Distribution of Players' Dominant Foot**:
   - Visualized the distribution of players' dominant foot (Left/Right) using a pie chart.
6. **Relationship Between Player Height and Age**:
   - Created a scatter plot to show the relationship between player height and age, with different colors for different positions.
7. **Club with the Tallest Average Players' Height**:
   - Identified and visualized the club with the tallest average player height.
8. **Young Midfielders**:
   - Displayed all players who play in the 'Midfielder' position and are under 25 years old.
9. **Tall or Left-Footed Players**:
   - Displayed all players who are over 180 cm tall or whose dominant foot is 'Left'.
10. **Specific Club and Position Analysis**:
    - Displayed all players who play in 'Real Madrid' and whose position is 'Defender'.
    - Displayed all players who are over 25 years old and whose dominant foot is 'Right'.
    - Displayed all players who are between 170 cm and 180 cm (inclusive) and play in 'Manchester United'.

## Files

- `Player Football.csv`: Original dataset.
- `Player Fix.csv`: Cleaned and processed dataset.
- `README.md`: This README file.
- `About.md`: Detailed information about the project (if needed).

## How to Use

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/football-player-data-analysis.git
