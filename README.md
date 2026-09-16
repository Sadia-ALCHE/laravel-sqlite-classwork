# Laravel + SQLite Classwork
## Student Management System

### Duration
1 Hour

### Objective

In this classwork, you will build a small **Student Management System** using Laravel and SQLite.

You will apply the concepts covered during the Laravel database session:

- Routes
- Controllers
- Models
- Migrations
- SQLite
- Eloquent ORM
- Blade
- GET and POST requests
- HTML forms
- CSRF protection

By the end of the classwork, your application should allow a user to:

1. View registered students
2. Open a student registration form
3. Register a new student
4. Store the student in SQLite
5. Display the saved student on the student list

---

# Scenario

The university needs a simple application for registering students.

Currently, the application does not have a student database.

Your task is to complete the application by connecting Laravel to SQLite and implementing the student registration feature.

---

# Getting Started

## 1. Clone/Fork the Repository

Fork this repository into your own GitHub account.

Then clone your fork:

```bash
git clone YOUR_REPOSITORY_URL
```

Move into the project:

```bash
cd laravel-sqlite-classwork
```

---

## 2. Install Dependencies

Run:

```bash
composer install
```

---

## 3. Create Your Environment File

Copy:

```text
.env.example
```

and create:

```text
.env
```

On Windows:

```bash
copy .env.example .env
```

On macOS/Linux:

```bash
cp .env.example .env
```

---

## 4. Generate the Application Key

Run:

```bash
php artisan key:generate
```

---

## 5. Configure SQLite

Open:

```text
.env
```

Make sure Laravel is configured to use SQLite.

The SQLite database should be located inside:

```text
database/
```

---

## 6. Start Laravel

Run:

```bash
php artisan serve
```

Open:

```text
http://127.0.0.1:8000
```

You should see the starter page.

---

# Your Task

You must complete the Student Management feature.

Your application must use the following flow:

```text
Browser
   ↓
Route
   ↓
Controller
   ↓
Model
   ↓
SQLite Database
   ↓
Controller
   ↓
Blade View
   ↓
Browser
```

---

# Part 1 — Student Database

Create a model named:

```text
Student
```

and create its migration.

The `students` table must contain the following fields:

| Field | Type |
|---|---|
| id | Primary Key |
| student_id | String |
| name | String |
| email | String |
| programme | String |
| created_at | Timestamp |
| updated_at | Timestamp |

After defining the table, run the appropriate Laravel command to create it in SQLite.

Do not create the table manually.

---

# Part 2 — Student Model

Configure the `Student` model so that the following fields can receive data:

```text
student_id
name
email
programme
```

Think about the Laravel property discussed during the database session that controls which fields may be filled.

---

# Part 3 — Student Controller

Create:

```text
StudentController
```

Your controller must contain three methods:

```text
index()
create()
store()
```

### index()

Retrieve all students from the database using Eloquent and send them to the student list view.

### create()

Display the student registration form.

### store()

Receive the information submitted by the registration form and create a new Student record using Eloquent.

After successfully registering a student, redirect the user to:

```text
/students
```

Do not use raw SQL.

---

# Part 4 — Routes

Your application must support the following routes:

| Method | URL | Purpose |
|---|---|---|
| GET | `/students` | Display all students |
| GET | `/students/create` | Display the registration form |
| POST | `/students` | Register a student |

Connect each route to the appropriate `StudentController` method.

---

# Part 5 — Student Registration Page

Create:

```text
resources/views/students/create.blade.php
```

The page must contain a form with the following fields:

### Student ID

Example:

```text
ST001
```

### Student Name

Example:

```text
Amina Johnson
```

### Email

Example:

```text
amina@example.com
```

### Programme

Example:

```text
Software Engineering
```

The form must submit its information using:

```text
POST
```

Remember Laravel's protection for forms that modify data.

---

# Part 6 — Student List

Create:

```text
resources/views/students/index.blade.php
```

The page must display all registered students in a table.

Example:

