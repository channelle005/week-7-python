# week-7-python
Task 1: Load and Explore the Dataset
Choose a dataset in CSV format (for example, you can use datasets like the Iris dataset, a sales dataset, or any dataset of your choice).
Load the dataset using pandas.
Display the first few rows of the dataset using .head() to inspect the data.
Explore the structure of the dataset by checking the data types and any missing values.
Clean the dataset by either filling or dropping any missing values.

ANSWERS

import pandas as pd

# Step 2: Load the dataset (from a URL or local file)
url = "https://raw.githubusercontent.com/uiuc-cse/data-fa14/gh-pages/data/iris.csv"  # Or use your local file path
df = pd.read_csv(url)

# Step 3: Display the first few rows to inspect the data
print("First 5 rows of the dataset:")
print(df.head())

# Step 4: Explore the structure of the dataset
# Check data types and non-null counts
print("\nData types and non-null counts:")
print(df.info())

# Check for missing values
print("\nMissing values per column:")
print(df.isnull().sum())

# Step 5: Clean the dataset by handling missing values
# Since there are no missing values in the Iris dataset, let's demonstrate two common ways to handle them:

# Option 1: Drop rows with missing values (if any)
df_cleaned = df.dropna()

# Option 2: Fill missing values with column mean (for numerical columns)
# df_filled = df.fillna(df.mean(numeric_only=True))

# Confirm no missing values after cleaning
print("\nMissing values after cleaning (dropna or fillna):")
print(df_cleaned.isnull().sum())  # Use df_filled if you used fillna instead of dropna

Task 2: Basic Data Analysis
Compute the basic statistics of the numerical columns (e.g., mean, median, standard deviation) using .describe().
Perform groupings on a categorical column (for example, species, region, or department) and compute the mean of a numerical column for each group.
Identify any patterns or interesting findings from your analysis.

ANSWERS
import pandas as pd

# Load the dataset (from a URL or local file)
url = "https://raw.githubusercontent.com/uiuc-cse/data-fa14/gh-pages/data/iris.csv"  # Or use your local file path
df = pd.read_csv(url)

# Compute basic statistics for numerical columns
print("Basic statistics of numerical columns:")
print(df.describe())

# Group by species and compute the mean for each numerical column
print("\nGroup by species and compute the mean of numerical columns:")
grouped_mean = df.groupby('species').mean()
print(grouped_mean)

Task 3: Data Visualization
Create at least four different types of visualizations:
Line chart showing trends over time (for example, a time-series of sales data).
Bar chart showing the comparison of a numerical value across categories (e.g., average petal length per species).
Histogram of a numerical column to understand its distribution.
Scatter plot to visualize the relationship between two numerical columns (e.g., sepal length vs. petal length).
Customize your plots with titles, labels for axes, and legends where necessary.

ANSWERS
import matplotlib.pyplot as plt
import pandas as pd

# Load the dataset (from a URL or local file)
url = "https://raw.githubusercontent.com/uiuc-cse/data-fa14/gh-pages/data/iris.csv"
df = pd.read_csv(url)

# 1. Line Chart (Trends Over Time)
plt.figure(figsize=(10, 6))
plt.plot(df['sepal_length'], label='Sepal Length', color='blue')
plt.plot(df['petal_length'], label='Petal Length', color='green')
plt.title('Trends of Sepal and Petal Length Over Time')
plt.xlabel('Time (Row Number)')
plt.ylabel('Length (cm)')
plt.legend()
plt.grid(True)
plt.show()

# 2. Bar Chart (Average Petal Length per Species)
plt.figure(figsize=(8, 5))
species_mean = df.groupby('species')['petal_length'].mean()
species_mean.plot(kind='bar', color=['blue', 'green', 'red'])
plt.title('Average Petal Length per Species')
plt.xlabel('Species')
plt.ylabel('Average Petal Length (cm)')
plt.xticks(rotation=0)
plt.show()

# 3. Histogram (Distribution of Sepal Length)
plt.figure(figsize=(8, 5))
plt.hist(df['sepal_length'], bins=15, color='skyblue', edgecolor='black')
plt.title('Distribution of Sepal Length')
plt.xlabel('Sepal Length (cm)')
plt.ylabel('Frequency')
plt.grid(True)
plt.show()

# 4. Scatter Plot (Sepal Length vs Petal Length)
plt.figure(figsize=(8, 5))
plt.scatter(df['sepal_length'], df['petal_length'], c='purple', alpha=0.5)
plt.title('Sepal Length vs Petal Length')
plt.xlabel('Sepal Length (cm)')
plt.ylabel('Petal Length (cm)')
plt.grid(True)
plt.show()

