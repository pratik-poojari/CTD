
# Lesson 1 - Topic 2

## Selecting & Filtering Data

---

### Selecting Columns

Think of a column like a single list/Series inside the table.  
Sometimes you don’t need the whole table, only a few columns.  

For instance: In a dataset with student info, maybe you only care about **name** and **score** for a leaderboard.

**Select one column:**  
```python
print(students_df["name"])  # This gives you a Series (just one column)
```

**Select multiple columns:**  
```python
print(students_df[["name", "age"]])  # This gives you a DataFrame (2 columns)
```

---

### Selecting Rows

Datasets can be huge, millions of rows. Being able to grab just the row(s) you need helps when debugging, checking a specific entry, or sampling data.

#### `.loc[]`  
- Great when your dataset has **meaningful labels** (names, IDs, dates, etc.).  
- Instead of remembering row numbers, you can just use the label.  

**Example: Get the row for Carol**  
```python
students_df = students_df.set_index("name")
print(students_df.loc["Carol"])
```

#### `.iloc[]`  
- Think **i for index number**.  
- Uses numbers (row position).  
- Helpful when you know the position/index of the element.  

**Example: Get the 3rd row (Carol):**  
```python
students_df = students_df.reset_index()
print(students_df.iloc[2])
```

---

### Filtering Rows by Condition

Filtering = ask a question and get matching rows.  
This helps us find rows based on conditions.  

**Real analysis questions:**  
- “Which students scored above 90?”  
- “Who is younger than 25?”  

**Example: Students older than 30**  
```python
print(students_df[students_df["age"] > 30])
```

**Example: Students with grade “A”**  
```python
print(students_df[students_df["grade"] == "A"])
```

---

### Sorting Data

We can sort rows by any column. Sorting helps you see patterns.  

For example:  
- Sort students by **score** to see the top performers.  
- Sort by **age** to see youngest/oldest.  

**Example: Sort by score (descending):**  
```python
students_df.sort_values("score", ascending=False)
```

---

## Quiz: Selecting & Filtering Data 🎯

**Q1. How do you select just the `name` column from `students_df`?**  
A1. `students_df["name"]`  

**Q2. How do you select both `name` and `age` columns?**  
A2. `students_df[["name", "age"]]`  

**Q3. How do you select the first row using `.iloc`?**  
A3. `students_df.iloc[0]`  

**Q4. How do you select the third row using `.loc` (assuming labels)?**  
A4. `students_df.loc[2]`  

**Q5. Show the rows where age is greater than 30.**  
A5. `students_df[students_df["age"] > 30]`  

---

✅ This wraps up **Part 2 of Lesson 1**.
