
# Data Visualization using Matplotlib

## Why Visualization Matters?

Imagine you have exam scores of 100 students. You could look at the raw numbers in a table, but that would feel overwhelming.  
Instead, a single chart can instantly show you trends, like who’s performing better, how many failed, or whether scores are clustered around a certain range.

👉 That’s the power of Matplotlib — it turns numbers into pictures.

---

## Installing and Importing Matplotlib

In VS Code, run:  
```bash
pip install matplotlib
```

Then import the library:  
```python
import matplotlib.pyplot as plt
```

---

## Basic Plotting

### 1. Line Plot (Trends over time)
**Use case:** Tracking your monthly expenses.

```python
months = ["Jan", "Feb", "Mar", "Apr"]
expenses = [200, 250, 300, 220]

plt.plot(months, expenses)
plt.title("Monthly Expenses")
plt.xlabel("Month")
plt.ylabel("Amount ($)")
plt.show()
```

Output:

---

### 2. Bar Plot (Comparisons)
**Use case:** Comparing marks of different students.

```python
students = ["Alice", "Bob", "Charlie"]
marks = [85, 90, 78]

plt.bar(students, marks, color="orange")
plt.title("Student Marks")
plt.xlabel("Students")
plt.ylabel("Marks")
plt.show()
```

Output:

---

### 3. Scatter Plot (Relationships between two things)
**Use case:** Hours studied vs. exam score.

```python
hours = [2, 4, 6, 8, 10]
scores = [50, 60, 70, 80, 90]

plt.scatter(hours, scores, color="green")
plt.title("Hours Studied vs Score")
plt.xlabel("Hours")
plt.ylabel("Score")
plt.show()
```

Output:

---

### 4. Histogram (Distribution of data)
**Use case:** How exam scores are spread out in a class.

```python
scores = [55, 60, 61, 62, 65, 70, 72, 80, 85, 90, 90, 92, 95]

plt.hist(scores, bins=5, color="purple", edgecolor="black")
plt.title("Score Distribution")
plt.xlabel("Score Range")
plt.ylabel("Number of Students")
plt.show()
```

Output:

---

## Customization (Making Charts Readable)

Adding titles, labels, legends, colors makes your chart easy to understand.

**Example:**  
```python
plt.plot(months, expenses, label="Expenses", color="red", marker="o")
plt.title("Monthly Expenses")
plt.xlabel("Month")
plt.ylabel("Amount ($)")
plt.legend()
plt.show()
```

Output:

---

## Lesson 1 Wrap-Up

🎉 Congrats! You’ve completed Lesson 1.  

You now know the **three pillars of data analysis**:  
- **Pandas** → handle and explore data tables  
- **NumPy** → fast math & calculations  
- **Matplotlib** → turn numbers into visual stories  

With just these, you can already clean data, analyze trends, and make charts. This is the foundation every data scientist uses daily.  

📌 Keep practicing — the more you play with data, the more confident you’ll get. You’re off to a great start!
