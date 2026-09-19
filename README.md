# NumPy-and-Pandas-Data-Analysis
# 📊 Python Data Analytics – 
NumPy and Pandas Data Analysis
---

## 📌 Project Overview

This project is part of the **Python Data Analytics – Module 5** assignment.

The objective of this project is to practice fundamental **NumPy and Pandas** concepts used in Data Analytics.

The project analyzes:

- 🌡️ Daily temperature data using **NumPy**
- 🎓 Student marks using **Pandas Series**
- 💰 Transaction data using **Pandas DataFrame**

The assignment demonstrates data creation, inspection, indexing, slicing, filtering, aggregation, and data manipulation.

---

## 🎯 Objectives

The key objectives of this project are:

- Create and work with NumPy arrays
- Understand 1D and 2D arrays
- Inspect array shape, data type, and size
- Perform numerical calculations
- Convert Celsius temperatures to Fahrenheit
- Apply NumPy indexing and slicing
- Create Pandas Series with custom indexes
- Use `loc` and `iloc` for data access
- Apply Boolean masking
- Create and explore Pandas DataFrames
- Filter data using multiple conditions
- Perform grouping and aggregation
- Modify, add, and delete data

---

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Python | Programming language |
| NumPy | Numerical and array operations |
| Pandas | Data manipulation and analysis |
| Google Colab | Notebook development |
| Jupyter Notebook | Notebook execution |

---

# 🔹 Part 1 – NumPy Array Operations

## 🌡️ Temperature Analysis

The project uses daily average temperatures recorded over two weeks.

### Week 1

```text
[22.5, 25.3, 20.8, 23.4, 26.1, 24.8, 21.9]
```

### Week 2

```text
[19.2, 22.5, 21.3, 24.0, 23.5, 22.8, 20.1]
```

### NumPy Operations Performed

- 1D array creation
- 2D array creation
- Shape inspection
- Data type inspection
- Number of elements
- Celsius to Fahrenheit conversion
- Maximum temperature
- Minimum temperature
- Mean temperature
- Array indexing
- Array slicing

### Example

```python
temperatures_w1 = np.array(
    [22.5, 25.3, 20.8, 23.4, 26.1, 24.8, 21.9]
)

print(temperatures_w1.shape)
print(temperatures_w1.dtype)
print(temperatures_w1.size)
```

### Temperature Conversion

```python
temperatures_f = (temperatures_w1 * 9/5) + 32
```

### Statistical Analysis

```python
np.max(temperatures_w1)
np.min(temperatures_w1)
np.mean(temperatures_w1)
```

---

# 🔹 Part 2 – Pandas Series

## 🎓 Student Marks Analysis

A Pandas Series named `marks` was created using custom rank indexes.

| Rank | Mark |
|---|---:|
| Rank1 | 95 |
| Rank2 | 92 |
| Rank3 | 89 |
| Rank4 | 85 |
| Rank5 | 80 |

### Operations Performed

- Series creation
- Custom indexing
- Integer position indexing
- Label-based indexing
- `loc`
- `iloc`
- Boolean masking
- Updating values
- Removing entries
- CGPA calculation

### Creating the Series

```python
marks = pd.Series(
    [95, 92, 89, 85, 80],
    index=["Rank1", "Rank2", "Rank3", "Rank4", "Rank5"]
)
```

### Accessing the First Rank

```python
marks.iloc[0]
```

### Retrieving Top 3 Ranks

```python
marks.loc[["Rank1", "Rank2", "Rank3"]]
```

### Boolean Filtering

```python
marks[marks > 90]
```

### Updating Rank 1

```python
marks.loc["Rank1"] = 100
```

### Calculating CGPA

```python
cgpa = marks / 10
```

---

# 🔹 Part 3 – Pandas DataFrame

## 💰 Transaction Data Analysis

A DataFrame named `transactions` was created with the following fields:

- TransactionID
- ProductCategory
- Region
- Amount

### Dataset

| TransactionID | ProductCategory | Region | Amount |
|---:|---|---|---:|
| 101 | Electronics | North | 200 |
| 102 | Clothing | South | 150 |
| 103 | Electronics | North | 300 |
| 104 | Furniture | East | 450 |
| 105 | Clothing | West | 200 |
| 106 | Electronics | North | 250 |
| 107 | Furniture | East | 300 |
| 108 | Clothing | West | 180 |
| 109 | Furniture | South | 350 |
| 110 | Electronics | North | 400 |

---

## 🔍 Data Exploration

The following Pandas functions were used:

```python
transactions.head()
transactions.tail()
transactions.shape
transactions.columns
transactions.dtypes
transactions.info()
```

