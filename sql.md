# 💾 SQL (MySQL) Cheatsheet

---

## Setup & Fundamentals

### MySQL Installation & Connect

- Install MySQL, use `mysql -u root -p` to connect.

---

### DATABASES

- Create, use, drop databases.

```sql
CREATE DATABASE dbname;
USE dbname;
DROP DATABASE dbname;
```

---

### TABLES

- Create, drop tables.

```sql
CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL
);
DROP TABLE users;
```

---

## Data Manipulation (DML)

### INSERT

- Add rows.

```sql
INSERT INTO users (name) VALUES ('Alice');
```

---

### SELECT

- Query data.

```sql
SELECT * FROM users;
SELECT name FROM users WHERE id = 1;
SELECT DISTINCT name FROM users;
```

---

### UPDATE & DELETE

- Modify or remove rows.

```sql
UPDATE users SET name = 'Bob' WHERE id = 1;
DELETE FROM users WHERE id = 1;
```

---

### Transactions

- Control commit/rollback.

```sql
START TRANSACTION;
-- DML statements
COMMIT;
ROLLBACK;
```

---

## Constraints & Integrity

### UNIQUE, NOT NULL, CHECK, DEFAULT

```sql
CREATE TABLE products (
    id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL UNIQUE,
    price DECIMAL(10,2) CHECK (price > 0) DEFAULT 1.00
);
```

---

### PRIMARY KEY & AUTO_INCREMENT

```sql
CREATE TABLE logs (
    log_id INT PRIMARY KEY AUTO_INCREMENT,
    message TEXT
);
```

---

### FOREIGN KEY

```sql
CREATE TABLE orders (
    id INT PRIMARY KEY,
    user_id INT,
    FOREIGN KEY (user_id) REFERENCES users(id)
);
```

---

### ON DELETE

```sql
FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE
```

---

## Querying & Relationships

### JOINS

```sql
SELECT u.name, o.id
FROM users u
INNER JOIN orders o ON u.id = o.user_id;
```

---

### SELF JOIN

```sql
SELECT a.name, b.name
FROM employees a, employees b
WHERE a.manager_id = b.id;
```

---

### UNION

```sql
SELECT name FROM users
UNION
SELECT name FROM customers;
```

---

## Filtering, Sorting, Aggregation

### WHERE, AND, OR, NOT

```sql
SELECT * FROM products WHERE price > 10 AND category = 'Electronics';
```

---

### LIKE & Wildcards

```sql
SELECT * FROM users WHERE name LIKE 'A%';
```

---

### ORDER BY & LIMIT

```sql
SELECT * FROM products ORDER BY price DESC LIMIT 5;
```

---

### GROUP BY & HAVING

```sql
SELECT category, COUNT(*) FROM products GROUP BY category HAVING COUNT(*) > 1;
```

---

### Functions

```sql
SELECT COUNT(*) FROM users;
SELECT AVG(price) FROM products;
SELECT CONCAT(first_name, ' ', last_name) FROM users;
```

---

### CURRENT_DATE(), NOW()

```sql
SELECT CURRENT_DATE(), NOW();
```

---

## Advanced Objects & Logic

### VIEWS

```sql
CREATE VIEW active_users AS SELECT * FROM users WHERE active = 1;
SELECT * FROM active_users;
```

---

### INDEXES

```sql
CREATE INDEX idx_name ON users(name);
DROP INDEX idx_name ON users;
```

---

### SUBQUERIES

```sql
SELECT name FROM users WHERE id IN (SELECT user_id FROM orders);
```

---

### STORED PROCEDURES

```sql
DELIMITER //
CREATE PROCEDURE GetUser(IN uid INT)
BEGIN
  SELECT * FROM users WHERE id = uid;
END //
DELIMITER ;
CALL GetUser(1);
```

---

### TRIGGERS

```sql
CREATE TRIGGER before_update
BEFORE UPDATE ON users
FOR EACH ROW
SET NEW.updated_at = NOW();
```

---
