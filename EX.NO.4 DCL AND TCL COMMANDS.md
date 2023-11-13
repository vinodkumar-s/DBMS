# EX.NO 4 Data Control Language (DCL) Commands and Transaction Control Languages (TCL) in SQL
### DATE:
## AIM:
To create a manager database and execute DML queries using SQL.


# THEORY
## Data Control Language (DCL) commands
* Data control language (DCL) is used to access the stored data.
* It is mainly used for revoke and to grant the user the required access to a database.
## List of DCL commands: 
1. GRANT : It is used to insert data into a table.
2. REVOKE: It is used to update existing data within a table.
## Transaction control language(TCL) commands
1. COMMIT : COMMIT command in SQL is used to save all the transaction-related changes permanently to the disk
2. START TRANSACTION : to start the transaction
3. ROLLBACK : undo the transaction upto savepoint 
4. SAVEPOINT : create a savepoint to save the different parts of the same transaction using different names

### Q1) Create a table employee with employee id ,name and Address

### QUERY:
```sql
create table employee(
emp_id numeric,
emp_name varchar(10),
addr varchar(40)
);
```



### OUTPUT:
![image](https://github.com/Yuvaraj878/DBMS/assets/118622554/4885d2a8-451a-43b0-8c65-3fd8808d47d6)




### Q2) Insert three rows into emploee table 



### QUERY:
```sql
INSERT INTO employee (employee_id, name, address)
VALUES (1, 'John Doe', '123 Main Street'),
       (2, 'Jane Doe', '456 Elm Street'),
       (3, 'Peter Parker', '789 Queens Boulevard');
```

### OUTPUT:
![image](https://github.com/Yuvaraj878/DBMS/assets/118622554/10475fc7-507b-4621-8330-61a2a1b3f92e)

### Q3) Start the transaction and create a save point A.

### QUERY:
```sql
START TRANSACTION;
SAVEPOINT s1;
```

### OUTPUT:
![image](https://github.com/Yuvaraj878/DBMS/assets/118622554/c82a7afd-ad22-41d4-93c0-09d3f0eb8ac2)

![image](https://github.com/Yuvaraj878/DBMS/assets/118622554/8fcc7ae6-b16e-49f2-a219-8dd49c3ee93a)


### Q4) Perform insertion into employee table.

### QUERY:
```sql
INSERT INTO employee (employee_id, name, address)
VALUES (4, 'Mary Jane Watson', '1011 Mockingbird Lane');
```

### OUTPUT:
![image](https://github.com/Yuvaraj878/DBMS/assets/118622554/9a83829c-4b35-425d-942b-8a25e1b70d9e)




### Q6)	Display the employee table and create a save point s2 .


### QUERY:
```sql
SELECT * FROM employee;
SAVEPOINT s2;
```

### OUTPUT:
![image](https://github.com/Yuvaraj878/DBMS/assets/118622554/f2c1c800-e66a-4af1-a8b3-99b7c63dbb4c)




### Q7)	Perform updation on any one of the row.


### QUERY:
```sql
UPDATE employee SET name = 'Spider-Man' WHERE employee_id = 3;
```

### OUTPUT:
![image](https://github.com/Yuvaraj878/DBMS/assets/118622554/04623c17-7bdb-442e-91ef-988eea34a57c)




### Q8) Display the employee table and rollback to  save point s2 


### QUERY:
```sql
SELECT * FROM employee;
ROLLBACK TO SAVEPOINT s2;
```

### OUTPUT:
![image](https://github.com/Yuvaraj878/DBMS/assets/118622554/84694909-163c-4c14-9f5d-596ceeade9a0)



### Q9) Display the employee table and commit the changes; 


### QUERY:
```sql
SELECT * FROM employee;
COMMIT;
```

### OUTPUT:
![image](https://github.com/Yuvaraj878/DBMS/assets/118622554/fdd4bb14-f103-41a8-bd16-782b0b39d97e)




### Q10) Rollback to save point s1;


### QUERY:
```sql
ROLLBACK TO SAVEPOINT s1;
```

### OUTPUT:
![image](https://github.com/Yuvaraj878/DBMS/assets/118622554/a599ec17-2359-4aae-8011-17a7f8e1a839)



### Q11)	Create a new user and grant access to any one database with "insert and update"


### QUERY:
```sql
CREATE USER new_user;
GRANT INSERT, UPDATE ON database_name TO new_user;
```

### OUTPUT:
![image](https://github.com/Yuvaraj878/DBMS/assets/118622554/3c3761a5-28c0-4c83-a203-89e0087e6676)

![image](https://github.com/Yuvaraj878/DBMS/assets/118622554/fd08ac3a-d1a5-4a16-af6a-f3bc5ff24629)

### Q12) Check the user access and display the result 


### QUERY:
```sql
SHOW GRANTS FOR new_user;
```

### OUTPUT:
![image](https://github.com/Yuvaraj878/DBMS/assets/118622554/2fbd5d94-7610-4828-a072-c84372c06442)

### Q13) Revoke the privillages.

### QUERY:
```sql
SHOW GRANTS FOR new_user;
REVOKE INSERT, UPDATE ON database_name FROM new_user;
SHOW GRANTS FOR new_user;
```

### OUTPUT:
![image](https://github.com/Yuvaraj878/DBMS/assets/118622554/bd4b2b58-817e-42ea-b84d-a59af0382c11)


## RESULT :
Thus the basic TCL and DCL commands are executed.
