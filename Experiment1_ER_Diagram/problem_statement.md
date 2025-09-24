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
<img width="1536" height="1024" alt="er diagram for senario 1" src="https://github.com/user-attachments/assets/05bc6a27-d6db-40a8-9aae-6fe4eb6d6049" />


### Entities and Attributes

| Entity               | Attributes (PK, FK)                                                                      | Notes                                              |
| -------------------- | ---------------------------------------------------------------------------------------- | -------------------------------------------------- |
| **MEMBER**           | MemberID (PK), Name, MembershipType, StartDate                                           | Stores gym members.                                |
| **PROGRAM**          | ProgramID (PK), ProgramName, Category (Yoga, Zumba, Weight Training)                     | Fitness programs offered.                          |
| **TRAINER**          | TrainerID (PK), Name, Specialization                                                     | Trainers managing programs or sessions.            |
| **PROGRAM\_TRAINER** | ProgramID (FK), TrainerID (FK)                                                           | Resolves many-to-many between PROGRAM and TRAINER. |
| **MEMBER\_PROGRAM**  | MemberID (FK), ProgramID (FK), EnrollmentDate                                            | Resolves many-to-many between MEMBER and PROGRAM.  |
| **SESSION**          | SessionID (PK), MemberID (FK), TrainerID (FK), SessionDate, SessionType (Personal/Group) | Represents personal training bookings or sessions. |
| **ATTENDANCE**       | AttendanceID (PK), SessionID (FK), MemberID (FK), Status (Present/Absent)                | Tracks member participation in sessions.           |
| **PAYMENT**          | PaymentID (PK), MemberID (FK), Amount, PaymentDate, PaymentType (Membership/Session)     | Tracks payments by members.                        |


### Relationships and Constraints

| Relationship                         | Cardinality                                              | Participation      | Notes                                                                                                      |
| ------------------------------------ | -------------------------------------------------------- | ------------------ | ---------------------------------------------------------------------------------------------------------- |
| MEMBER – MEMBER\_PROGRAM – PROGRAM   | M\:N                                                     | Total (Mandatory)  | A member can enroll in many programs; programs can have many members.                                      |
| PROGRAM – PROGRAM\_TRAINER – TRAINER | M\:N                                                     | Partial (Optional) | A program may have multiple trainers; a trainer can manage many programs.                                  |
| MEMBER – SESSION – TRAINER           | M\:N (via SESSION)                                       | Partial            | A session links one trainer and one member, but trainers can have multiple sessions with multiple members. |
| SESSION – ATTENDANCE – MEMBER        | 1\:M (Session to Attendance), M:1 (Member to Attendance) | Mandatory          | Records which members attended each session.                                                               |
| MEMBER – PAYMENT                     | 1\:M                                                     | Mandatory          | A member can make multiple payments; each payment is linked to one member.                                 |


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
<img width="1536" height="1024" alt="er diagram for senario 2" src="https://github.com/user-attachments/assets/0f98d887-acca-4308-b758-48a08c3bf459" />


### Entities and Attributes

| Attribute      | Data Type | Key Type |
| -------------- | --------- | -------- |
| MemberID       | INT       | PK       |
| Name           | VARCHAR   | -        |
| Phone          | VARCHAR   | -        |
| Email          | VARCHAR   | -        |
| MembershipDate | DATE      | -        |
| --------- | --------- | -------- |
| BookID    | INT       | PK       |
| Title     | VARCHAR   | -        |
| Author    | VARCHAR   | -        |
| Category  | VARCHAR   | -        |

| ---------- | --------- | -------------------- |
| LoanID     | INT       | PK                   |
| MemberID   | INT       | FK → MEMBER.MemberID |
| BookID     | INT       | FK → BOOK.BookID     |
| LoanDate   | DATE      | -                    |
| DueDate    | DATE      | -                    |
| ReturnDate | DATE      | -                    |
| FineAmount | DECIMAL   | -                    |

| --------- | --------- | -------- |
| RoomID    | INT       | PK       |
| RoomName  | VARCHAR   | -        |
| Capacity  | INT       | -        |
| RoomType  | VARCHAR   | -        |

| --------- | --------- | ---------------- |
| EventID   | INT       | PK               |
| EventName | VARCHAR   | -                |
| EventDate | DATE      | -                |
| RoomID    | INT       | FK → ROOM.RoomID |

| --------- | --------- | -------- |
| SpeakerID | INT       | PK       |
| Name      | VARCHAR   | -        |
| Bio       | TEXT      | -        |

| ----------------------------- | --------- | ---------------------- |
| EventID                       | INT       | FK → EVENT.EventID     |
| SpeakerID                     | INT       | FK → SPEAKER.SpeakerID |
| **PK = (EventID, SpeakerID)** |           |                        |

| ---------------- | --------- | -------------------- |
| RegistrationID   | INT       | PK                   |
| EventID          | INT       | FK → EVENT.EventID   |
| MemberID         | INT       | FK → MEMBER.MemberID |
| RegistrationDate | DATE      | -                    |



### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

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


### Entities and Attributes

| Entity          | Attributes (PK, FK)                                                                                                                       | Notes                                         |
| --------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------- |
| **CUSTOMER**    | CustomerID (PK), Name, Phone, Email                                                                                                       | Stores customer details.                      |
| **TABLE**       | TableID (PK), Capacity, Location                                                                                                          | Represents physical restaurant tables.        |
| **RESERVATION** | ReservationID (PK), CustomerID (FK), TableID (FK), ReservationDate, ReservationTime, NumGuests, Type (Reservation/Walk-in), WaiterID (FK) | Tracks table bookings or walk-ins.            |
| **WAITER**      | WaiterID (PK), Name, Shift                                                                                                                | Waiters serving reservations.                 |
| **ORDER**       | OrderID (PK), ReservationID (FK), OrderTime                                                                                               | Food orders linked to a reservation.          |
| **DISH**        | DishID (PK), DishName, Price, CategoryID (FK)                                                                                             | Food menu items.                              |
| **CATEGORY**    | CategoryID (PK), CategoryName (Starter, Main, Dessert, Beverage)                                                                          | Groups dishes.                                |
| **ORDER\_ITEM** | OrderID (FK), DishID (FK), Quantity                                                                                                       | Resolves many-to-many between ORDER and DISH. |
| **BILL**        | BillID (PK), ReservationID (FK), BillDate, FoodAmount, ServiceCharge, TotalAmount                                                         | Final billing per reservation.                |

### Relationships and Constraints

| Relationship               | Cardinality                  | Participation | Notes                                                                               |
| -------------------------- | ---------------------------- | ------------- | ----------------------------------------------------------------------------------- |
| CUSTOMER – RESERVATION     | 1\:M                         | Mandatory     | A customer can have many reservations; each reservation belongs to one customer.    |
| TABLE – RESERVATION        | 1\:M                         | Mandatory     | A table can be booked many times; each reservation is for one table.                |
| RESERVATION – WAITER       | 1\:M (Waiter to Reservation) | Optional      | A waiter may serve multiple reservations; each reservation is served by one waiter. |
| RESERVATION – ORDER        | 1\:M                         | Mandatory     | Each reservation may have multiple food orders.                                     |
| ORDER – ORDER\_ITEM – DISH | M\:N                         | Mandatory     | Orders can contain multiple dishes; dishes appear in many orders.                   |
| DISH – CATEGORY            | M:1                          | Mandatory     | Each dish belongs to one category.                                                  |
| RESERVATION – BILL         | 1:1                          | Mandatory     | Each reservation generates exactly one bill.                                        |


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
