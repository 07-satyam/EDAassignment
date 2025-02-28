# Game and Grade Analysis

## Overview
This project analyzes the relationship between gaming habits and academic performance using a dataset containing students' grades and gaming-related factors. The analysis explores various correlations and trends through data visualization and statistical insights.

## Dataset
The dataset is loaded from `gameandgrade.csv` and includes the following columns:
- `Sex`
- `School Code`
- `Playing Years`
- `Playing Often`
- `Playing Hours`
- `Playing Games`
- `Parent Revenue`
- `Father Education`
- `Mother Education`
- `Grade`

## Data Preprocessing
- Removed non-numeric characters and multiple dots from the `Grade` column.
- Converted the `Grade` column to numeric format.
- Checked for missing values and dropped rows with missing values.
- Converted `Grade` to a categorical type for further analysis.

## Exploratory Data Analysis
### Summary Statistics
Basic dataset information and summary statistics are printed to understand the structure and distribution of data.

### Missing Values
Missing values in each column are counted and handled appropriately.

### Histograms
Histograms for numeric columns are plotted to visualize their distributions.

### Grade Distribution
A count plot is created to visualize the distribution of grades among students.

## Data Visualizations and Insights
### Mean Grade vs Parent Revenue
```python
mother_edu_avg_grade = df.groupby('Parent Revenue', as_index=False)['Grade'].mean()
plt.figure(figsize=(8, 4))
sns.barplot(x='Parent Revenue', y='Grade', data=mother_edu_avg_grade, palette='Purples')
plt.title("Mean Grade vs Parent Revenue")
plt.xlabel("Parent Revenue")
plt.ylabel("Mean Grade")
plt.xticks(rotation=0)
plt.tight_layout()
plt.show()
```
*Insight:* This graph shows how parental revenue influences student grades.

### Mean Grade vs Physical Activity
```python
mother_edu_avg_grade = df.groupby('Playing Often', as_index=False)['Grade'].mean()
plt.figure(figsize=(8, 4))
sns.barplot(x='Playing Often', y='Grade', data=mother_edu_avg_grade, palette='Purples')
plt.title("Mean Grade vs Physical activity")
plt.xlabel("How often they play")
plt.ylabel("Mean Grade")
plt.xticks(rotation=0)
plt.tight_layout()
plt.show()
```
*Insight:* Students who play more often tend to have higher grades, indicating a potential positive impact of gaming.

### Mean Grade vs Playing Hours
```python
mother_edu_avg_grade = df.groupby('Playing Hours', as_index=False)['Grade'].mean()
plt.figure(figsize=(8, 4))
sns.barplot(x='Playing Hours', y='Grade', data=mother_edu_avg_grade, palette='Purples')
plt.title("Mean Grade vs How much they play")
plt.xlabel("How much they play")
plt.ylabel("Mean Grade")
plt.xticks(rotation=0)
plt.tight_layout()
plt.show()
```
*Insight:* The performance decreases as playing hours increase, suggesting excessive gaming may negatively impact grades.

### Mean Grade vs Playing Years
```python
mother_edu_avg_grade = df.groupby('Playing Years', as_index=False)['Grade'].mean()
plt.figure(figsize=(8, 4))
sns.barplot(x='Playing Years', y='Grade', data=mother_edu_avg_grade, palette='Purples')
plt.title("Mean Grade vs How long they have been playing")
plt.xlabel("How long they have been playing")
plt.ylabel("Mean Grade")
plt.xticks(rotation=0)
plt.tight_layout()
plt.show()
```
*Insight:* No clear trend is observed, suggesting that the number of years a student has been playing games does not significantly impact academic performance.

### Mean Grade vs School Code
```python
mother_edu_avg_grade = df.groupby('School Code', as_index=False)['Grade'].mean()
plt.figure(figsize=(8, 4))
sns.barplot(x='School Code', y='Grade', data=mother_edu_avg_grade, palette='Purples')
plt.title("Mean Grade vs Which school they belong to")
plt.xlabel("School Code")
plt.ylabel("Mean Grade")
plt.xticks(rotation=0)
plt.tight_layout()
plt.show()
```
*Insight:* Certain schools perform better on average than others, which may indicate differences in educational quality.

### Correlation Heatmap
```python
numeric_df = df.select_dtypes(include=[np.number])
if numeric_df.shape[1] >= 4:
    plt.figure(figsize=(10, 8))
    corr = numeric_df.corr()
    sns.heatmap(corr, annot=True, cmap='coolwarm', fmt='.2f')
    plt.title('Numeric Features Correlation Heatmap')
    plt.tight_layout()
    plt.show()
else:
    print('Not enough numeric features to create a correlation heatmap.')
```
*Insight:* The heatmap visualizes the relationships between numeric variables, showing which factors are more correlated with grades.

## Conclusion
This project explores how different factors related to gaming and parental background impact student grades. While moderate gaming appears to be beneficial, excessive gaming negatively affects performance. Additionally, school quality and parental revenue also play important roles in academic success.

---

### Requirements
To run this analysis, ensure you have the following libraries installed:
```sh
pip install pandas matplotlib seaborn numpy
```

### How to Run
1. Place `gameandgrade.csv` in the same directory as the script.
2. Run the script in a Jupyter Notebook or a Python environment.
3. View the generated plots and insights.

---
Author:Satyam Kumar,23112089,Chemical Engineering

