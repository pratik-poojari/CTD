
# Lesson 1 - Topic 1

## Recapping and Adding to What We Learned in Python 100

### Prerequisites
- Operators  
- Data Types  
- Loops  
- Functions  
- File types (.CSV, .Excel)

### Topics Covered
- **Pandas** (load, clean, and analyze data)  
- **Numpy** (complex numerical operations)  
- **Matplotlib** (visualization or plotting the data on graphs)  

---

## Pandas

Pandas is a Python library that makes it easy to work with structured data, like tables you’d see in Excel or a database. It helps you store, clean, analyze, and explore data quickly and efficiently.

There is a ton of data being generated and processed every second and most real-world data comes in messy formats, missing values, weird columns, extra info, or in files like CSVs or Excel spreadsheets.

**Pandas helps you:**
- Load that data into Python.  
- Clean it up.  
- Ask useful questions like:  
  - “What’s the average income in this dataset?”  
  - “How many people signed up last week?”  
  - “Which product had the most sales?”  

It’s used in data analytics, machine learning, finance, science, and pretty much anywhere people work with data.

---

## Getting Started with Pandas

### What is a DataFrame and a Series?

**DataFrame**  
You can think of a DataFrame as a two-dimensional table or a spreadsheet in Python.  
- It has rows and columns.  
- Each column has a name.  
- Each row has an index number.  

Rule of Thumb: a DataFrame has two axes, just like a table.  
- **Rows** (top to bottom) = Axis 0  
- **Columns** (left to right) = Axis 1  

👉 More on DataFrames: [GeeksforGeeks Pandas DataFrame](https://www.geeksforgeeks.org/pandas/python-pandas-dataframe/)  

**Series**  
You can think of a Series as just one column from a DataFrame.  
- It has values and an index, but only one column.  
- Can store heterogeneous data types.  
- A Series is like a fancy list that knows the name of each item.  

👉 More on Series: [GeeksforGeeks Pandas Series](https://www.geeksforgeeks.org/python/python-pandas-series/)  

---

## Installing and Importing Pandas

```bash
pip install pandas
```

Once installed, import it into your Python code:

```python
import pandas as pd
```

---

## Reading from a CSV File

**What is a CSV file?**  
CSV = Comma-Separated Values. It’s a plain text file that looks like a spreadsheet, where each row is a line and columns are separated by commas.

```python
# Read data from a CSV file
df = pd.read_csv('customers_100.csv')
```

---

## Creating a DataFrame

You can create DataFrames in several ways:

**From a Dictionary (most common):**  
```python
data = {
    "name": ["Alice", "Bob", "Carol"],
    "age": [25, 30, 22],
    "grade": ["A", "B", "A"]
}
df = pd.DataFrame(data)
print(df)
```

**From a List of Dictionaries:**  
```python
students = [
    {"name": "Alice", "age": 25, "grade": "A"},
    {"name": "Bob", "age": 30, "grade": "B"}
]
df = pd.DataFrame(students)
print(df)
```

**From a List of Lists (with column names):**  
```python
data = [
    ["Alice", 25, "A"],
    ["Bob", 30, "B"],
    ["Carol", 22, "A"]
]
df = pd.DataFrame(data, columns=["name", "age", "grade"])
print(df)
```

---

## Creating a Series

**From a Python list:**  
```python
numbers = [10, 20, 30, 40]
num_series = pd.Series(numbers)
print(num_series)
```

**From a list with custom labels:**  
```python
data = [85, 90, 95]
names = ["Alice", "Bob", "Carol"]
my_series = pd.Series(data, index=names)
print(my_series)
```

**From a Dictionary:**  
```python
data = {"Alice": 85, "Bob": 90, "Carol": 95}
my_dict_series = pd.Series(data)
print(my_dict_series)
```

---

## Reading a Series from a DataFrame

```python
data = {
    "name": ["Alice", "Bob", "Carol"],
    "age": [25, 30, 22]
}
df = pd.DataFrame(data)
print(df)

# Read a Series (pick a column)
ages = df["age"]
print(ages)
```

---

## Why Series are Important

- A DataFrame is really just a collection of Series.  
- Series can have **labels** (indexes) which make it easy to access values.  
- Series handle **missing data** with NaN gracefully.  

```python
s = pd.Series([85, 90, 95], index=["Alice", "Bob", "Carol"])
print(s["Bob"])  # Output: 90

s = pd.Series([10, None, 30])
print(s)  # Handles missing values
```

---

## Exploring Your Data in Pandas

When you load a dataset, you might want to get a quick look at it. Pandas provides:  
- `.head()` → Peek at first few rows  
- `.tail()` → Peek at last few rows  
- `.info()` → Structure, datatypes, missing values  
- `.describe()` → Quick statistics summary  

Example with `students.csv`:

```python
students_df = pd.read_csv("students.csv")
print(students_df.head(2))   # First 2 rows
print(students_df.tail())    # Last 5 rows
print(students_df.info())    # Structure info
print(students_df.describe()) # Stats summary
```

---

## Assessment Time 🎯

You have the dataset **students.csv** loaded into a DataFrame called `students_df`.  

**Q1. How many rows are in the dataset?**  
A1. 6 rows  

**Q2. How many columns are there?**  
A2. 6 columns  

**Q3. Which columns have missing values?**  
A3. age, grade, city, score  

**Q4. What are the data types of the age and score columns?**  
A4. Both are float64  

**Q5 (Bonus). How many students are missing their score?**  
A5. 1 student  