These functions were used to understand the structure and contents of the dataset.

---

## 🎯 Data Selection

Selected specific columns:

```python
transactions[["ProductCategory", "Amount"]]
```

Retrieved the last three columns:

```python
transactions.iloc[:, -3:]
```

---

## 🔎 Data Filtering

Transactions from the **North region** with an amount greater than **200** were filtered.

```python
transactions[
    (transactions["Region"] == "North") &
    (transactions["Amount"] > 200)
]
```

---

## 📊 Product Category Analysis

The frequency of each product category was calculated using:

```python
transactions["ProductCategory"].value_counts()
```

### Result

| Product Category | Number of Transactions |
|---|---:|
| Electronics | 4 |
| Clothing | 3 |
| Furniture | 3 |

---

## 🌍 Region Analysis

Unique regions were identified using:

```python
transactions["Region"].unique()
```

The dataset contains:

- North
- South
- East
- West

---

## 📈 Grouping and Aggregation

The average transaction amount for each region was calculated using `groupby()` and `mean()`.

```python
transactions.groupby("Region")["Amount"].mean()
```

### Average Amount by Region

| Region | Average Amount |
|---|---:|
| East | 375.00 |
| North | 287.50 |
| South | 250.00 |
| West | 190.00 |

---

# 🔧 DataFrame Manipulation

## Update Transaction Amount

Transaction ID **102** was updated from 150 to 165.

```python
transactions.loc[
    transactions["TransactionID"] == 102,
    "Amount"
] = 165
```

---

## Add Discount Column

A `Discount` column was created using 10% of the transaction amount.

```python
transactions["Discount"] = transactions["Amount"] * 0.10
```

---

## Remove Transaction

Transaction ID **109** was removed.

```python
transactions.drop(
    transactions[transactions["TransactionID"] == 109].index,
    inplace=True
)
```

---

## Delete Discount Column

```python
transactions.drop("Discount", axis=1, inplace=True)
```

---

# 📌 Key Learning Outcomes

Through this assignment, I gained practical experience in:

### NumPy

- Creating 1D and 2D arrays
- Array properties
- Mathematical operations
- Indexing and slicing
- Statistical calculations

### Pandas Series

- Creating labeled data
- Custom indexes
- `loc` and `iloc`
- Boolean masking
- Updating and deleting values
- Data transformation

### Pandas DataFrame

- Creating structured datasets
- Data exploration
- Column selection
- Conditional filtering
- Frequency analysis
- Unique value analysis
- Grouping and aggregation
- Updating data
- Adding and deleting columns
- Removing rows

---

# 💡 Key Insights

### Temperature Dataset

- Week 1 contains 7 daily temperature observations.
- The highest Week 1 temperature is **26.1°C**.
- The lowest Week 1 temperature is **20.8°C**.
- The average Week 1 temperature is approximately **23.54°C**.

### Marks Dataset

- Rank 1 was initially **95** and was updated to **100**.
- Rank 1 and Rank 2 had marks greater than 90.
- CGPA was calculated by dividing marks by 10.

### Transaction Dataset

- **Electronics** has the highest number of transactions.
- North-region transactions with amounts greater than 200 are **103, 106, and 110**.
- The transaction data was grouped by region to calculate average transaction amounts.
- DataFrame manipulation was performed through updating, adding, and deleting data.

---

# 📁 Project Structure

```text
Python-DA-Module-5/
│
├── Python_DA_Module_5_Assignment_1.ipynb
│
├── README.md
│
└── Project_Documentation/
    └── Python_DA_Module_5_Project_Document.docx
```

---

# ▶️ How to Run the Project

### Option 1 – Google Colab

1. Open the `.ipynb` file in Google Colab.
2. Run the cells sequentially.
3. Review the generated outputs.

### Option 2 – Jupyter Notebook

Install the required libraries:

```bash
pip install numpy pandas
```

Then open the notebook using Jupyter Notebook or JupyterLab.

---

# 📚 Conclusion

This project demonstrates the practical application of **NumPy and Pandas** for basic data analysis.

NumPy was used for numerical temperature analysis, while Pandas Series was used for student marks analysis. Pandas DataFrame was used to explore, filter, group, and manipulate transaction data.

The assignment helped strengthen fundamental Data Analytics skills including **data structures, indexing, slicing, filtering, aggregation, and data manipulation using Python**.

---

## 👩‍💻 Author

**Dhivya M**

**Skills Practiced:**  
`Python` · `NumPy` · `Pandas` · `Data Analysis` · `Data Manipulation`

---

⭐ **If you find this project useful, feel free to explore the notebook and code.**
