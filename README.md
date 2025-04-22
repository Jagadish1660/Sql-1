# 🎓 Student Result Management System (SQL Project)

This is a simple and beginner-friendly **SQL project** to manage student results, courses, and marks using structured relational data. It is designed to help students and freshers learn how to use SQL for real-world database applications.

## 📌 Project Objective

The system manages:
- Student information
- Courses
- Marks/Results
- Retrieval of performance reports

Great for practicing **SQL joins, constraints, and aggregate functions**.

---

## 🛠️ Technologies Used

- 💾 SQL (MySQL / Oracle)
- 🧠 SQL Queries: DDL, DML, Joins, Group By, Aggregate Functions
- 💻 Optional: VS Code + SQLTools (for query execution)

---

## 📁 Project Structure

- `create_database.sql` – Create database and tables
- `insert_data.sql` – Insert sample student, course, and marks data
- `queries.sql` – Practice useful SELECT queries and reports

---

## 📂 Tables Overview

1. `Students(student_id, name, department)`
2. `Courses(course_id, course_name, max_marks)`
3. `Results(result_id, student_id, course_id, marks_obtained)`

All relationships are maintained using **foreign keys**.

---

## ✅ Features

- Add and view student records
- Add course details
- Insert marks for students
- Generate result reports
- Show student-wise or course-wise performance
- Calculate average marks, total marks, and highest scorers

---

## 🧪 Sample Queries Included

```sql
-- List all students with their marks
SELECT s.name, c.course_name, r.marks_obtained
FROM Students s
JOIN Results r ON s.student_id = r.student_id
JOIN Courses c ON r.course_id = c.course_id;

-- Total and average marks of each student
SELECT s.name, SUM(r.marks_obtained) AS total_marks, AVG(r.marks_obtained) AS average
FROM Students s
JOIN Results r ON s.student_id = r.student_id
GROUP BY s.name;

-- Highest scorer in each course
SELECT c.course_name, s.name AS topper, r.marks_obtained
FROM Results r
JOIN Students s ON r.student_id = s.student_id
JOIN Courses c ON r.course_id = c.course_id
WHERE (r.course_id, r.marks_obtained) IN (
    SELECT course_id, MAX(marks_obtained) FROM Results GROUP BY course_id
);
