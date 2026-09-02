# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
<img width="1056" height="363" alt="image" src="https://github.com/user-attachments/assets/9e5447e9-6d71-491f-885a-85b4b9cb61b3" />


```sql
INSERT INTO Books SELECT * FROM Out_of_print_books;
```

**Output:**

<img width="919" height="414" alt="image" src="https://github.com/user-attachments/assets/6950eb81-853f-4dcb-8378-8cd22e576e3f" />

**Question 2**
---
<img width="988" height="456" alt="image" src="https://github.com/user-attachments/assets/73f3d7de-2a9a-4685-b59d-170b27495ff3" />

```sql
CREATE TABLE Employees(
    EmployeeID INTEGER,
    FirstName TEXT,
    LastName TEXT,
    HireDate DATE
);
```

**Output:**

<img width="955" height="438" alt="image" src="https://github.com/user-attachments/assets/35adb9d6-17f1-45c1-95cb-f488247e83d1" />

**Question 3**
---
<img width="1224" height="280" alt="image" src="https://github.com/user-attachments/assets/35ba6860-81f6-4560-8873-246c54a0802c" />


```sql
INSERT INTO Books (ISBN, Title, Author, Publisher, Year)
VALUES ('978-1234567890', 'Data Science Essentials', 'Jane Doe', 'TechBooks', 2024);
```

**Output:**

<img width="876" height="314" alt="image" src="https://github.com/user-attachments/assets/94380d97-a438-4d8f-b6ab-9cadd963d25a" />


**Question 4**
---
<img width="1432" height="560" alt="image" src="https://github.com/user-attachments/assets/0fb42b76-685c-4522-9fe5-d9092601aea9" />


```sql
INSERT INTO Student_details
VALUES (205, 'Olivia Green', 'F', NULL, NULL);
INSERT INTO Student_details
VALUES (207, 'Liam Smith', 'M', 'Mathematic', 85);
INSERT INTO Student_details
VALUES (208, 'Sophia Johns', 'F', 'Science',NULL);
```

**Output:**

<img width="832" height="293" alt="image" src="https://github.com/user-attachments/assets/b0e0d27d-894c-449a-ae30-d1e1528213a8" />

**Question 5**
---
<img width="1109" height="223" alt="image" src="https://github.com/user-attachments/assets/60526f99-c34f-46f1-a274-545e8d44cf1e" />


```sql
CREATE TABLE Orders (
    OrderID INTEGER PRIMARY KEY,
    OrderDate DATE NOT NULL,
    CustomerID INTEGER,
    FOREIGN KEY ( CustomerID)
REFERENCES Customers(CustomerID)
);
```

**Output:**

<img width="816" height="252" alt="image" src="https://github.com/user-attachments/assets/4a068547-3145-4b1a-9c97-f66ca9a75334" />


**Question 6**
---
<img width="1010" height="202" alt="image" src="https://github.com/user-attachments/assets/0bfe4c76-5059-46b3-8638-0b8c12315d32" />


```sql
CREATE TABLE Shipments ( 
    ShipmentID INTEGER PRIMARY KEY,
    ShipmentDate DATE,
    SupplierID INTEGER,
    OrderID INTEGER,
    FOREIGN KEY (SupplierID)
REFERENCES Suppliers(SupplierID),
    FOREIGN KEY (OrderID) REFERENCES
Orders(orderID)    
);
```

**Output:**

<img width="907" height="270" alt="image" src="https://github.com/user-attachments/assets/38a5ea70-9a9d-439a-a527-6652dad07d75" />


**Question 7**
---
<img width="1200" height="247" alt="image" src="https://github.com/user-attachments/assets/a1c7fbb1-12d5-409b-a027-6b1c9335b3f8" />


```sql
CREATE TABLE contacts (
    contact_id INTEGER PRIMARY KEY,
    first_name TEXT NOT NULL,
    last_name TEXT NOT NULL,
    email TEXT,
    phone TEXT NOT NULL CHECK
    (LENGTH(phone)>=10)
);
```

**Output:**

<img width="1056" height="322" alt="image" src="https://github.com/user-attachments/assets/1ec6cfa1-25c6-493c-8fbe-a6db97a7f870" />


**Question 8**
---
<img width="868" height="207" alt="image" src="https://github.com/user-attachments/assets/8f62ea9e-8d7c-4852-a8fa-e437387969dd" />


```sql
CREATE TABLE Bonuses (
    BonusID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    BonusAmount REAL CHECK
(BonusAmount>0),
    BonusDate DATE,
    Reason TEXT NOT NULL,
    FOREIGN KEY (EmployeeID)
REFERENCES
Employees(EmployeeID)
);
```

**Output:**

<img width="1101" height="345" alt="image" src="https://github.com/user-attachments/assets/d04a7779-d49e-4c97-8872-99541565553c" />


**Question 9**
---
<img width="1545" height="476" alt="image" src="https://github.com/user-attachments/assets/6ae3fe80-8a69-40c0-b7c1-855842296f8d" />

```sql
ALTER TABLE Student_details
ADD COLUMN MobileNumber NUMBER;
ALTER TABLE Student_details
ADD COLUMN Address VARCHAR(100);
```

**Output:**

<img width="1190" height="368" alt="image" src="https://github.com/user-attachments/assets/0dda4221-1e79-426c-a756-d3f7709fede4" />

**Question 10**
---
<img width="1284" height="435" alt="image" src="https://github.com/user-attachments/assets/f1d19c22-c55b-4f2a-a53a-292f5e6baefc" />

```sql
ALTER TABLE Student_details
ADD COLUMN Date_of_birth Date;
```

**Output:**

<img width="1294" height="357" alt="image" src="https://github.com/user-attachments/assets/6312a24b-9e11-4dff-93c8-609185e99d42" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
