# StudentHub Portal

A full-stack student portal built step by step across 15 practicals for ITUE203 - Web Development Frameworks

Students can register, log in, browse events and register for them. Admins manage students and events, use a JSON API with AJAX, and monitor everything from a dashboard with an audit log.



## Features

Public
- Responsive pages built with semantic HTML5, CSS Grid and Flexbox (mobile, tablet, desktop)
- Home slider, notification banner, hamburger menu, FAQ accordion, popup modal
- Light / dark theme, remembered with localStorage
- Contact and feedback forms processed by PHP and stored in CSV files
- Data Explorer: JSON loaded with the Fetch API, with search, filter, sort and pagination

Students
- Secure registration (client and server validation, password strength meter, duplicate email check, password_hash())
- Login / logout with sessions, 30-minute inactivity timeout
- Dashboard, profile, event registration, attendance, assignments, results, timetable, notices

Admin
- Role-based access control (RBAC) and a dynamic menu
- Student CRUD with search, filter, pagination and delete confirmation
- Event CRUD with poster upload (type and size validation)
- JSON API (api/students.php) with fetch-based CRUD, no page reload
- Dashboard with live statistics, latest registrations and an audit log

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML5, CSS3, JavaScript (ES6) |
| Backend | PHP 8 (MySQLi, prepared statements) |
| Database | MySQL / MariaDB |
| Server | Apache (WAMP / XAMPP) |
| Tools | VS Code, Git, GitHub, phpMyAdmin |

---

## Getting Started

### Requirements
- WAMP or XAMPP (Apache + PHP 8 + MySQL)
- A modern browser

### Installation
1. Clone or download this repository.
   bash
   git clone <your-repository-url>
   
2. Copy the project folder into your server folder:
   - WAMP: C:\wamp64\www\ (or D:\wamp64\www\)
   - XAMPP: C:\xampp\htdocs\
3. Start Apache and MySQL.
4. Open phpMyAdmin (http://localhost/phpmyadmin), choose Import, select sql/studenthub.sql and click Import.
   > This creates a database named studenthub with sample data. If a database with that name already exists, it is replaced.
5. Open the site in your browser:
   
   http://localhost/<folder-name>/
   The site detects its own URL, so the folder name can be anything.

Database settings
Edit includes/db.php if your MySQL user or password is not the default (root with an empty password).

 Demo accounts

| Role | Email | Password |
|---|---|---|
| Admin | admin@studenthub.local | Admin@123 |
| Student | student@studenthub.local | Student@123 |

These are sample accounts for local testing only.

---
 Project Structure

StudentHub/
├── index.php, about.php, events.php, faq.php, contact.php, feedback.php
├── register.php, login.php, logout.php, dashboard.php, profile.php
├── timetable.php, notices.php, attendance.php, assignments.php, results.php
├── explorer.php                 JSON explorer (Fetch API)
├── admin/
│   ├── index.php                admin dashboard + audit log
│   ├── students.php             student CRUD
│   ├── events.php               event CRUD + poster upload
│   └── ajax-students.php        AJAX student management
├── api/students.php             JSON API
├── includes/                    db.php, auth.php, header.php, footer.php
├── assets/                      css/style.css, js/main.js, validation.js, explorer.js, students-ajax.js
├── data/                        events.json, notices.json, profiles.json, faqs.json
├── storage/                     CSV files written by the contact and feedback forms
├── uploads/posters/             event posters
├── sql/studenthub.sql           database schema and sample data
└── docs/test-report.md          test cases


---

 Security Highlights
- Passwords stored with password_hash() and checked with password_verify()
- MySQLi prepared statements for all database queries
- Output escaped with htmlspecialchars() to prevent XSS
- Session ID regenerated after login, HttpOnly cookies, inactivity timeout
- Server-side validation of every form, plus client-side validation for usability
- Poster uploads checked for real image type and size, renamed, and PHP execution blocked in uploads/
- Admin pages and the API restricted by role

---
Testing
---
Test cases for navigation, responsiveness, authentication, CRUD, uploads, AJAX and the dashboard are listed in [docs/test-report.md](docs/test-report.md).

---

Author
---
Mann Mahant
Subject: ITUE203 Web Development Frameworks

---

License
---
Created for educational purposes as part of university coursework.