| Student ID | Name | Email | Programme |
|---|---|---|---|
| ST001 | Amina Johnson | amina@example.com | Software Engineering |
| ST002 | David Mensah | david@example.com | Computer Science |

The information displayed in the table must come from SQLite.

You must use Blade to loop through the students.

Hard-coded student records are not allowed.

---

# Part 7 — Navigation

Your application should allow the user to move between the two pages.

The Student List page must contain:

```text
Add Student
```

which takes the user to:

```text
/students/create
```

The registration page must contain:

```text
Back to Students
```

which takes the user back to:

```text
/students
```

---

# Part 8 — Test Your Application

Register at least **three students** using your application.

Do not insert the three students manually into SQLite.

After registration, verify that:

```text
/students
```

displays all three students.

Also inspect your SQLite database and confirm that the records exist inside the:

```text
students
```

table.

---

# Expected Application

## Student List

Your final page should look approximately like:

```text
--------------------------------------------------------

              STUDENT MANAGEMENT SYSTEM

                                      [ Add Student ]

--------------------------------------------------------

Student ID | Name           | Email              | Programme

ST001      | Amina Johnson  | amina@example.com  | Software Engineering

ST002      | David Mensah   | david@example.com  | Computer Science

ST003      | Sarah Williams | sarah@example.com  | Software Engineering

--------------------------------------------------------
```

You may improve the design using CSS or Bootstrap.

However, functionality is more important than design.

---

## Registration Page

Your registration page should look approximately like:

```text
------------------------------------------------

              REGISTER STUDENT

Student ID
[_______________________________]

Student Name
[_______________________________]

Email
[_______________________________]

Programme
[_______________________________]


        [ Register Student ]


        Back to Students

------------------------------------------------
```

---

# Requirements

Your project must contain:

- Student Model
- Students Migration
- StudentController
- SQLite database connection
- GET `/students`
- GET `/students/create`
- POST `/students`
- Student list Blade view
- Student registration Blade view
- Eloquent for database operations
- CSRF protection
- At least three student records

---

# Restrictions

You must NOT:

- Hard-code students inside the Controller
- Hard-code students inside the Blade view
- Use raw SQL for retrieving or inserting students
- Create the `students` table manually
- Use phpMyAdmin/MySQL for this classwork
- Copy another student's repository

Use Laravel migrations and Eloquent.

---

# Testing Checklist

Before submitting, verify the following:

- [ ] Laravel starts without errors
- [ ] SQLite is configured
- [ ] Migration runs successfully
- [ ] `students` table exists
- [ ] `/students` opens successfully
- [ ] `/students/create` opens successfully
- [ ] Form submits successfully
- [ ] No 419 error occurs
- [ ] Student is stored in SQLite
- [ ] Student appears on `/students`
- [ ] At least three students have been registered
- [ ] Navigation works between the pages
- [ ] Code has been committed and pushed

---

# Troubleshooting

### 419 Page Expired

Check your form.

Laravel forms that modify data require CSRF protection.

---

### Class "App\Http\Controllers\Request" does not exist

Check whether the correct Request class has been imported into your controller.

---

### Mass Assignment Error

Check the configuration of your Model and the fields that Laravel is allowed to fill.

---

### Table Not Found

Check:

1. Your database configuration
2. Your migration
3. Whether your migration has been executed

You can inspect migration status using Laravel's Artisan commands.

---

### No Students Appear

First check whether records actually exist in SQLite.

Then check the flow:

```text
Route
   ↓
Controller
   ↓
Model
   ↓
Database
   ↓
Controller
   ↓
View
```

Do not immediately change everything. Identify which part of the flow is not working.

---

## Learning Goal

The goal is not to memorise Laravel commands.

The goal is to understand the pattern:

```text
Route → Controller → Model → Database → View
```

Once you understand this pattern, you can reuse it for:

- Courses
- Products
- Vehicles
- Patients
- Bookings
- Employees
- Rooms
- Inventory
- Orders

Good luck!
