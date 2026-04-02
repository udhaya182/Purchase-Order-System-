# Database-Driven Purchase Order Management System

## 🧾 Overview
A backend-focused Purchase Order Management System built using Python, SQL, and Flask. The system is designed to handle real-world transactional workflows, ensuring data integrity, consistency, and efficient data retrieval across multiple related entities.

It simulates enterprise-level database operations including order processing, validation, and inventory updates through structured SQL queries and API endpoints.

---

## ⚙️ Technologies
- Python (Flask)
- SQL (MySQL / Relational Database)
- JDBC-style database interaction (via connectors)
- RESTful APIs

---

## 🗄️ Database Design
The system uses a relational database with multiple interconnected tables:

- **Clients**
- **Parts (Inventory)**
- **Purchase Orders**
- **Order Lines**

Key design principles:
- Normalized schema to reduce redundancy
- Foreign key relationships to maintain referential integrity
- Structured data model supporting transactional operations

---

## 🔑 Key Features
- Designed and implemented a **relational database schema** for managing orders, clients, and inventory  
- Executed **complex SQL queries** for insertion, updates, validation, and data retrieval  
- Developed RESTful APIs to support **data access and reporting**  
- Implemented **data validation logic** (client checks, stock availability, order constraints)  
- Utilized **SQL triggers** to automate backend updates and enforce consistency  
- Supported full purchase order lifecycle: creation, updates, status tracking, and querying  

---

## 🔄 Transaction Handling
The system ensures consistency through **transactional workflows**:

- Purchase order creation  
- Order line insertion  
- Inventory updates  

All operations are executed atomically using commit/rollback mechanisms to prevent partial updates and maintain database consistency.

---

## ⚡ Data Integrity & Validation
- Enforced through validation queries before data insertion  
- Prevents invalid orders (e.g., non-existent clients, insufficient stock)  
- Maintains consistency across related tables  
- Automated updates using SQL triggers  

---

## 📊 Sample Queries

```sql
-- Get total orders per client
SELECT clientId, COUNT(*) AS total_orders
FROM PurchaseOrders
GROUP BY clientId;

-- Get pending orders
SELECT *
FROM PurchaseOrders
WHERE status = 'Pending';

-- Generate next line number dynamically
SELECT COALESCE(MAX(lineNo), 0) + 1
FROM OrderLines
WHERE poId = ?;
