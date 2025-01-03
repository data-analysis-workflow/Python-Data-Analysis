# Handling Outliers in Numerical and Categorical Data

This document outlines strategies for identifying and handling outliers in both numerical and categorical datasets.

## 1. Numerical Data Outliers

Numerical outliers are values that significantly deviate from the majority of the dataset. These are typically continuous or discrete numerical values.

### Handling Methods

**Identify Outliers:**

*   **Statistical methods:**
    *   Z-scores: Measures how many standard deviations a value is from the mean.
    *   IQR (Interquartile Range): The range between the first (Q1) and third (Q3) quartiles.
*   **Visualizations:**
    *   Boxplots: Show the distribution, including potential outliers as points beyond the "whiskers."
    *   Scatterplots: Can help visualize outliers in relation to other variables.

**Handle Outliers:**

*   **Remove:** Delete rows containing outliers if they are due to errors. Use cautiously.
*   **Cap or Winsorize:** Limit values to a specified range, typically the upper and lower bounds of the dataset without outliers.
*   **Transform:** Use transformations like:
    *   Logarithmic: Reduces the impact of large values, useful for skewed data.
    *   Square root: Similar to logarithmic, can help with skewed data.
    *   Box-Cox: A family of transformations that can make data more normally distributed.
*   **Impute:** Replace outliers with:
    *   Mean: Suitable for approximately symmetrical data.
    *   Median: Less sensitive to extreme values, good for skewed data.
    *   Other statistics: Such as the mode or a value predicted by a model.
*   **Analyze Separately:** Create a new group or flag outliers for targeted analysis. This is helpful when outliers have a distinct characteristic or significance.

**Automate Detection:**

*   **Algorithms:**
    *   Isolation Forest: A tree-based algorithm that isolates outliers by making them easily separable.
    *   DBSCAN (Density-Based Spatial Clustering of Applications with Noise): Groups dense points together and labels outliers as noise.
    *   Clustering: Other clustering methods can also identify outliers by finding data points that do not belong to any cluster.

**Example (Python):**
```python
import pandas as pd

# Sample data (replace with your actual data)
data = pd.DataFrame({'age': [25, 30, 28, 22, 35, 80, 26, 29]})

# Removing outliers based on IQR
Q1 = data['age'].quantile(0.25)
Q3 = data['age'].quantile(0.75)
IQR = Q3 - Q1

filtered_data = data[~((data['age'] < (Q1 - 1.5 * IQR)) | (data['age'] > (Q3 + 1.5 * IQR)))]

print("Original Data:\n", data)
print("\nFiltered Data (outliers removed using IQR):\n", filtered_data)
```

## 2. Categorical Data Outliers

Categorical outliers are values that appear infrequently or are unexpected based on the context of the data. These might not be true "outliers" in the statistical sense but can represent anomalies or errors.

### Handling Methods

**Identify Outliers:**

*   **Frequency Analysis:** Count occurrences of each category and identify rare values.
*   **Domain Knowledge:** Use context to recognize invalid or unexpected categories.

**Handle Outliers:**

*   **Group Rare Categories:** Combine infrequent categories into an "Other" category.
*   **Correct:** Correct misspellings or incorrect values based on domain knowledge.
*   **Remove:** Delete rows with invalid categories.
*   **Impute:** Replace with:
    *   Mode: Most frequent value.
    *   Another relevant category: Based on context or business rules.

**Automate Detection:**

*   **Machine learning models:** Use clustering to identify and flag unexpected categories.

**Example (Python):**
```python
import pandas as pd

# Sample data (replace with your actual data)
data = pd.DataFrame({'category': ['A', 'B', 'A', 'C', 'B', 'A', 'D', 'A', 'E', 'E', 'E']})

# Grouping infrequent categories
rare_categories = data['category'].value_counts()[data['category'].value_counts() < 2].index
data['category'] = data['category'].replace(rare_categories, 'Other')

print("Original Data:\n", data)
print("\nData with rare categories grouped:\n", data)
```

## 3. Combined Approaches

When datasets have both numerical and categorical variables:

**Numerical Variables:**

*   Treat outliers as described above.

**Categorical Variables:**

*   Ensure consistency using techniques like:
    *   Encoding (e.g., one-hot or label encoding).
    *   Ensuring all categories are valid based on the domain.

**Interaction Between Categorical and Numerical Variables:**

*   Analyze numerical outliers within each category separately. This determines if they are truly anomalous or just extreme within one specific category.

## Key Differences

| Aspect               | Numerical Data                         | Categorical Data                       |
| -------------------- | -------------------------------------- | -------------------------------------- |
| Outlier Definition   | Values outside statistical thresholds  | Rare or unexpected categories          |
| Detection Tools     | Z-scores, IQR, histograms, boxplots    | Frequency counts, domain knowledge     |
| Handling Methods    | Remove, cap, transform, impute, analyze | Group, correct, remove, or replace      |
| Automation           | Isolation Forest, DBSCAN, clustering   | Clustering or automated anomaly detection |
