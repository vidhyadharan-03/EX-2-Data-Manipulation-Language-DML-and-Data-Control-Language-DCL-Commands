# EX 2 Data Manipulation Language (DML) Commands and built in functions in SQL
## DATE : 
## AIM:
To create a manager database and execute DML queries using SQL.


## DML(Data Manipulation Language)
<div align="justify">
The SQL commands that deal with the manipulation of data present in the database belong to DML or Data Manipulation Language and this includes most of the SQL statements. It is the component of the SQL statement that controls access to data and to the database. Basically, DCL statements are grouped with DML statements.
</div>

## List of DML commands: 
<div align="justify">
INSERT: It is used to insert data into a table.<br>
UPDATE: It is used to update existing data within a table.<br>
DELETE: It is used to delete records from a database table.<br>
</div>

## Create the table as given below:
```sql
create table manager(enumber number(6),ename char(15),salary number(5),commission number(4),annualsalary number(7),Hiredate date,designation char(10),deptno number(2),reporting char(10));
```
## insert the following values into the table
```sql
insert into manager values(7369,'Dharsan',2500,500,30000,'30-June-81','clerk',10,'John');
insert into manager values(7839,'Subu',3000,400,36000,'1-Jul-82','manager',null,'James');
insert into manager values(7934,'Aadhi',3500,300,42000,'1-May-82','manager',30,NULL);
insert into manager values(7788,'Vikash',4000,0,48000,'12-Aug-82','clerk',50,'Bond');
```

### Q1) Update all the records of manager table by increasing 10% of their salary as bonus.
### QUERY:
~~~
UPDATE manager SET salary = salary * 1.10;
~~~
### Output:
![db1](https://github.com/vidhyadharan-03/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/114286357/f497e4fe-794c-43a9-b78a-156d886a185a)

### Q2) Delete the records from manager table where the salary less than 2750.
### QUERY:
~~~
DELETE FROM manager WHERE salary < 2750;
~~~
### OUTPUT:
![db2](https://github.com/vidhyadharan-03/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/114286357/05681895-d482-4fa0-8109-ff48b8d97c7a)

### Q3) Display each name of the employee as “Name” and annual salary as “Annual Salary” (Note: Salary in emp table is the monthly salary)
### QUERY:
~~~
SELECT ename AS "Name", (salary * 12) + NVL(commission, 0) AS "Annual Salary" FROM manager;
~~~
### OUTPUT:
![db3](https://github.com/vidhyadharan-03/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/114286357/0c287523-4b3f-480f-89c2-f2e58004a57f)

### Q4)	List the names of Clerks from emp table.
### QUERY:
~~~
SELECT ename FROM manager WHERE designation = 'clerk';
~~~
### OUTPUT:
![db4](https://github.com/vidhyadharan-03/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/114286357/216edac9-481c-46df-a461-cc9b3e46301d)

### Q5)	List the names of employee who are not Managers.
### QUERY:
~~~~
SELECT ename FROM manager WHERE designation != 'manager';
~~~~
### OUTPUT:
![db5](https://github.com/vidhyadharan-03/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/114286357/26af984a-1403-4787-8a19-fb1387534716)

### Q6)	List the names of employees not eligible for commission.
### QUERY:
~~~
SELECT ename FROM manager WHERE commission = 0;
~~~
### OUTPUT:
![db6](https://github.com/vidhyadharan-03/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/114286357/99e70079-f7b3-4d12-99a3-9e9e7495957c)

### Q7)	List employees whose name either start or end with ‘s’.
### QUERY:
~~~
SELECT ename FROM manager WHERE ename LIKE 'S%' OR ename LIKE '%S';
~~~
### OUTPUT:
![db7](https://github.com/vidhyadharan-03/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/114286357/8e946d2e-8f72-41a8-ae39-6a5179455034)

### Q8) Sort emp table in ascending order by hire-date and list ename, job, deptno and hire-date.
### QUERY:
~~~
SELECT ename, designation, deptno, Hiredate FROM manager ORDER BY hiredate ASC;
~~~
### OUTPUT:
![db8](https://github.com/vidhyadharan-03/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/114286357/62240796-329d-4a17-842f-d56a6ea57d14)

### Q9) List the Details of Employees who have joined before 30 Sept 81.
### QUERY:
~~~
SELECT * FROM manager WHERE Hiredate < TO_DATE('30-SEP-81', 'DD-MON-YY');
~~~
### OUTPUT:
![db9](https://github.com/vidhyadharan-03/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/114286357/ea38e4d9-dac8-4426-8ded-f4c165131c67)

### Q10)	List ename, deptno and sal after sorting emp table in ascending order by deptno and then descending order by sal.
### QUERY:
~~~
SELECT ename, deptno, salary FROM manager ORDER BY deptno ASC, salary DESC;
~~~
### OUTPUT:
![db10](https://github.com/vidhyadharan-03/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/114286357/5c803a7f-c1c8-4cd4-9997-03fa5728422c)

### Q11) List the names of employees not belonging to dept no 30,40 & 10
### QUERY:
~~~
SELECT ename FROM manager WHERE deptno NOT IN (10, 30, 40);
~~~
### OUTPUT:
![db11](https://github.com/vidhyadharan-03/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/114286357/abd545b1-7084-4d6e-9bd6-4d4cd87805ce)

### Q12) Find number of rows in the table EMP
### QUERY:
~~~
SELECT COUNT(*) AS "Number of Rows" FROM manager;
~~~
### OUTPUT:
![db12](https://github.com/vidhyadharan-03/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/114286357/738d99f8-46d3-4841-8913-c6e9aca68a1c)

### Q13) Find maximum, minimum and average salary in EMP table.
### QUERY:
~~~
SELECT MAX(salary) AS "Maximum Salary", MIN(salary) AS "Minimum Salary", AVG(salary) AS "Average Salary" FROM manager;
~~~
### OUTPUT:

![db13](https://github.com/vidhyadharan-03/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/114286357/485abadc-d414-40c7-a477-2db3784f578f)

### Q14) List the jobs and number of employees in each job. The result should be in the descending order of the number of employees.
### QUERY:
~~~
SELECT designation, COUNT(*) AS "Number of Employees" FROM manager GROUP BY designation ORDER BY COUNT(*) DESC;
~~~
### OUTPUT:
![db14](https://github.com/vidhyadharan-03/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/114286357/2212a2b1-3529-486e-b16f-1c0f2a66a2e5)
