# 🧠 SQL LeetCode 50 — Problem Solutions and Insights

Welcome to my **SQL LeetCode 50 Questions Repository**!  
This repository contains **solutions, explanations, and learning notes** for the study plan of top 50 SQL problems on [LeetCode](https://leetcode.com/problemset/database/).  

Each solution is written to emphasize **clean query structure, logical reasoning, and performance optimization** — helping not just to solve, but to **understand SQL deeply**.

---


---

## 💡 Learning Focus

| Concept | Description |
|----------|-------------|
| **SELECT, WHERE, ORDER BY** | Core query syntax and filtering conditions |
| **GROUP BY & HAVING** | Aggregations and logical grouping |
| **JOIN (INNER, LEFT, SELF)** | Combining relational data |
| **Subqueries** | Nested logic and data dependency |
| **Window Functions** | Ranking, cumulative sums, and moving averages |
| **CTEs (Common Table Expressions)** | Breaking down complex queries for readability |
| **CASE WHEN** | Conditional logic within SQL |

---

## 🧩 Example Problem

### 🔹 Problem: Department Highest Salary  
**LeetCode #184**

**Goal:** Find the employee(s) with the highest salary in each department.

```sql
SELECT D.name AS Department,
       E.name AS Employee,
       E.salary AS Salary
FROM Employee E
JOIN Department D ON E.departmentId = D.id
WHERE (E.departmentId, E.salary) IN (
    SELECT departmentId, MAX(salary)
    FROM Employee
    GROUP BY departmentId
);
