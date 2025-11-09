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
*Paste or attach your diagram here*  
<img width="784" height="496" alt="image" src="https://github.com/user-attachments/assets/ddbed31a-600b-47c6-b174-9ecba8da8387" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| Member |id(pk),name,type    |       |
|Fitness | Payment , Salary   |       |
 Gym                         |       |
|Program |  Name ,seats       |       |
|        |                    |       |

### Relationships and Constraints

| **Relationship**                                | **Cardinality** | **Participation**             | **Notes**                                            |
| ----------------------------------------------- | --------------- | ----------------------------- | ---------------------------------------------------- |
| Details (Member – Fitness Gym)                  | M:N             | Partial                       | Includes attribute *date*                            |
| Enroll (Member – Fitness Program)               | M:N             | Partial                       | A member can enroll in multiple programs             |
| Course Offering (Fitness Gym – Fitness Program) | 1:M             | Total on Fitness Program side | Each program is offered by one gym                   |
| Details (Trainer – Fitness Gym)                 | 1:1             | Total                         | Each trainer works in exactly one gym                |
| Train (Trainer – Fitness Program)               | M:N             | Partial                       | A trainer can train multiple programs and vice versa |


### Assumptions
- 
- 
- 

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
*Paste or attach your diagram here*  
<img width="827" height="395" alt="image" src="https://github.com/user-attachments/assets/eab0ad0c-3bd0-4c32-9e5a-e387a55d0ce3" />


### Entities and Attributes

| **Entity**  | **Attributes (PK, FK)**          | **Notes**                                                   |
| ----------- | -------------------------------- | ----------------------------------------------------------- |
| **Member**  | id **(PK)**, name                | Represents library members                                  |
| **Books**   | title **(PK)**, category, author | Each book has a unique title                                |
| **Library** | timing, dues                     | Manages library operations and rules                        |
| **Event**   | speakers                         | Events organized by the library, may include guest speakers |


### Relationships and Constraints

| **Relationship**            | **Cardinality** | **Participation**     | **Notes**                                                                             |
| --------------------------- | --------------- | --------------------- | ------------------------------------------------------------------------------------- |
| Borrow (Member – Books)     | M:1             | Partial               | A member can borrow multiple books, but each book is borrowed by one member at a time |
| Stores (Books – Library)    | M:1             | Total on Library side | Each book is stored in one library                                                    |
| Consists (Library – Rooms)  | 1:M             | Total on Rooms side   | A library consists of multiple rooms                                                  |
| Booked (Event – Rooms)      | M:N             | Partial               | Events can be held in multiple rooms and a room can host multiple events              |
| Organises (Library – Event) | 1:M             | Total on Event side   | A library organizes many events                                                       |
| Enroll (Member – Event)     | M:N             | Partial               | Members can enroll in multiple events                                                 |


### Assumptions
- 
- 
- 

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
*Paste or attach your diagram here*  
<img width="940" height="325" alt="image" src="https://github.com/user-attachments/assets/61a750f4-4006-49b5-adbe-5e4c4c1099a0" />


### Entities and Attributes

| **Entity**      | **Attributes (PK, FK)**                                                                   | **Notes**                                                            |
| --------------- | ----------------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| **Customer**    | CustomerID **(PK)**, Name, Phone                                                          | Represents customers who make reservations or place orders           |
| **Reservation** | ReservationID **(PK)**, Date, Time, NumberOfGuests, CustomerID **(FK)**, TableID **(FK)** | Links customers to reserved tables at a specific date and time       |
| **Table**       | TableID **(PK)**, Capacity                                                                | Each table has a fixed capacity for guests                           |
| **Order**       | OrderID **(PK)**, OrderTime, ReservationID **(FK)**, WaiterID **(FK)**                    | Represents orders placed during a reservation and served by a waiter |
| **Dish**        | DishID **(PK)**, Name, Price, CategoryID **(FK)**                                         | Represents menu items categorized by type                            |
| **Category**    | CategoryID **(PK)**, CategoryName                                                         | Classifies dishes (e.g., Starter, Main, Dessert)                     |
| **Bill**        | BillID **(PK)**, TotalAmount, ServiceCharge, OrderID **(FK)**                             | Contains payment details linked to a specific order                  |
| **Waiter**      | WaiterID **(PK)**, Name                                                                   | Represents staff serving the customers                               |


### Relationships and Constraints

| **Relationship**                     | **Cardinality** | **Participation**         | **Notes**                                                         |
| ------------------------------------ | --------------- | ------------------------- | ----------------------------------------------------------------- |
| **Makes (Customer – Reservation)**   | 1:M             | Total on Reservation side | Each customer can make multiple reservations                      |
| **AssignedTo (Reservation – Table)** | M:1             | Total on Reservation side | Each reservation is assigned to one table                         |
| **Has (Reservation – Order)**        | 1:M             | Total on Order side       | Each reservation can have multiple orders                         |
| **Contains (Order – Dish)**          | M:N             | Partial                   | Each order can include multiple dishes, with attribute *Quantity* |
| **BelongsTo (Dish – Category)**      | M:1             | Total on Dish side        | Each dish belongs to one category                                 |
| **Generates (Reservation – Bill)**   | 1:1             | Total                     | Each reservation generates exactly one bill                       |
| **Serves (Waiter – Reservation)**    | 1:M             | Total on Reservation side | Each waiter serves multiple reservations                          |


### Assumptions
- 
- 
- 

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
