# Scalable Multi-Threaded Course Registration System

A concurrent client-server based academic course registration system developed in C using POSIX sockets, Pthreads, synchronization primitives, and low-level Linux file system operations.

---

## Overview

This project simulates a university course registration portal where multiple users can concurrently access and modify course information through a centralized server.

The system supports three user roles:

- Administrator
- Faculty
- Student

and provides functionalities for user management, course management, enrollment handling, and persistent data storage.

The primary objective of the project is to demonstrate Operating Systems concepts such as:

- Multi-threading
- Synchronization
- Inter-Process Communication
- File Management
- Concurrency Control
- Client-Server Architecture

---

## System Architecture

```text
Client Applications
        │
        ▼
POSIX Socket Connection
        │
        ▼
Multi-Threaded Server
        │
 ┌──────┼──────┐
 ▼      ▼      ▼
Students Faculty Admin
        │
        ▼
Persistent Binary Storage
```

Each client connection is served by an independent worker thread, allowing multiple users to interact with the system simultaneously.

---

## Key Operating Systems Concepts

### Multi-Threading

- Implemented using POSIX Threads (Pthreads)
- Each client connection is handled by a dedicated thread
- Detached thread model used for automatic cleanup

### Synchronization

Thread-safe operations are implemented using mutex locks:

- Student database lock
- Faculty database lock
- Course management lock

These locks prevent race conditions during concurrent enrollment and course updates.

### Socket Programming

Implemented using:

- socket()
- bind()
- listen()
- accept()
- connect()

The server continuously listens for incoming client requests and serves them concurrently.

### File Management

Persistent storage is implemented using Linux system calls:

- open()
- read()
- write()
- lseek()

Data is stored in binary files and preserved across server restarts.

### Signal Handling

Graceful server termination is implemented using:

- SIGINT handling
- Resource cleanup
- Mutex destruction

---

## Features

### Administrator

- Add Student
- Add Faculty
- Activate Student Account
- Deactivate Student Account
- Update Student Details
- Update Faculty Details

### Faculty

- Add New Courses
- Remove Courses
- View Course Enrollments
- Change Password

### Student

- Enroll in Courses
- Unenroll from Courses
- View Registered Courses
- Change Password

---

## System Demonstration

### Server Startup

![Server Startup](screenshots/server_startup.png)

### Administrator Management

![Admin Operations](screenshots/admin_user_management.png)

### Faculty Course Creation

![Faculty Operations](screenshots/faculty_add_course.png)

### Student Enrollment

![Student Enrollment](screenshots/student_course_enrollment.png)

### Student Registered Courses

![Student Courses](screenshots/student_view_courses.png)

### Faculty Enrollment Tracking

![Faculty Enrollments](screenshots/faculty_view_enrollments.png)

## Persistent Storage

The system maintains three binary files:

| File | Purpose |
|--------|--------|
| admin.dat | Administrator credentials |
| students.dat | Student information and enrollments |
| faculty.dat | Faculty information and course offerings |

---

## Concurrency Control

The system safely supports multiple concurrent clients by protecting critical sections using mutex locks.

Examples:

- Multiple students enrolling simultaneously
- Faculty updating courses during enrollment
- Administrator modifying records while users are active

---

## Technologies Used

- C Programming
- Linux
- POSIX Sockets
- POSIX Threads (Pthreads)
- Synchronization Primitives
- File Systems
- TCP/IP Networking

---

## Build Instructions

Compile Server

```bash
gcc server.c -o server -lpthread
```

Compile Client

```bash
gcc client.c -o client
```

Run Server

```bash
./server
```

Run Client

```bash
./client
```

---

## Learning Outcomes

- Concurrent server design
- Thread synchronization
- Race condition prevention
- Socket programming
- Binary file handling
- Client-server communication
- Operating system resource management

---

## Repository Structure

```text
src/
├── server.c
└── client.c

docs/
└── Project_Report.pdf

screenshots/

data/
└── DATA_FILES.md
```

---

## Authors

Rishik Patha

International Institute of Information Technology Bangalore (IIIT-B)