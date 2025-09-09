
# Topic 5 of Lesson 1: Modifying Data

So far, we’ve learned how to look at data, select/filter it, and clean it.  
Now comes the fun part, modifying the data to make it more useful!

---

## Creating New Columns

Sometimes, we need new information that doesn’t exist in the dataset.

**Example:**  
Let’s say we want to give every student 5 extra points on their score. We can create a new column for this:

```python
students_df["bonus_score"] = students_df["final_score"] + 5

# print specific columns and see the data
print(students_df[["name", "final_score", "bonus_score"]])
```
<img width="430" height="159" alt="Screenshot 2025-09-09 at 3 44 19 PM" src="https://github.com/user-attachments/assets/3c15f083-05a8-4bed-afa3-43c76fcfc542" />

Here we created a new column called **bonus_score**:  
- It simply takes everyone’s final_score and adds 5 extra points.  
- If Bob’s final_score was 70, his bonus_score will show 75.  
- If Carol’s final_score was NaN (missing), the bonus_score will also be NaN.  

---

## Applying Functions to Columns (.apply())

`.apply()` is like telling pandas:  
"Please run this function on every element in this column."

**Example: Make all student names uppercase**

```python
students_df["name_upper"] = students_df["name"].apply(str.upper)
print(students_df[["name", "name_upper"]])
```
<img width="304" height="184" alt="Screenshot 2025-09-09 at 3 45 27 PM" src="https://github.com/user-attachments/assets/a034f773-7107-4e5d-a590-9bd7204bbadd" />

---


## Replacing Values

Sometimes, data has wrong values or needs standardizing.  
We can use `.replace()` for this.

**Example:**  
Suppose some students’ grade column has `"A"`, `"B"`, etc.  
We want to replace `"A"` with `"A+"`.

```python
students_df["class_grade"] = students_df["class_grade"].replace("A", "A+")
print(students_df[["name", "class_grade"]])
```
<img width="263" height="178" alt="Screenshot 2025-09-09 at 3 45 38 PM" src="https://github.com/user-attachments/assets/dc283845-8858-441f-8d31-2d2cd14330c7" />

---

## Exercise

Create a new column called **name_lower** that converts all names to lowercase.

(Hint: Use `str.lower` with `.apply()`)  

**Solution Code (avoid unhiding before trying):**  

<details>
<summary>Show Solution</summary>  

```python
students_df["name_lower"] = students_df["name"].apply(str.lower)
```  
</details>

---

# Topic 6 of Lesson 1: Grouping & Aggregating

When working with data, sometimes we don’t want to look at every row, instead, we want summaries.

For instance:  
- What is the average score for each grade?  
- How many students are there in each city?  

That’s where **grouping & aggregating** comes in!

---

## Grouping Data with .groupby()

`.groupby()` is like telling pandas:  
“Please organize my data by this column.”

**Example: Group students by grade:**  

```python
grouped = students_df.groupby("class_grade")
print(grouped)
```

Note: This won’t immediately show results, it just tells pandas how the data should be grouped.  
We usually combine it with an aggregation function (like mean, sum, count).

---

## Aggregating Data

Aggregation means applying a summary calculation to each group.

**Example 1: Average score by grade**

```python
# This will show the average score for each grade.
print(students_df.groupby("class_grade")["final_score"].mean())
```
<img width="406" height="144" alt="Screenshot 2025-09-09 at 3 46 15 PM" src="https://github.com/user-attachments/assets/f58b548c-b062-4318-867c-74bf196d7e8a" />

**Example 2: Number of students in each city**

```python
# This counts how many students are from each city.
print(students_df.groupby("city")["id"].count())
```
<img width="286" height="191" alt="Screenshot 2025-09-09 at 3 46 26 PM" src="https://github.com/user-attachments/assets/175bcf71-13ca-46d4-b0d8-90d1bb3cac84" />

Grouping & aggregation helps you summarize big datasets into meaningful insights without looking row by row.

---

# Topic 7 of Lesson 1: Merging & Combining Data

When working with data in the real world, we often don’t get one “perfect” dataset with everything in it.  
Instead, information is spread across multiple tables and we need to bring it together. That’s where merging and combining come in.

**Scenario:**  
- Table 1: students’ names and IDs.  
- Table 2: their test results.  
To do meaningful analysis, we need to bring them together.

---

## Merging Data with .merge()

Think of `.merge()` as when you want to bring two different lists together based on a common identifier.

**Example:**  

```python
# List one: Student info
students_info = pd.DataFrame({
    "id": [1, 2, 3],
    "name": ["Alice", "Bob", "Carol"]
})
print(students_info)
```
<img width="234" height="132" alt="Screenshot 2025-09-09 at 3 46 50 PM" src="https://github.com/user-attachments/assets/bf61c077-246f-44be-aa7b-02695288f7ba" />


