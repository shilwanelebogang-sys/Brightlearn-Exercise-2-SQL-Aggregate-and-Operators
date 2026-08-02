# SQL Aggregates & Operators — Analytical Exercise

This exercise demonstrates my ability to perform structured data analysis using SQL, with a focus on aggregation, grouping, and conditional filtering.

Using multiple datasets, I solved 15 analytical queries that simulate real business scenarios such as performance tracking, departmental analysis, and financial summaries.

---

## Exercise Overview

In this exercise, I worked with multiple datasets representing different business domains (students, courses, enrollments, salaries, and projects) to:

- Aggregate and summarize data for decision-making  
- Identify trends and patterns across departments  
- Filter both raw data and grouped results  
- Apply SQL logic to answer analytical questions  
- Produce clean, structured, and verifiable outputs  

This exercise reflects how SQL is applied in:
- Reporting and dashboards  
- Operational analysis  
- Performance evaluation  

---

## Skills Demonstrated

### SQL & Data Analysis
- Aggregate functions: `COUNT`, `SUM`, `AVG`, `MIN`, `MAX`  
- Grouping data using `GROUP BY`  
- Filtering grouped data using `HAVING`  
- Row-level filtering using `WHERE`  

### Query Logic & Structure
- Use of logical operators (`AND`, `OR`, `NOT`, `IN`, `BETWEEN`)  
- Understanding execution order (`WHERE` vs `GROUP BY` vs `HAVING`)  
- Writing clean, readable SQL queries  

### Analytical Thinking
- Translating analytical questions into SQL queries  
- Identifying key metrics (totals, averages, counts)  
- Interpreting grouped and aggregated results  

### Data Validation & Presentation
- Manual validation of query outputs  
- Structuring results for reporting  
- Clear documentation of queries and outputs  

---

## 🗂 Datasets Used

### 1. `students`
| Column       | Description |
|-------------|------------|
| student_id  | Student ID |
| name        | Student name |
| age         | Age |
| department  | Department |

### 2. `courses`
| Column       | Description |
|-------------|------------|
| course_id   | Course ID |
| course_name | Course name |
| department  | Department |
| credits     | Credits |

### 3. `enrollments`
| Column         | Description |
|---------------|------------|
| enrollment_id | Enrollment ID |
| student_id    | Student ID |
| course_id     | Course ID |
| grade         | Student grade |

### 4. `salaries`
| Column       | Description |
|-------------|------------|
| employee_id | Employee ID |
| name        | Employee name |
| department  | Department |
| salary      | Salary |
| bonus       | Bonus |

### 5. `projects`
| Column       | Description |
|-------------|------------|
| project_id  | Project ID |
| project_name| Project name |
| department  | Department |
| budget      | Budget |

---

## SQL Queries

```sql
-- Question 1
SELECT DISTINCT department FROM students;

-- Question 2
SELECT department, AVG(age) AS avg_age
FROM students
GROUP BY department;

-- Question 3
SELECT department, COUNT(*) AS student_count
FROM students
GROUP BY department
HAVING COUNT(*) > 1;

-- Question 4
SELECT * FROM students
WHERE age BETWEEN 21 AND 23;

-- Question 5
SELECT * FROM students
WHERE department IN ('IT', 'HR')
AND age > 21;

-- Question 6
SELECT department, SUM(credits) AS total_credits
FROM courses
GROUP BY department
HAVING SUM(credits) > 5;

-- Question 7
SELECT * FROM courses
WHERE credits <> 4;

-- Question 8
SELECT course_id, course_name, credits
FROM courses
ORDER BY credits DESC
LIMIT 3;

-- Question 9
SELECT 
    MAX(grade) AS max_grade,
    MIN(grade) AS min_grade,
    AVG(grade) AS avg_grade
FROM enrollments;

-- Question 10
SELECT course_id, COUNT(*) AS enrollment_count
FROM enrollments
GROUP BY course_id;

-- Question 11
SELECT department,
       SUM(salary) AS total_salary,
       SUM(bonus) AS total_bonus
FROM salaries
GROUP BY department;

-- Question 12
SELECT department, AVG(salary) AS avg_salary
FROM salaries
GROUP BY department
HAVING AVG(salary) > 55000;

-- Question 13
SELECT 
    employee_id,
    name,
    salary,
    bonus,
    (salary + bonus) AS total_compensation
FROM salaries
WHERE (salary + bonus) > 60000;

-- Question 14
SELECT department,
       SUM(budget) AS total_budget,
       AVG(budget) AS avg_budget
FROM projects
GROUP BY department
HAVING AVG(budget) > 70000;

-- Question 15
SELECT 
    project_id,
    project_name,
    department,
    budget
FROM projects
WHERE budget BETWEEN 50000 AND 120000
AND department <> 'Marketing';
