
🚢 Enhanced Titanic Survival Analysis 🔍📊
✨ Improvements Over Original Analysis


🧹 Better Data Cleaning:
✅ Used median instead of mean for age imputation
👨‍👩‍👧‍👦 Created new FamilySize feature
📊 More detailed age groups (5 categories)
🔍 Additional Insights:
📈 Survival rates by family size
🚢 Embarkation port analysis
👴 Identified oldest survivor
🖼️ Comprehensive visualizations



🧩 Code Structure:
🧱 Modular functions for better organization
💄 Improved display formatting
🤖 Automated visualization generation

📌 New Findings
👨‍👩‍👧‍👦 Survival by Family Size
👪 Family Size	💚 Survival Rate
1	30.35%
2	55.26%
3	57.84%
4	72.41%
5+ 20.00%

🌟 Notable Passengers
👶 Youngest survivor: Miss. Lillian Gertrud Asplund (🍼 0.42 years)
👴 Oldest survivor: Mr. Algernon Henry Wilson Barkworth (🎩 80.00 years)










# Titanic Dataset - Exploratory Data Analysis (EDA)

![Titanic](https://upload.wikimedia.org/wikipedia/commons/thumb/f/fd/RMS_Titanic_3.jpg/1200px-RMS_Titanic_3.jpg)

## Project Overview
This project performs exploratory data analysis (EDA) on the Titanic passenger dataset to uncover patterns in survival rates. The analysis includes data cleaning, visualization, and feature engineering.

## Dataset Information
- Source: Built-in Seaborn dataset (`sns.load_dataset('titanic')`)
- Original Features: 15 columns including passenger class, age, gender, fare, etc.
- Target Variable: `survived` (0 = No, 1 = Yes)

## Data Cleaning Steps
1. **Removed Columns**:
   - `deck` (too many missing values)
   - `embark_town` (redundant with `embarked`)

2. **Handled Missing Values**:
   - Age: Filled with median (28.0 years)
   - Embarked: Filled with mode ('S')

3. **Dropped Remaining NA**:
   - Removed rows with any missing values

4. **Created New Features**:
   - `is_child`: Boolean (age < 18)
   - `family_size`: Sum of siblings/spouses + parents/children

## Key Visualizations
1. **Passenger Class Distribution**:
   - Countplot showing number of passengers by class

2. **Age Distribution**:
   - Histogram with KDE showing passenger age distribution

3. **Survival Analysis**:
   - Survival rates by passenger class
   - Survival rates by gender
   - Survival rates by age group (children vs adults)

# Load dependencies
import seaborn as sns
import pandas as pd
import matplotlib.pyplot as plt

# Load and clean data
df = sns.load_dataset('titanic')
df.drop(columns=['deck','embark_town'], inplace=True)
df['age'].fillna(df['age'].median(), inplace=True)
df['embarked'].fillna(df['embarked'].mode()[0], inplace=True)
df.dropna(inplace=True)

# Create visualizations
sns.countplot(x='pclass', data=df)
plt.title('Passenger Class Distribution')
plt.show()

