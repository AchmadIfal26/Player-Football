
### analysis.py

```python
# Import Libraries
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Import Dataset
player = pd.read_csv('Player Football.csv')

# Check whether the data is correct or not
print(player.info())
print(player.isna().sum())

# Drop unnecessary columns
player = player.drop(['nationality', 'image'], axis=1)

# Define function to categorize age
def categorize_age(age):
    if age < 25:
        return "Young"
    elif 25 <= age < 30:
        return "Prime"
    elif 30 <= age < 35:
        return "Experienced"
    else:
        return "Veteran"

# Add age category column
player['age_category'] = player['age'].apply(categorize_age)

# Data Analysis

# 1. Player Position Distribution
sns.set(style="whitegrid")
plt.figure(figsize=(12, 8))
position_counts = player['position'].value_counts(ascending=True)
ax = position_counts.plot(kind='bar', color='skyblue', edgecolor='black')
plt.title('Distribution of Total Players', fontsize=14)
plt.xlabel('Position', fontsize=12)
plt.ylabel('Total Players', fontsize=12)
plt.xticks(rotation=45, ha='right')
plt.grid(axis='y', linestyle='--', alpha=0.7)
for p in ax.patches:
    ax.annotate(f'{p.get_height()}', (p.get_x() + p.get_width() / 2., p.get_height()),
                ha='center', va='center', xytext=(0, 10), textcoords='offset points')
plt.tight_layout()
plt.show()

# 2. Average Player Height by Position
average_height = player.groupby('position')['height'].mean().sort_values()
sns.set(style="whitegrid")
plt.figure(figsize=(10, 8))
ax = average_height.plot(kind='barh', color='lightgreen', edgecolor='black')
plt.title('Average Height by Position', fontsize=14)
plt.xlabel('Average Height (cm)', fontsize=12)
plt.ylabel('Position', fontsize=12)
plt.grid(axis='x', linestyle='--', alpha=0.7)
for p in ax.patches:
    ax.annotate(f'{p.get_width():.2f}', (p.get_width(), p.get_y() + p.get_height() / 2.),
                ha='left', va='center', xytext=(10, 0), textcoords='offset points')
plt.tight_layout()
plt.show()

# 3. Age Distribution of Players
plt.figure(figsize=(10, 8))
player['age'].plot(kind='hist', bins=5)
plt.title("Distribution of Players' Age")
plt.xlabel('Age')
plt.ylabel("Total Players")
plt.show()

# 4. Number of Players by Club
total_club = player['club'].value_counts(ascending=True)
sns.set(style="whitegrid")
plt.figure(figsize=(16, 10))
ax = total_club.plot(kind='bar', color='skyblue', edgecolor='black')
plt.title('Total Number of Players in Each Club', fontsize=14)
plt.xlabel('Club', fontsize=12)
plt.ylabel('Total Players', fontsize=12)
plt.xticks(rotation=45, ha='right')
plt.grid(axis='y', linestyle='--', alpha=0.7)
for p in ax.patches:
    ax.annotate(f'{p.get_height()}', (p.get_x() + p.get_width() / 2., p.get_height()),
                ha='center', va='center', xytext=(0, 10), textcoords='offset points')
plt.tight_layout()
plt.show()

# 5. Distribution of the Player's Dominant Foot
foot_distribution = player['foot'].value_counts()
colors = ['#ff9999', '#66b3ff', '#99ff99']
explode = (0.1, 0, 0)
plt.figure(figsize=(8, 8))
foot_distribution.plot(kind='pie', autopct='%1.1f%%', colors=colors, explode=explode, shadow=True)
plt.title("Distribution of Player's Dominant Foot")
plt.legend(foot_distribution.index, loc='upper right')
plt.axis('equal')
plt.show()

# 6. The Relationship Between Player Height and Age
sns.set(style="whitegrid")
plt.figure(figsize=(10, 8))
sns.scatterplot(data=player, x='height', y='age', hue='position', palette='Set1', s=100, alpha=0.7)
plt.title("Relationship Between Player Height and Age", fontsize=14)
plt.xlabel("Height (cm)", fontsize=12)
plt.ylabel("Age", fontsize=12)
plt.legend(title='Position', bbox_to_anchor=(1.05, 1), loc='upper left')
plt.tight_layout()
plt.show()

# 7. Analyze Clubs with the Highest Players
average_height_by_club = player.groupby('club')['height'].mean()
tallest_club = average_height_by_club.idxmax()
print(f"Club with the tallest average players' height: {tallest_club}")
sns.set(style="whitegrid")
plt.figure(figsize=(12, 8))
ax = average_height_by_club.plot(kind='bar', color='skyblue', edgecolor='black')
ax.bar(tallest_club, average_height_by_club[tallest_club], color='red')
plt.title('Average Height of Players by Club', fontsize=14)
plt.xlabel('Club', fontsize=12)
plt.ylabel('Average Height (cm)', fontsize=12)
plt.xticks(rotation=45, ha='right')
plt.grid(axis='y', linestyle='--', alpha=0.7)
for p in ax.patches:
    height = p.get_height()
    ax.annotate(f'{height:.2f}', (p.get_x() + p.get_width() / 2., height),
                ha='center',
