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
Insert all employees from Former_employees into Employee

Table attributes are EmployeeID, Name, Department, Salary

```sql
Insert into Employee (EmployeeID,Name,Department,Salary) 
Select EmployeeID,Name,Department,Salary 
From Former_employees;
```

**Output:**

![alt text](image.png)

**Question 2**
---
Create a table named Members with the following columns:

+ MemberID as INTEGER
+ MemberName as TEXT
+ JoinDate as DATE

```sql
Create table Members(MemberID INTEGER,
MemberName TEXT,
JoinDate DATE);
```

**Output:**

![alt text](image-1.png)

**Question 3**
---
Insert the below data into the Employee table, allowing the Department and Salary columns to take their default values.

| EmployeeID | Name         | Position |
|-------------|--------------|-----------|
| 4           | Emily White  | Analyst   |


Note: The Department and Salary columns will use their default values
```sql
Insert into Employee (EmployeeID, Name, Position) values(4,"Emily White","Analyst"); 
```

**Output:**

![alt text](image-3.png)

**Question 4**
---
| RollNo | Name        | Gender | Subject     | Marks |
|--------|--------------|--------|--------------|--------|
| 202    | Ella King    | F      | Chemistry    | 87     |
| 203    | James Bond   | M      | Literature   | 78     |


```sql
Insert into Student_details values(202,"Ella King","F","Chemistry",87),
                                  (203,"James Bond","M","Literature",78); 
```

**Output:**

![alt text](image-4.png)

**Question 5**
---
Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
+ ShipmentDate as DATE.
+ SupplierID as INTEGER should be a foreign key referencing Suppliers SupplierID).
+ OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
Create table Shipments(
ShipmentID INTEGER primary key,
ShipmentDate DATE,
SupplierID INTEGER,
OrderID INTEGER,
foreign key(OrderID) references Orders(OrderID),
foreign key(SupplierID) references Suppliers(SupplierID));
```

**Output:**

![alt text](image-2.png)

**Question 6**
---
Create a table named ProjectAssignments with the following constraints:
+ AssignmentID as INTEGER should be the primary key.
+ EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
+ ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
+ AssignmentDate as DATE should be NOT NULL.

```sql
Create table ProjectAssignments(
AssignmentID INTEGER primary key,
EmployeeID INTEGER,
ProjectID INTEGER,
AssignmentDate DATE NOT NULL,
foreign key(ProjectID) references Projects(ProjectID), 
foreign key(EmployeeID) references Employees(EmployeeID));
```

**Output:**

![alt text](image-5.png)

**Question 7**
---
Write a SQL query to add a column named Date_of_birth as Date in the Student_details table.

```sql
Alter table Student_details add Date_of_birth Date;
```

**Output:**

![alt text](image-6.png)

**Question 8**
---
Write an SQL query to change the name of the column id to employee_id in the table employee.

```sql
Alter table employee rename id to employee_id;
```

**Output:**

![alt text](image-7.png)

**Question 9**
---
create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.

```sql
Create table jobs(
job_id Int,
job_title text,
min_salary int Default 8000 Check(min_salary >7999),
max_salary int Default Null); 
```

**Output:**

![alt text](image-8.png)

**Question 10**
---
Write a SQL query to Add a new column named "discount" with the data type DECIMAL(5,2) to the "customer" table.

Sample table: customer

| customer_id | cust_name     | city        | grade | salesman_id |
|--------------|---------------|-------------|--------|--------------|
| 3002         | Nick Rimando  | New York    | 100    | 5001         |
| 3007         | Brad Davis    | New York    | 200    | 5001         |
| 3005         | Graham Zusi   | California  | 200    | 5002         |


```sql
Alter Table Customer Add discount DECIMAL(5,2);
```

**Output:**

![alt text](image-9.png)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
