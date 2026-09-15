# RabTech Task 02 – Business Rules to Executable Relational Model

## Project Overview

This project focuses on designing an order management database using PostgreSQL. It converts business requirements into an executable relational model with enforceable constraints and automated validation through SQL tests.

The project demonstrates how database integrity, business rules, and transaction-level validation can help maintain accurate and reliable order records.

## Objectives

* Design a relational database for customers and orders.
* Implement primary keys and foreign key relationships.
* Enforce business rules using SQL constraints.
* Validate cross-table date integrity using triggers.
* Prevent accidental deletion of customer order history.
* Test database rules using negative test cases.

## Technologies Used

* PostgreSQL
* SQL
* Relational Database Design
* Database Constraints and Triggers

## Database Design

The project includes two main entities:

**Customers:** Stores customer registration information.

**Orders:** Stores purchase information associated with customers.

One customer can have multiple orders, while each order must belong to exactly one customer.

## Business Rules Implemented

1. Every order must reference an existing customer.
2. Order status must be `PLACED`, `PAID`, or `CANCELLED`.
3. Order amount must be greater than or equal to zero.
4. An order date cannot precede the customer's registration date.
5. Customers with existing orders cannot be deleted.

## Project Structure

```text
rabtech-order-management/
├── docs/
│   ├── domain-brief.md
│   ├── rule-to-constraint-matrix.md
│   └── er-diagram.md
├── migrations/
│   ├── 001_init_schema.sql
│   └── 002_temporal_integrity_trigger.sql
├── fixtures/
│   ├── commerce-seed-data.sql
│   └── 003_seed_fixtures.sql
├── tests/
│   └── negative_tests.sql
└── README.md
```

## How to Run the Project

### Prerequisites

Install PostgreSQL and ensure that the `createdb` and `psql` commands are available.

### Setup

Create the database:

```bash
createdb rabtech_order_management
```

Run the database migrations:

```bash
psql -d rabtech_order_management -f migrations/001_init_schema.sql
psql -d rabtech_order_management -f migrations/002_temporal_integrity_trigger.sql
```

Load the sample data:

```bash
psql -d rabtech_order_management -f fixtures/003_seed_fixtures.sql
```

Run the validation tests:

```bash
psql -d rabtech_order_management -f tests/negative_tests.sql
```

The negative test cases are expected to produce errors when business rules are violated.

## Learning Outcomes

This project helped me understand relational database design, SQL constraints, foreign key relationships, triggers, data integrity, and database testing.

It also provided practical experience in translating business requirements into executable SQL logic.

## Acknowledgment

This project was completed as part of the SQL & Database Engineering virtual internship program at RabTech Academy.

## Author

Nivashini Manivannan

B.Tech Student | Aspiring Data Analyst

## License

This project is intended for educational and learning purposes.
