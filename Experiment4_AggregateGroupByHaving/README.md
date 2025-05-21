# Experiment 4: Aggregate Functions, Group By and Having Clause
### Reg.No : 212223040186
### Name : SANJEV R M
## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
```
Write a SQL query to find the customer with longest name?
Table: customer
name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER
For example:
Result
name          length
------------  ----------
Preeti Patel  12
```
```sql
select name,LENGTH(name) as length
from customer
order by length(name) DESC LIMIT 1;
```

**Output:**

![image](https://github.com/user-attachments/assets/de1deadb-97ca-4dfa-9c6c-6f5a0e10f574)


**Question 2**
```
How many appointments are scheduled for each patient?
Sample table: Appointments Table
name                  type
--------------------  ----------
AppointmentID         INTEGER
PatientID             INTEGER
DoctorID              INTEGER
AppointmentDateTime   DATETIME
Purpose               TEXT
Status                TEXT
For example:
Result
PatientID   TotalAppointments
----------  -----------------
3           3
5           2
6           1
7           1
10          3
```

```sql
select PatientID,count(*) as TotalAppointments
from Appointments
group by PatientID
```

**Output:**

![image](https://github.com/user-attachments/assets/b11fedb4-8d68-4c21-93be-b57805ebc207)

**Question 3**
```
Write a SQL query to find the minimum purchase amount.
Sample table: orders
ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001
For example:
Result
MINIMUM
----------
65.26
```
```sql
select min(purch_amt) as "MINIMUM"
from orders;
```

**Output:**

![image](https://github.com/user-attachments/assets/cffc8b52-4601-462d-b8a3-53ef22fc5b18)


**Question 4**
```
How many appointments are scheduled in each hour of the day?
Sample table:Appointments Table
name                              type
--------------------          ----------
AppointmentID               INTEGER
PatientID                         INTEGER
DoctorID                         INTEGER
AppointmentDateTime   DATETIME
Purpose                           TEXT
Status                              TEXT     
For example:
Result
HourOfDay   TotalAppointments
----------  -----------------
09          2
10          5
11          1
14          1
16          1
```

```sql
select strftime('%H',AppointmentDateTime)as HourOfDay,count(*) as TotalAppointments
from Appointments
group by HourOfDay
order by HourOfDay;
```

**Output:**

![image](https://github.com/user-attachments/assets/e324b364-4c90-4b70-87d8-2cd7c9bd9cc1)




**Question 5**
```
Write a SQL query to find What is the age difference between the youngest and oldest employee in the company.
Table: employee
name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
For example:
Result
age_difference
--------------
13
```
```sql
select MAX(age)-MIN(age) as age_difference
from employee;
```

**Output:**

![image](https://github.com/user-attachments/assets/068fca57-5e72-4419-99c3-cd8d96e1ef69)

**Question 6**
```
What is the average dosage prescribed for each medication?
Sample tablePrescriptions Table
```
![image](https://github.com/user-attachments/assets/af0015ae-9461-42eb-84e0-51e064466b75)
```
For example:
Result
Medication     AvgDosage
-------------  ----------
Ciprofloxacin  500.0
Doxorubicin    60.0
Ibuprofen      400.0
Levothyroxine  50.0
Lisinopril     10.0
MMR            0.5
Pending        0.0
Prenatal vita  1.0
Sertraline     50.0
Topiramate     25.0
```

```sql
select Medication,avg(Dosage) as AvgDosage
from Prescriptions
group by Medication;
```

**Output:**

![image](https://github.com/user-attachments/assets/25c11a97-d608-40bd-b3ce-100aaa680b28)



**Question 7**
```
Write a SQL query that counts the number of unique salespeople. Return number of salespeople.
Sample table: orders
ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001
For example:
Result
COUNT
----------
6
```

```sql
select count(DISTINCT salesman_id)as COUNT
from orders;
```

**Output:**

![image](https://github.com/user-attachments/assets/b3175bf9-2572-4363-af84-f7f354f232e6)



**Question 8**
```
Write the SQL query that achieves the grouping of data by city, calculates the total income for each city, and includes only those cities where the total income sum is greater than 200,000.
Sample table: employee
```
![image](https://github.com/user-attachments/assets/b9bdb5ec-c7eb-4692-844f-61a9dec1f10a)
```
For example:
Result
city        Income
----------  ----------
Alaska      450000
Arizona     1000000
California  5300000
Florida     5350000
Georgia     250000
```

```sql
select city,sum(income) as Income
from employee
group by city
having sum(income)>200000;
```

**Output:**

![image](https://github.com/user-attachments/assets/e3830f2d-83f0-41a7-bff4-3486a4c5d0cc)



**Question 9**
```
Write a SQL query to calculate total available amount of fruits that has a price greater than 0.5 . Return total Count. 
Note: Inventory attribute contains amount of fruits
Table: fruits
name        type
----------  ----------
id          INTEGER
name        TEXT
unit        TEXT
inventory   INTEGER
price       REAL
For example:
Result
total_available_amount
----------------------
160
```
```sql
select  sum(inventory) as total_available_amount
from fruits
where price >0.5;

```

**Output:**

![image](https://github.com/user-attachments/assets/d191675d-fc2d-43f2-947e-06bffb4b6bc4)

**Question 10**
```
Write a SQL query to find the average length of email addresses (in characters):
Table: customer
name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER
For example:
Result
avg_email_length
----------------
15.0
```
```sql
select AVG(length(email)) as avg_email_length
from customer;
```

**Output:**

![image](https://github.com/user-attachments/assets/9a4be1ed-cfeb-4529-a540-9263fab67cbf)



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