# List two: Exam scores
exam_scores = pd.DataFrame({
    "id": [1, 2, 3],
    "score": [85, 90, 78]
})
print(exam_scores)

<img width="201" height="128" alt="Screenshot 2025-09-09 at 3 47 13 PM" src="https://github.com/user-attachments/assets/6986efda-0a19-4404-94d2-ad2de26a0277" />

# Merge the two lists on "id"
merged_df = pd.merge(students_info, exam_scores, on="id")
print(merged_df)

<img width="456" height="170" alt="Screenshot 2025-09-09 at 3 49 35 PM" src="https://github.com/user-attachments/assets/c730d5d6-bb61-4d19-bd04-98fc3e1319bc" />

Here, the `on="id"` tells pandas to use the id column as the matching key in both tables.

---

## Combining Data with .concat()

Imagine you have two separate lists of students, and you just want to stack them together into one list.  
Here, we don’t need a common key. We just want to put one list below the other.

**Example:**  

```python
# Class A students
class_a = pd.DataFrame({
    "name": ["Alice", "Bob"],
    "score": [85, 90]
})
print(class_a)
```
<img width="321" height="125" alt="Screenshot 2025-09-09 at 3 50 18 PM" src="https://github.com/user-attachments/assets/8f5fa2d8-863b-459a-b168-bdcae3824685" />

```python
# Class B students
class_b = pd.DataFrame({
    "name": ["Carol", "David"],
    "score": [78, 92]
})
print(class_b)
```
```python
# Combine the two classes into one big list
all_students = pd.concat([class_a, class_b])
print(all_students)
```
<img width="290" height="124" alt="Screenshot 2025-09-09 at 3 50 35 PM" src="https://github.com/user-attachments/assets/3e654800-0443-4eee-87ee-af38672625c3" />

---

## Quiz Time 🎯

**Q1. You have one list with student IDs and names, and another list with student IDs and exam scores. You want to bring the scores next to the names.**  
Options: Should you use **merge** or **concat**?  

<details>
<summary>Show Answer</summary>  
merge (because we’re matching rows using the common key student_id).  
</details>

---

**Q2. You have two lists of students: one for Class A and another for Class B. You just want to put them together into one list of all students.**  
Options: Should you use **merge** or **concat**?  

<details>
<summary>Show Answer</summary>  
concat (because we’re stacking two datasets without matching, one below the other).  
</details>

📺 [Follow the YouTube video on merging and concatenating](https://www.youtube.com/watch?v=4mHm32u4zbQ)

---

# Topic 8 of Lesson 1: Pandas "EDA Superpower" using ydata-profiling

Imagine you’ve just received a large dataset and don’t know where to start.  
Instead of manually checking column by column, you can run a single function that summarizes:  
- Missing values  
- Data types  
- Distributions of each column  
- Correlations between columns  
- Basic visualizations  

Pandas can create an **Exploratory Data Analysis (EDA)** report for you automatically.

---

## Example with ydata-profiling

```python
import pandas as pd  

# load the students data
students_df = pd.read_csv("students.csv")
print(students_df.head())
```

### Step 2: Install the library

```bash
pip install ydata-profiling
```

### Step 3: Import the library

```python
from ydata_profiling import ProfileReport
```

### Step 4: Create a profile report

```python
profile = ProfileReport(students_df, title="Students Data Report", explorative=True)
```

### Step 5: View the report

- Save as HTML:  
```python
profile.to_file("students_report.html")
```

- Or view inline in Jupyter/Colab:  
```python
profile.to_notebook_iframe()
```

---

# Topic 9 (Wrap-up) of Lesson 1: Exporting & Saving Data

After we’re done working with our data, whether it’s cleaning, exploring, or applying operations, we’ll often want to save the dataset.

**Why?**  
- To share with others.  
- To avoid repeating all steps later.  
- To use in other tools (Excel, SQL, ML libraries, etc.).  

---

## Examples

Save to CSV:  
```python
students_df.to_csv("students_cleaned.csv", index=False)
```

Save to Excel:  
```python
students_df.to_excel("students_cleaned.xlsx", index=False)
```

---

## Final Tip for Pandas

You’ll definitely run into errors sometimes, that’s normal!  
Just read the error message carefully and search online. Errors are your best hints for fixing problems.

📺 [Learning Pandas for Data Analysis?](https://www.youtube.com/watch?v=DkjCaAMBGWM)  
📺 [What is Pandas?](https://www.youtube.com/watch?v=dcqPhpY7tWk&t=70s)
