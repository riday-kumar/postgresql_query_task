# Online Course Enrollment Database

## TABLE CREATIONS.

### There are 3 tables : learners, courses, enrollments

## Table 1 : learners

### This table will store learners information with the following columns:

- `learner_id` : Integer, primary key
- `first_name` : Text field (max 50 characters)
- `last_name` : Text field (max 50 characters)
- `email` : Text field (max 100 characters)
- `phone` : Text field (max 20 characters)
- `country` : Text field (max 50 characters)
- `enrollment_date` : Date field

<hr>

## Table 2 : courses

### This table should store course information with the following columns:

- `course_id` : Integer, primary key
- `course_title` : Text field (max 150 characters)
- `category` : Text field (max 50 characters)
- `price` : Decimal number (10 digits total, 2 after decimal point)
- `instructor` : Text field (max 100 characters)
- `publication_year` : Integer

<hr>

## Table 3 : enrollments

### This table should store enrollment information with the following columns:

- `enrollment_id` : Integer, primary key
- `learner_id` : Integer that references the students table
- `course_id` : Integer that references the courses table
- `enrollment_date` : Date field
- `progress_percentage` : Integer (NULL allowed)
- `paid_amount` : Decimal number (10 digits total, 2 after decimal point)

<br> <br>

## TABLE CREATIONS.

```
create table if not exists learners(
  learner_id int primary key,
  first_name varchar(50) not null,
  last_name varchar(50) not null,
  email varchar(100) not null,
  phone varchar(20),
  country varchar(50) not null,
  enrollment_date date
)



create table if not exists courses(
  course_id int primary key,
  course_title varchar(150) not null,
  category varchar(50) not null,
  price decimal(10,2) not null,
  instructor varchar(100) not null,
  published_year int
)


create table if not exists enrollments(
  enrollment_id int primary key,
  learner_id int references learners(learner_id) not null,
  course_id int references courses(course_id) not null,
  enrollment_date date not null,
  progress_percentage int,
  paid_amount decimal(10,2) not null
)
```

<br> <br>

## Insert Data into the tables

```
-- insert data to the learners table

insert into customers (customer_id, first_name, last_name, email, city, country, registration_date)
values
(1, 'John', 'Smith', 'john.smith@email.com', 'New York', 'USA', '2023-01-15'),
(2, 'Emma', 'Johnson', 'emma.j@email.com', 'London', 'UK', '2023-02-20'),
(3, 'Michael', 'Brown', 'mbrown@email.com', 'Toronto', 'Canada', '2023-01-10'),
(4, 'Sophia', 'Davis', 'sophia.d@email.com', 'Sydney', 'Australia', '2023-03-05'),
(5, 'James', 'Wilson', 'jwilson@email.com', 'New York', 'USA', '2023-02-28'),
(6, 'Oliver', 'Taylor', 'oliver.t@email.com', 'London', 'UK', '2023-04-12'),
(7, 'Ava', 'Anderson', 'ava.anderson@email.com', 'Los Angeles', 'USA', '2023-03-18'),
(8, 'William', 'Martinez', 'w.martinez@email.com', 'Madrid', 'Spain', '2023-01-25'),
(9, 'Isabella', 'Garcia', 'isabella.g@email.com', 'Mexico City', 'Mexico', '2023-02-14'),
(10, 'Lucas', 'Rodriguez', 'lucas.r@email.com', 'Buenos Aires', 'Argentina', '2023-03-30')
```

```
-- insert data to the books table
insert into books(book_id, title, author, genre, price, publication_year, stock_quantity)
values
(1, 'The Great Gatsby', 'F. Scott Fitzgerald', 'Fiction', 12.99, 1925, 45),
(2, 'To Kill a Mockingbird', 'Harper Lee', 'Fiction', 14.99, 1960, 32),
(3, '1984', 'George Orwell', 'Science Fiction', 13.99, 1949, 28),
(4, 'Pride and Prejudice', 'Jane Austen', 'Romance', 11.99, 1813, 50),
(5, 'The Catcher in the Rye', 'J.D. Salinger', 'Fiction', 12.99, 1951, 22),
(6, 'Harry Potter and the Sorcerer Stone', 'J.K. Rowling', 'Fantasy', 19.99, 1997, 60),
(7, 'The Hobbit', 'J.R.R. Tolkien', 'Fantasy', 15.99, 1937, 38),
(8, 'Brave New World', 'Aldous Huxley', 'Science Fiction', 13.99, 1932, 25),
(9, 'The Lord of the Rings', 'J.R.R. Tolkien', 'Fantasy', 29.99, 1954, 41),
(10, 'Animal Farm', 'George Orwell', 'Fiction', 10.99, 1945, 55),
(11, 'Fahrenheit 451', 'Ray Bradbury', 'Science Fiction', 12.99, 1953, 30),
(12, 'The Great Adventure', 'John Anderson', 'Fiction', 16.99, 2020, 18),
(13, 'Mystery in Paris', 'Marie Dubois', 'Mystery', 14.99, 2019, 27),
(14, 'Romance in Rome', 'Isabella Rossi', 'Romance', 13.99, 2021, 35);
```

