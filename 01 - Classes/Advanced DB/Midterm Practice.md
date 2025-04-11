2025/03/12 16:14
Status: #idea
Tags:

# Midterm Practice

**Question 1:** A company database has a table called `employees` with columns `employee_id`, `first_name`, `last_name`, `department`, and `salary`. Write a query to retrieve the first and last names of all employees in the Marketing department who earn more than $60,000.

Answer: 
	SELECT first_name, last_name FROM employees WHERE salary > 60000

**Question 1A:** A company database has a table called `products` with columns `product_id`, `product_name`, `category`, `price`, and `stock_quantity`. Write a query to retrieve the names of all products in the "Electronics" category with a price less than $500 and stock quantity greater than 0.

Answer:
	```SELECT product_name
	FROM products
	WHERE category = 'Electronics'
	AND price < 500
	AND stock_quantity > 0;```


**Question 1B:** Using the same `employees` table from earlier (`employee_id`, `first_name`, `last_name`, `department`, `salary`, `hire_date`), write a query to find the average salary for each department, but only include departments that have more than 5 employees.

Answer:
	```SELECT department, AVG(salary) AS average_salary
	FROM employees
	GROUP BY department
	HAVING COUNT(*) > 5;
	```


**Question 2:** You have two tables: `students` (with columns `student_id`, `name`, `major`) and `courses` (with columns `course_id`, `course_name`, `instructor`). There's also a junction table called `enrollments` (with columns `student_id`, `course_id`, `semester`). Write a query to find all students who are enrolled in "Database Systems" for the "Fall 2024" semester.

Answer:
	```SELECT s.name, s.major
	FROM students s
	JOIN enrollments e ON s.student_id = e.student_id
	JOIN courses c ON e.course_id = c.course_id
	WHERE c.course_name = 'Database Systems'
	AND e.semester = 'Fall 2024';```

**Question 2A:** You have two tables: `customers` (with columns `customer_id`, `name`, `email`, `signup_date`) and `orders` (with columns `order_id`, `customer_id`, `order_date`, `total_amount`). Write a query to find all customers who have placed orders in both January 2024 and February 2024.

Answer:
	```SELECT c.name, c.email
	FROM customers c
	WHERE c.customer_id IN 
	(SELECT customer_id
	FROM orders
	WHERE order_date BETWEEN '2024-01-01' AND '2024-01-31')
	AND c.customer_id IN 
	(SELECT customer_id 
	FROM orders 
	WHERE order_date BETWEEN '2024-02-01' AND '2024-02-29');```



**Question 2B:** A library database has tables `books` (with columns `book_id`, `title`, `author_id`, `published_year`) and `authors` (with columns `author_id`, `author_name`, `nationality`). Write a query to retrieve the titles of all books written by American authors published after 2010.

Answer:

```
SELECT b.title
FROM books b
WHERE b.author_id IN 
(SELECT author_id
FROM authors
WHERE nationality = 'American')
AND b.published_year > 2010;
```

**Question 2C:** A school database contains tables `teachers` (with columns `teacher_id`, `name`, `subject`) and `classes` (with columns `class_id`, `teacher_id`, `room_number`, `grade_level`). Write a query to find the names of all teachers who teach both Math and Science subjects.

Answer:

```
SELECT t.name
FROM teachers t
WHERE t.subject IN ('Math', 'Science')
GROUP BY t.teacher_id, t.name
HAVING COUNT(DISTINCT t.subject) = 2;
```
## Medium Questions

**Question 3:** A retail database contains the tables `orders` (with columns `order_id`, `customer_id`, `order_date`, `total_amount`) and `order_items` (with columns `order_id`, `product_id`, `quantity`, `unit_price`). Write a query to find the top 3 customers who spent the most money in 2024, along with their total spending amount.

Answer:

```sql
SELECT o.customer_id, SUM(o.total_amount) AS total_spent
FROM orders o 
WHERE o.order_date BETWEEN '2024-01-01' AND '2024-12-31'
GROUP BY o.customer_id
ORDER BY total_spent DESC
LIMIT 3;
```

**Question 4:** A university database has tables `professors` (with columns `prof_id`, `name`, `department`) and `classes` (with columns `class_id`, `prof_id`, `course_name`, `semester`, `num_students`). Write a query to find the professor who taught the highest total number of students across all their classes in the Spring 2024 semester.

Answer: 

```sql
SELECT p.name
FROM professors p
WHERE p.prof_id = 
(SELECT prof_id
FROM classes
WHERE semester = 'Spring 2024'
GROUP BY prof_id
ORDER BY SUM(num_students) DESC
LIMIT 1);
```

**Question 4A:** A hospital database has tables `patients` (with columns `patient_id`, `name`, `admission_date`, `discharge_date`, `department_id`) and `departments` (with columns `department_id`, `department_name`, `floor`). Write a query to find the department with the highest average patient stay duration (in days) in 2024, along with that average duration.

Answer:

```
SELECT d.department_name
FROM 
```
## More Challenging Questions

**Question 5:** A social media database has tables `users` (with columns `user_id`, `username`, `join_date`), `posts` (with columns `post_id`, `user_id`, `post_date`, `content`), and `likes` (with columns `user_id`, `post_id`, `like_date`). Write a query to find users who have never received a like on any of their posts but have liked at least 5 posts from other users.

**Question 6:** An e-commerce database has tables `products` (with columns `product_id`, `name`, `category`, `price`), `customers` (with columns `customer_id`, `name`, `email`), and `purchases` (with columns `purchase_id`, `customer_id`, `product_id`, `purchase_date`, `quantity`). Write a query to find pairs of products that are frequently purchased together (in the same month by the same customer) at least 10 times.




---
# References
