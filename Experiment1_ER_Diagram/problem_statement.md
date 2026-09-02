# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
<img width="1430" height="1075" alt="WhatsApp Image 2026-09-01 at 18 58 49" src="https://github.com/user-attachments/assets/6bc3c1aa-63c3-4afa-a72f-04701ebe3606" />


### Entities and Attributes
<img width="1536" height="1167" alt="WhatsApp Image 2026-09-01 at 19 26 18" src="https://github.com/user-attachments/assets/d9119498-fc1a-438b-95a4-5e39b8187238" />

### Relationships and Constraints
<img width="1600" height="812" alt="WhatsApp Image 2026-09-01 at 20 29 35" src="https://github.com/user-attachments/assets/df63c56f-a4ae-4cce-9af8-d1117ebab7d7" />

### Assumptions
Each member has a unique Member_ID.
A member can enroll in more than one fitness program.
Each session is conducted by at least one trainer.
A payment belongs to exactly one member.
Attendance is recorded for booked/attended sessions.

---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:

<img width="1484" height="832" alt="WhatsApp Image 2026-09-01 at 18 58 50" src="https://github.com/user-attachments/assets/d2a21b14-32b7-43b1-8d1a-8e4f3e09b73d" />

### Entities and Attributes
<img width="1402" height="751" alt="WhatsApp Image 2026-09-01 at 19 26 19" src="https://github.com/user-attachments/assets/edaf0a12-346c-4be1-8254-34e83b8c8409" />


### Relationships and Constraints
<img width="1600" height="716" alt="WhatsApp Image 2026-09-01 at 20 29 36" src="https://github.com/user-attachments/assets/71a319ba-ccdb-4b3a-9e53-6c6fa4deeb1b" />



### Assumptions
Every member has a unique Member_ID.
A member can borrow multiple books.
A book can be borrowed by different members at different times.
An event can have one or more speakers.
Each event is organized by one library.
A room belongs to one library.
An overdue fee is generated only when a book is returned late.
---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
<img width="1536" height="995" alt="WhatsApp Image 2026-09-01 at 18 58 50 (1)" src="https://github.com/user-attachments/assets/2b7de3f3-69d3-4ad1-a8fa-e3e7a02fb812" />

### Entities and Attributes
<img width="1316" height="864" alt="WhatsApp Image 2026-09-01 at 19 26 19 (1)" src="https://github.com/user-attachments/assets/620f8bb4-9621-4cfb-9d86-6ca0dfbff123" />

### Relationships and Constraints
<img width="1403" height="650" alt="WhatsApp Image 2026-09-01 at 20 29 36 (1)" src="https://github.com/user-attachments/assets/7007901e-b435-4d25-8cd9-d81f0daddba5" />


### Assumptions
Each customer has a unique Customer_ID.
A customer can make multiple reservations.
Each reservation has a specified date, time and number of guests.
An order can contain multiple dishes.
A dish can appear in multiple orders.
Each bill is associated with one reservation.
A waiter can serve multiple reservations.
Service charge is included in the final bill.

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