```
-- insert data to the orders table
insert into orders(order_id, customer_id, book_id, order_date, quantity, total_amount)
values
(1, 1, 1, '2023-05-10', 2, 25.98),
(2, 1, 6, '2023-05-15', 1, 19.99),
(3, 2, 3, '2023-05-12', 1, 13.99),
(4, 3, 2, '2023-05-11', 3, 44.97),
(5, 4, 7, '2023-05-13', 1, 15.99),
(6, 5, 9, '2023-05-14', 2, 59.98),
(7, 2, 4, '2023-05-16', 1, 11.99),
(8, 6, 6, '2023-05-17', 2, 39.98),
(9, 7, 1, '2023-05-18', 1, 12.99),
(10, 8, 8, '2023-05-19', 1, 13.99),
(11, 1, 10, '2023-06-01', 2, 21.98),
(12, 3, 5, '2023-06-02', 1, 12.99),
(13, 9, 11, '2023-06-03', 3, 38.97),
(14, 10, 12, '2023-06-04', 1, 16.99),
(15, 4, 13, '2023-06-05', 2, 29.98),
(16, 5, 14, '2023-06-06', 1, 13.99),
(17, 2, 6, '2023-06-07', 1, 19.99),
(18, 7, 3, '2023-06-08', 2, 27.98)
```

## Queries

- Display all learners and their phone numbers.
  If the phone number is NULL, show 'Not Provided' using COALESCE.

```
select (first_name|| ' ' ||last_name) as full_name,
 coalesce(phone, 'Not Provided') as phone
from learners;
```

- Show all courses ordered by price (highest to lowest) and limit the result to 5 courses.

```
select * from courses
order by price desc
limit 5  offset 0
```

- Display courses for page 2, assuming 3 courses per page, using LIMIT and OFFSET.

```
select * from courses
limit 3  offset (2 - 1) * 3
```

- Update the price of all courses in the Programming category by increasing it 10%.

```
update courses
set price = price + (price * 0.1)
where category = 'Programming'
```

- Delete all enrollment records where progress_percentage is NULL.

```
delete from enrollments
where progress_percentage is null
```

- Find the total paid amount per course category using GROUP BY.

```

select c.category, sum(paid_amount) as "total paid amount"
from enrollments as e
  inner join courses as c on c.course_id = e.course_id
  group by c.category
```

- Show course categories where the average course price is greater than 60 using HAVING.

```
select category, avg(price) as "average course price"
from courses
group by category
having avg(price) > 60
```

- Count how many students are enrolled in each course.

```
select count(learner_id) as "enrolled students" ,
c.course_title from courses as c
left join enrollments as e
on c.course_id = e.course_id
group by c.course_title
order by c.course_title
```

- Display student full name, course title, and paid amount using an INNER JOIN.

```
select (l.first_name || ' ' || l.last_name) as "full name",
c.course_title, e.paid_amount from learners as l
inner join enrollments as e
on l.learner_id = e.learner_id
inner join courses as c
on e.course_id = c.course_id
```

- Display all students and their enrolled courses.
- Include students who have not enrolled in any course using a LEFT JOIN.

```
select first_name, last_name,course_title from learners as l
  left join enrollments as e
  on l.learner_id = e.learner_id
  left join courses as c
  on c.course_id = e.course_id
order by l.first_name desc
```

- Display all students and all courses, even if there is no matching enrollment, using a FULL JOIN.

```
select first_name, course_title as "enrolled courses" from learners
full join enrollments on  learners.learner_id = enrollments.learner_id
full join courses on courses.course_id = enrollments.course_id
```

- Show the number of enrollments per year based on enrollment_date.

```
select extract(year from enrollment_date) AS enrollment_year,count(*) from enrollments
group by extract(year from enrollment_date)
```
