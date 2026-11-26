# CampusLib – Smart College Library Management System

**Capstone Project | CSA0206 – C Programming**
SIMATS Engineering, Saveetha Institute of Medical and Technical Sciences, Chennai – 602105

CampusLib is a web-based library management system that organises books, users and circulation activities for a college library. Students search and reserve books, librarians manage inventory, borrowing and returns, and administrators oversee users and reports.

---

## Team

| Name | Reg. No. | Department | Contribution |
|---|---|---|---|
| Harshan K | 1911260183 | Computer Science and Engineering | 40% |
| Mathavan K | 1972260068 | Computer Science and Engineering | 30% |
| Ravinder R | 192312230 | Electronics and Communication Engineering | 30% |

- **Guide:** Balachandran M
- **Course Coordinator:** Dr. M. Shakila

---

## Features

- Registration, login and role-based access (Student, Librarian, Administrator)
- Book and copy management: add, update, search
- Circulation: issue, return and borrowing history
- Reservations: queue requests for unavailable books
- Overdue tracking, fine calculation and reports
- Administration: user management, permissions and audit logs

## Architecture

```
User  →  Frontend (HTML • CSS • JS)  →  C Backend (Mongoose • C APIs)  →  MySQL
Request → Validation → Business logic → SQL query → JSON response
```

## Tech Stack

| Layer | Technology |
|---|---|
| Backend | C (ANSI C), Mongoose embedded web server, MySQL C API, cJSON |
| Frontend | HTML, CSS, JavaScript |
| Database | MySQL |

## Modules

| Module | Purpose |
|---|---|
| Authentication | Login, registration, role checks |
| Book Management | Add, update, search, manage copies |
| Circulation | Issue, return, borrowing history |
| Reservations | Queue requests for unavailable books |
| Fines & Reports | Overdue calculation, usage summaries |
| Administration | Users, permissions, audit logs |

## Database Design

| Table | Key fields |
|---|---|
| `users` | user_id, name, email, role |
| `books` | book_id, title, author, category |
| `book_copies` | copy_id, book_id (FK), barcode, status |
| `borrowings` | user_id, copy_id, issue, due, return |
| `reservations` | user_id, book_id, queue status |
| `fines` / `audit` | amount, payment status, activity log |

Primary and foreign keys maintain relationships and data integrity.

## Security

- Password hashing for stored credentials
- Server-side role-based authorisation
- Prepared SQL statements to prevent SQL injection
- Input validation and secure sessions
- HTTPS, backups and audit logs

---

## Getting Started

> Adjust the folder names and commands below to match your repository.

### Prerequisites

- GCC (or any C compiler) and `make`
- MySQL Server and the MySQL C client library (development headers)
- Mongoose (`mongoose.c`, `mongoose.h`) and cJSON (`cJSON.c`, `cJSON.h`) in the backend source folder
- A modern web browser

### 1. Set up the database

```bash
mysql -u <user> -p -e "CREATE DATABASE campuslib;"
mysql -u <user> -p campuslib < database/schema.sql
```

### 2. Configure the backend

Set the database host, user, password and database name in the backend configuration (or environment variables). Do not commit real credentials.

### 3. Build and run the backend

```bash
cd backend
make
./campuslib_server
```

### 4. Open the frontend

Open the frontend in your browser at the address the server prints (for example `http://localhost:8000`).

---

## Project Structure (suggested)

```
CampusLib/
├── backend/        # C source: Mongoose server, modules, MySQL access
├── frontend/       # HTML, CSS, JavaScript pages
├── database/       # schema.sql and sample data
├── docs/           # report and presentation
└── README.md
```

## Success Criteria

- Users can sign in with the correct role
- Books and copies are stored and searchable
- Borrowing and returns update copy status
- Due dates and fines can be tracked
- Reports summarise library activity

## References

1. E. Balagurusamy, *Programming in ANSI C*
2. MySQL Reference Manual – https://dev.mysql.com/doc/
3. Mongoose Embedded Web Server – https://mongoose.ws
4. cJSON library – https://github.com/DaveGamble/cJSON
