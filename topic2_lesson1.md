
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
<img width="467" height="161" alt="Screenshot 2025-09-04 at 6 21 43 PM" src="https://github.com/user-attachments/assets/a8a0a2ef-1d2c-4bdd-8502-cb3e9c9ad019" />


**Select multiple columns:**  
```python
print(students_df[["name", "age"]])  # This gives you a DataFrame (2 columns)
```
<img width="324" height="171" alt="Screenshot 2025-09-04 at 6 21 50 PM" src="https://github.com/user-attachments/assets/52eea9c2-bcdf-4d35-b6b6-ee0436fab9ab" />

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
<img width="315" height="136" alt="Screenshot 2025-09-04 at 6 22 54 PM" src="https://github.com/user-attachments/assets/86e23600-f251-457f-8296-666bae5e2cd2" />

#### `.iloc[]`  
- Think **i for index number**.  
- Uses numbers (row position).  
- Helpful when you know the position/index of the element.  

**Example: Get the 3rd row (Carol):**  
```python
students_df = students_df.reset_index()
print(students_df.iloc[2])
```
<img width="208" height="137" alt="Screenshot 2025-09-04 at 6 23 17 PM" src="https://github.com/user-attachments/assets/fb9f9759-093e-441f-995d-3254415cd839" />

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
<img width="496" height="75" alt="Screenshot 2025-09-04 at 6 23 45 PM" src="https://github.com/user-attachments/assets/f95415cc-b165-4ee4-86c4-3dc1eaedfc33" />

**Example: Students with grade “A”**  
```python
print(students_df[students_df["grade"] == "A"])
```
<img width="484" height="93" alt="Screenshot 2025-09-04 at 6 24 01 PM" src="https://github.com/user-attachments/assets/4fd6d2bc-7041-41b9-b867-e146f9a93b45" />

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
<img width="532" height="239" alt="Screenshot 2025-09-04 at 6 24 12 PM" src="https://github.com/user-attachments/assets/d4bd9642-d929-4c77-ae31-90ff17bd68a8" />

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
