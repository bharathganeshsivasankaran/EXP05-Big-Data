# EXP05-Big-Data
## ANALYSIS AND VISUALIZATION OF COVID-19 DATASET
```
Name : Bharathganesh S
Reg No : 212222230022
```
### AIM:
To To analyze a large real-world COVID-19 dataset using Python and visualize key trends through multiple graphs for meaningful insights.

### PROCEDURE:

Step : 1 Install required libraries like pandas and matplotlib using pip.

Step : 2 Import the libraries and load the dataset covid_cases.csv using Pandas.

Step : 3 Display the dataset’s shape, column names, and first few rows for overview.

Step : 4 Check and handle missing data by filling or dropping null values.

Step : 5 Perform basic data exploration such as total records and statistical summary.

Step : 6 Create multiple visualizations using Matplotlib — line, bar, pie, scatter, and histogram plots.

Step : 7 Label all plots with proper titles, axis names, and legends for clarity.

Step : 8 Run the program and analyze visual outputs to derive key insights and trends.

### PROGRAM:
```py

import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_csv("covid_cases.csv")

print("----- First 5 Records -----")
print(df.head())

print("\nDataset Shape (Rows, Columns):", df.shape)

print("\nColumn Names:")
print(df.columns.tolist())

print("\nMissing Values in Each Column:")
print(df.isnull().sum())

df.fillna(0, inplace=True)

# 2. Basic Data Exploration

print("\nTotal Number of Records:", len(df))

print("\n----- Statistical Summary -----")
print(df.describe())

# 3. Visualization using Matplotlib

# To make plots look better
plt.style.use('seaborn-v0_8')
plt.rcParams['figure.figsize'] = (10, 6)

# Line Graph: Trend of confirmed cases over time (Globally)


df['date'] = pd.to_datetime(df['date'])
global_trend = df.groupby('date')['confirmed'].sum()

plt.figure()
plt.plot(global_trend.index, global_trend.values, color='blue', marker='o')
plt.title("Global Trend of Confirmed COVID-19 Cases Over Time")
plt.xlabel("Date")
plt.ylabel("Number of Confirmed Cases")
plt.grid(True)
plt.show()

# Bar Chart: Top 10 countries by total confirmed cases

country_confirmed = df.groupby('country')['confirmed'].sum().sort_values(ascending=False).head(10)

plt.figure()
country_confirmed.plot(kind='bar', color='orange')
plt.title("Top 10 Countries by Total Confirmed Cases")
plt.xlabel("Country")
plt.ylabel("Total Confirmed Cases")
plt.xticks(rotation=45)
plt.show()

# Pie Chart: Case distribution of top 5 affected countries

top5 = df.groupby('country')['confirmed'].sum().sort_values(ascending=False).head(5)

plt.figure()
plt.pie(top5, labels=top5.index, autopct='%1.1f%%', startangle=140)
plt.title("Case Distribution of Top 5 Affected Countries")
plt.show()

# Scatter Plot: Relation between Confirmed and Deaths

plt.figure()
plt.scatter(df['confirmed'], df['deaths'], color='red', alpha=0.5)
plt.title("Relationship between Confirmed Cases and Deaths")
plt.xlabel("Confirmed Cases")
plt.ylabel("Deaths")
plt.grid(True)
plt.show()

# Histogram: Distribution of Active Cases

plt.figure()
plt.hist(df['active'], bins=20, color='green', edgecolor='black')
plt.title("Distribution of Active COVID-19 Cases")
plt.xlabel("Active Cases")
plt.ylabel("Frequency")
plt.grid(True)
plt.show()

```
### OUTPUT:

<img width="1066" height="482" alt="image" src="https://github.com/user-attachments/assets/52bad40d-2088-4110-a01a-f5ff483c8edb" />

<img width="1045" height="306" alt="image" src="https://github.com/user-attachments/assets/c657b3e5-7e83-48d8-b3d4-9bd5fd0929b6" />

### Line Graph: Trend of confirmed cases over time (Globally)

<img width="1215" height="567" alt="image" src="https://github.com/user-attachments/assets/827f36c0-4bb1-4cbd-b5ce-864038cfbcae" />

### Bar Chart: Top 10 countries by total confirmed cases

<img width="1340" height="602" alt="image" src="https://github.com/user-attachments/assets/fb6fb09f-321b-4856-b2cc-17ce95109fe5" />

### Pie Chart: Case distribution of top 5 affected countries

<img width="1066" height="517" alt="image" src="https://github.com/user-attachments/assets/4999406d-a6b7-40be-9923-b3bdb8eedf9b" />

### Scatter Plot: Relation between Confirmed and Deaths

<img width="1278" height="564" alt="image" src="https://github.com/user-attachments/assets/72855a41-4614-4b64-8235-b60e58341b6c" />

### Histogram: Distribution of Active Cases

<img width="1266" height="564" alt="image" src="https://github.com/user-attachments/assets/079fd5a9-8f1e-4b24-8275-43e5cfaf95c1" />

### RESULT:
The Python program successfully analyzes and visualizes the COVID-19 dataset.
