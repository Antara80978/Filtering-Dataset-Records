# 📊 Task 19: Filter Dataset Records

This repository contains the implementation and documentation for **Task 19** of the **AI & ML Track at Veda Technology**.

The task focuses on filtering records from a Pandas DataFrame using **Boolean conditions**, including single conditions and multiple conditions with `AND` and `OR` operators.

---

## 📌 Description

In this task, a sample **Student Performance Dataset** is created using Pandas.

Different filtering techniques are implemented to identify specific records based on:

* Student scores
* Age
* Grade
* Pass/fail status

The task demonstrates how **Boolean Masking** can be used to filter DataFrame rows efficiently.

---

## 🎯 Objectives

* [x] Create a sample dataset using Pandas.
* [x] Implement at least **3 filtering examples**.
* [x] Filter records using a single condition.
* [x] Combine multiple conditions using `AND`.
* [x] Combine multiple conditions using `OR`.
* [x] Display the filtered DataFrames.
* [x] Display the number of filtered records.
* [x] Understand Boolean masking in Pandas.
* [x] Answer common Pandas filtering interview questions.

---

## 🛠️ Tools & Technologies

* **Python 3.x**
* **Pandas**
* **Jupyter Notebook / Python Script**

---

## 📂 Dataset

A sample **Student Performance Dataset** is created directly in the Python program.

| Column       | Description                |
| ------------ | -------------------------- |
| `Student_ID` | Unique ID of the student   |
| `Name`       | Student name               |
| `Age`        | Student age                |
| `Grade`      | Academic grade             |
| `Score`      | Student's score            |
| `Passed`     | Whether the student passed |

---

## 🚀 Implementation

### Import Pandas and Create Dataset

```python
import pandas as pd

# Sample Dataset: Student Performance
data = {
    'Student_ID': [101, 102, 103, 104, 105, 106, 107],
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Eva', 'Frank', 'Grace'],
    'Age': [19, 21, 20, 22, 19, 21, 20],
    'Grade': ['A', 'B', 'A', 'C', 'B', 'A', 'F'],
    'Score': [92, 78, 88, 65, 82, 95, 45],
    'Passed': [True, True, True, True, True, True, False]
}

df = pd.DataFrame(data)

print("Student Performance Dataset:")
print(df)
```

---

## 🔎 Filtering Examples

### Example 1: Single Condition

Find students whose score is greater than `80`.

```python
high_scorers = df[df['Score'] > 80]

print("Example 1: High Scorers (Score > 80)")
print(high_scorers)
print(f"Total Records: {len(high_scorers)}")
```

**Condition used:**

```python
df['Score'] > 80
```

This creates a Boolean Series containing `True` for students with scores above 80 and `False` for the remaining students.

---

### Example 2: Multiple Conditions using AND

Find students who are **older than 19 AND have Grade A**.

```python
top_older = df[(df['Age'] > 19) & (df['Grade'] == 'A')]

print("Example 2: Top Older Students (Age > 19 AND Grade == 'A')")
print(top_older)
print(f"Total Records: {len(top_older)}")
```

The `&` operator means **AND**.

Both conditions must be `True` for a record to be selected.

---

### Example 3: Multiple Conditions using OR

Find students who either scored below `50` **OR** did not pass.

```python
at_risk = df[(df['Score'] < 50) | (df['Passed'] == False)]

print("Example 3: At-Risk Students (Score < 50 OR Passed == False)")
print(at_risk)
print(f"Total Records: {len(at_risk)}")
```

The `|` operator means **OR**.

A record is selected when at least one of the conditions is `True`.

---

## 🧠 Key Concepts

### 1. Boolean Masking

Boolean masking is a technique used to filter rows based on a condition.

For example:

```python
df['Score'] > 80
```

produces a Boolean Series such as:

```text
True
False
True
False
True
True
False
```

When this Boolean Series is passed to the DataFrame:

```python
df[df['Score'] > 80]
```

only the rows where the condition is `True` are returned.

---

### 2. Logical Operators

Pandas uses bitwise operators for combining conditions:

| Operator | Meaning | Example                       |               |                    |
| -------- | ------- | ----------------------------- | ------------- | ------------------ |
| `&`      | AND     | `(Age > 19) & (Grade == 'A')` |               |                    |
| `        | `       | OR                            | `(Score < 50) | (Passed == False)` |
| `~`      | NOT     | `~(Grade == 'A')`             |               |                    |

---

### 3. Parentheses

Parentheses are important when combining conditions in Pandas.

Correct:

```python
df[(df['Age'] > 19) & (df['Grade'] == 'A')]
```

Without parentheses, Python's operator precedence can result in an error or unexpected behavior.

---

## 📊 Expected Results

### Example 1 — Score > 80

The filtered records are:

* Alice — 92
* Charlie — 88
* Eva — 82
* Frank — 95

**Total Records: 4**

### Example 2 — Age > 19 AND Grade A

The filtered record is:

* Frank — Age 21, Grade A

**Total Records: 1**

### Example 3 — Score < 50 OR Passed = False

The filtered record is:

* Grace — Score 45, Failed

**Total Records: 1**

---

## ❓ Interview Questions & Answers

### 1. How do you filter rows in Pandas?

Rows can be filtered using **Boolean Indexing**.

A condition applied to a DataFrame column produces a Boolean mask containing `True` and `False` values.

For example:

```python
df[df['Score'] > 80]
```

returns only the rows where the score is greater than 80.

---

### 2. How do you combine multiple conditions?

Multiple conditions can be combined using Pandas bitwise operators:

* `&` → **AND**
* `|` → **OR**
* `~` → **NOT**

Example:

```python
df[(df['Age'] > 19) & (df['Grade'] == 'A')]
```

---

### 3. Why are parentheses important in Pandas conditions?

Parentheses ensure that each comparison is evaluated before the logical operation is performed.

For example:

```python
(df['Age'] > 19) & (df['Grade'] == 'A')
```

Each condition is evaluated separately before `&` combines them.

This prevents operator-precedence errors and makes the filtering logic clear.

---

### 4. What is Boolean Masking?

Boolean masking is the process of creating a Boolean condition and using it to select only the rows that satisfy that condition.

Example:

```python
mask = df['Score'] > 80
filtered_data = df[mask]
```

---

## ▶️ How to Run

### Step 1: Install Pandas

```bash
pip install pandas
```

### Step 2: Open the Notebook or Python File

Run the code using:

* Jupyter Notebook
* JupyterLab
* VS Code
* Any Python IDE

### Step 3: Execute the Code

The program will create the dataset, apply the filtering conditions, and display the filtered records along with their counts.

---

## 📁 Project Structure

```text
Task-19-Filter-Dataset-Records/
│
├── task19.py
├── README.md
└── screenshots/
    └── output.png
```

---

## 📚 Key Learnings

Through this task, I learned:

* How to filter DataFrame rows using Pandas.
* How Boolean masking works.
* How to apply single filtering conditions.
* How to combine conditions using `&` and `|`.
* The importance of parentheses in Pandas conditions.
* How to count filtered records.
* How Pandas filtering is used in practical data analysis.

---

## 👩‍💻 Author

**Antara Sarvade**

AI & ML Track
**Veda Technology**

---

⭐ **Task 19 completed successfully!**
