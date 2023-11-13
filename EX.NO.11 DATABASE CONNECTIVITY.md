# EX 11: Oracle Database Connection with Python
## Date: 
## AIM:
To connect Oracle database with Python using mysql.
## PROCEDURE:
1. Install mysql : With the command **pip install mysql**
2. To Connect **connect():**
   Now Establish a connection between the Python program and Oracle database by using connect() function. 
```python
con = mysql.connect('username/password@localhost')
cursor(): To execute a SQL query and to provide results some special object is required that is nothing but cursor() object.
cursor = con.cursor()
```
3.To Execute **execute/executemany method:**
```python
cursor.execute(sqlquery) - - - -> to execute a single query. 
cursor.executemany(sqlqueries) - - - -> to execute a single query with multiple bind variables/place holders.
```
4. To Commit **commit():**
   For DML(Data Manipulation Language) queries that comprise operations like update, insert, delete. We need to commit() then only the result reflects in the database.
5. To Fetch rows: **fetchone(), fetchmany(int), fetchall():**
fetchone() : This method is used to fetch one single row from the top of the result set.
fetchmany(int): This method is used to fetch a limited number of rows based on the argument passed in it.
fetchall() : This method is used to fetch all rows from the result set.
6. To Close db connectivity **close():**
   After all done it is mandatory to close all operations.
```python
cursor.close()
con.close()
```
## Creating a Table:
## PROGRAM:

```py
import mysql.connector
conn = mysql.connector.connect(
    host='*****',
    user='********',  
    password='***************',  
    database='students'  
)
my_cursor = conn.cursor()
create_table_query = """
CREATE TABLE students (
    stuid INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    department VARCHAR(10)
)
"""
my_cursor.execute(create_table_query)
conn.commit()
my_cursor.close()
conn.close()
print("Table 'STUDENTS' created successfully.")
```
## OUTPUT:
![image](https://github.com/Yuvaraj878/DBMS/assets/118622554/b45e56da-6fe2-49c8-bf46-03aa9602e339)

## Insert the data into the table:
## PROGRAM:
```py
import mysql.connector
conn = mysql.connector.connect(
    host='*****',
    user='***********',  
    password='***************',  
    database='students'  
)
my_cursor = conn.cursor()
records = [
    ("Yuvaraj.S", "AIML"),
    ("Puneeth.P", "ECE"),
    ("Rohit.R", "CSE"),
]
insert_query = "INSERT INTO STUDENTS (name, department) VALUES (%s, %s)"
my_cursor.executemany(insert_query, records)
conn.commit()
my_cursor.close()
conn.close()
print(f"{my_cursor.rowcount} records inserted successfully.")
```
## OUTPUT
![image](https://github.com/Yuvaraj878/DBMS/assets/118622554/4aa1e402-86e2-4717-ba50-26b2e7cc514f)

## Display the table:
## PROGRAM:
```python
import mysql.connector
conn = mysql.connector.connect(
    host='***',
    user='****',  
    password='******',  
    database='students'  
)
my_cursor = conn.cursor()
select_query = "SELECT * FROM students"
my_cursor.execute(select_query)
records = my_cursor.fetchall()
print("Students Data:")
print("StuID\tName\tDepartment")
for record in records:
    stuid, name, department = record
    print(f"{stuid}\t{name}\t{department}")
my_cursor.close()
conn.close()
```
## OUTPUT:
![image](https://github.com/Yuvaraj878/DBMS/assets/118622554/d3530991-dde6-4418-adcf-2c6a5ea077fd)

## RESULT:
Thus the program for dababase connectivity with python has been executed successfully.
