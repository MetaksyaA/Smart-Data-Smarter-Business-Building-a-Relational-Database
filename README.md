# Aesthetic Center Database System

This repository contains the relational database structure and SQL queries for managing an aesthetic center's business operations. The schema is designed to handle services, clients, reservations, payments, sales, feedback, insurance, and more.

## Database Schema

The database schema consists of multiple interconnected tables representing various entities such as clients, services, specialists, reservations, sales, and insurance. The schema diagram provides a visual representation of these relationships.

### **[Interactive Database Diagram](https://dbdiagram.io/d/66d72fffeef7e08f0e90dc38)**

## Key Features

- **Client and Specialist Management**: Track client details, specialist availability, and appointments.
- **Service and Reservation Handling**: Manage services offered, client reservations, and associated specialists.
- **Sales and Payments**: Monitor sales, apply discounts, and track payments made by clients.
- **Insurance and Claims**: Handle insurance policies and claims associated with client appointments.
- **Feedback**: Collect and analyze feedback for services provided.

## SQL Queries

This project includes a series of SQL queries to help analyze business operations. Below are some key queries.

### 1. Reservations with Client, Service, Specialist, and Branch Details
```sql
SELECT
    r.reservation_id,
    CONCAT(c.first_name, ' ', c.last_name) AS client,
    srv.service_name,
    CONCAT(sp.first_name, ' ', sp.last_name) AS specialist,
    b.branch_name,
    r.reservation_date,
    r.reservation_time,
    r.reservation_status
FROM
    Reservations r
JOIN Clients c ON r.client_id = c.client_id
JOIN Services srv ON r.service_id = srv.service_id
JOIN Specialists sp ON r.specialist_id = sp.specialist_id
JOIN Branches b ON r.branch_id = b.branch_id
ORDER BY r.reservation_date DESC;


### 2. Client Feedback on Services
```sql

SELECT 
    f.feedback_id, 
    CONCAT(c.first_name, ' ', c.last_name) AS client,
    s.service_name, 
    CONCAT(sp.first_name, ' ', sp.last_name) AS specialist, 
    f.rating, 
    f.feedback_comments
FROM Feedbacks f
JOIN Clients c ON f.client_id = c.client_id
JOIN Services s ON f.service_id = s.service_id
JOIN Specialists sp ON f.specialist_id = sp.specialist_id;


## How to Use the Queries

### Clone the repository:
```bash
git clone https://github.com/yourusername/aesthetic-center-database.git


## Database Setup:
Ensure your database is set up according to the schema in the diagram. The schema includes tables like Clients, Services, Specialists, Reservations, Payments, and others.

## Run Queries:
Use a SQL client to run the queries. Modify the queries if needed based on your branch, date, or other specific data needs.

## Analyze Results:
The queries are designed to provide insight into different aspects of the business, such as reservation trends, client feedback, specialist availability, and financial summaries.

## Contribution
Feel free to contribute to this repository by forking it, making changes, and submitting a pull request. Contributions can include:

## Additional queries.
Improvements to the schema.
Bug fixes or performance optimizations.
