# ASSIGNMENT-8
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
# Load built-in Iris dataset from seaborn
df = sns.load_dataset("iris")

# Display the first 5 rows
print(df.head())
print(df.info())
print(df.isnull().sum())
# Drop missing values if found
df.dropna(inplace=True)
print(df.describe())
grouped = df.groupby("species").mean()
print(grouped)
# Add synthetic date to simulate time trend
import numpy as np
df['date'] = pd.date_range(start='2023-01-01', periods=len(df), freq='D')
df_sorted = df.sort_values(by='date')

plt.figure(figsize=(10, 5))
plt.plot(df_sorted['date'], df_sorted['sepal_length'])
plt.title('Sepal Length Over Time')
plt.xlabel('Date')
plt.ylabel('Sepal Length')
plt.grid(True)
plt.tight_layout()
plt.show()
plt.figure(figsize=(8, 5))
sns.barplot(data=df, x='species', y='petal_length', ci=None)
plt.title('Average Petal Length per Species')
plt.ylabel('Petal Length')
plt.xlabel('Species')
plt.tight_layout()
plt.show()
plt.figure(figsize=(8, 5))
sns.histplot(df['sepal_width'], bins=20, kde=True)
plt.title('Distribution of Sepal Width')
plt.xlabel('Sepal Width')
plt.tight_layout()
plt.show()
plt.figure(figsize=(8, 5))
sns.scatterplot(data=df, x='sepal_length', y='petal_length', hue='species')
plt.title('Sepal Length vs Petal Length')
plt.xlabel('Sepal Length')
plt.ylabel('Petal Length')
plt.legend(title='Species')
plt.tight_layout()
plt.show()
| Task           | Outcome                                 |
| -------------- | --------------------------------------- |
| Load Data      | Iris dataset loaded and explored        |
| Clean Data     | Checked for missing values              |
| Analyze Data   | Computed stats and grouped insights     |
| Visualize Data | Line, Bar, Histogram, and Scatter plots |
