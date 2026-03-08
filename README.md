# 💍 Wedding & Event Coordination Database System

A relational database system designed to manage wedding and event 
coordination operations, built as a final project for the 
Database Fundamentals course (CSC1393) at 
Kolej Profesional MARA (KPM) Indera Mahkota.

---

## 📋 What It Does

- Manage client registrations and event bookings
- Track event packages, venues, and pricing
- Handle vendor and supplier assignments per event
- Record payment transactions and outstanding balances
- Generate reports on event schedules and staff assignments
- Maintain full relational integrity across all tables

---

## 🗄️ Database Design

- **Database:** MySQL
- **Tables:** Clients, Events, Venues, Packages, Vendors, 
              Payments, Staff, Bookings
- **Normalization:** Designed up to Third Normal Form (3NF)
- **Relationships:** One-to-many and many-to-many with 
                     junction tables

---

## 📐 ER Diagram

> *(Add your ER Diagram image here — drag it into GitHub)*

---

## 📁 Project Structure
```
wedding-event-database/
│
├── schema.sql          # Table creation scripts (DDL)
├── data.sql            # Sample data insertion (DML)
├── queries.sql         # All SQL queries and reports
├── docs/
│   ├── er_diagram.png  # Entity Relationship Diagram
│   ├── report.docx     # Full project report
│   └── normalization.docx  # Normalization documentation
└── README.md
```

---

## 🛠️ How to Run

1. Make sure MySQL is installed (or use XAMPP / phpMyAdmin)
2. Open MySQL Workbench or your preferred SQL client
3. Run `schema.sql` first to create all tables
4. Run `data.sql` to insert sample data
5. Run `queries.sql` to test all queries
```sql
-- Quick start in MySQL:
SOURCE schema.sql;
SOURCE data.sql;
SOURCE queries.sql;
```

---

## 🔑 Key SQL Concepts Used

- **DDL** — CREATE, ALTER, DROP for database structure
- **DML** — INSERT, UPDATE, DELETE for data management
- **DQL** — SELECT with JOIN, WHERE, GROUP BY, ORDER BY
- **Constraints** — PRIMARY KEY, FOREIGN KEY, NOT NULL, UNIQUE
- **Normalization** — 1NF → 2NF → 3NF to eliminate redundancy
- **Aggregate Functions** — COUNT, SUM, AVG for reporting

---

## 📊 Sample Queries
```sql
-- View all upcoming events with client details
SELECT e.event_id, c.client_name, e.event_date, 
       v.venue_name, p.package_name
FROM Events e
JOIN Clients c ON e.client_id = c.client_id
JOIN Venues v ON e.venue_id = v.venue_id
JOIN Packages p ON e.package_id = p.package_id
WHERE e.event_date >= CURDATE()
ORDER BY e.event_date ASC;

-- Total revenue per month
SELECT MONTH(payment_date) AS month, 
       SUM(amount) AS total_revenue
FROM Payments
WHERE YEAR(payment_date) = YEAR(CURDATE())
GROUP BY MONTH(payment_date)
ORDER BY month;
```

---

## 📚 What I Learned

- Designing a full relational database from requirements
- Applying normalization from 0NF all the way to 3NF
- Writing complex SQL queries using multiple JOINs
- Maintaining referential integrity with foreign key constraints
- Thinking about real-world data relationships and business logic
- Documenting a database system professionally

---

## 👤 Author

**Muhammad Irfan**  
Diploma in Computer Science  
Kolej Profesional MARA Indera Mahkota, Kuantan  
🐙 [github.com/irfanzamizi-prog](https://github.com/irfanzamizi-prog)
