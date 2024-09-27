# SQL-files
SQL codes showing my competencies as an SQL professional
## This is the SQL code showing various SQL queries on my LITA Database
CREATE TABLE 
---
```
CREATE TABLE Employee (
staffid varchar (10) not null,
FirstName varchar (255) NOT NULL,
SecondName varchar (255),
Gender varchar (10),
Date_of_Birth date,
HireDate datetime,
primary key (staffid)
)
```
**VIEW TABLE**
---
```
Select * from Employee;
```
ADD RECORD TO A TABLE
---
```
insert into Employee (staffid, firstname, secondname, gender,Date_of_Birth, hiredate)
values ( 'AB401', 'ayan', 'olakun', 'female', '1992-08-22', '2018-02-09'),
( 'AB212', 'okorie', 'mercy', 'female','1988-10-09', '2018-10-09'),
( 'AB223', 'joshua', 'chukwuemeka', 'male','1980-10-09', '2022-02-09'),
( 'AB234', 'sanni', 'ibrahim', 'male','1958-10-09', '2019-09-23'),
( 'AB254', 'mercy', 'olanipekun', 'female','1982-10-09', '2020-02-09'),
( 'AB249', 'johnson', 'mercy', 'female','1982-10-09', '2019-12-09'),
( 'AB298', 'ayomide', 'halleluyah', 'female', '1982-10-09','2018-07-11'),
( 'AB260', 'deborah', 'justin', 'female','1982-10-09', '2018-02-09'),
( 'AB281', 'wale', 'olanipekun', 'male','1982-10-09', '2018-02-09')
```


-------to drop table --------

drop table employee

----delete sql command--

delete from employee
where staffid  = 'ab281'

-----truncate sql command

truncate table employee  

-----identity in SQL -----



select * from PERSON


( 'AB240', 'johnson', 'mercy', 'female','1982-10-09', '2019-12-09'),
( 'AB299', 'ayomide', 'halleluyah', 'female', '1982-10-09','2018-07-11'),
( 'AB268', 'deborah', 'justin', 'female','1982-10-09', '2018-02-09'),
( 'AB286', 'wale', 'olanipekun', 'male','1982-10-09', '2018-02-09'),
( 'AB270', 'shukurat', 'lasisi', 'female','1982-10-09', '2018-02-09')

select * from Employee

---- to create second table call SALARY TABLE-------
CREATE TABLE Salary (
salary_id int AUTO_INCREMENT primary key not null,
Staffid varchar (255),
firstname varchar (255),
lastname varchar (255),
department varchar(255),
salary decimal (10, 3) 
)

select * from Salary

-----insert records into Salary table-------------

insert into salary (staffid, FirstName, lastname, Department, Salary)



----SUM, COUNT, MAX, MIN, AVERAGE---------------------------------

SELECT SUM(Salary) AS TOTALSALARY FROM Salary
----I want to know the totls
SELECT AVG(Salary) AS AVERAGESALARY FROM Salary

SELECT COUNT(Staffid) AS EmployeeCount FROM EMPLOYEE

SELECT COUNT(Staffid) AS NumberOfEmployee FROM Salary

-----update--------

UPDATE Salary
SET salary = 7056999.999
WHERE Staffid = 'AB401'

------
-----------------------13/09/2024------------------------
--update staff name-----

select * from Employee 

update employee
set secondname = 'Endurance'
where staffid = 'AB405'

----UPDATE DEPARTMENT-------

select * from Salary

UPDATE SALARY
SET department = 'Information Tech.'
where Staffid = 'AB234'

UPDATE SALARY
SET department = 'Information Tech.' WHERE Staffid = 'AB240'


SELECT * FROM Salary
WHERE Staffid = 'AB281'

----CREATE ADDITIONAL COLUMN INTO EMPLOYEE TABLE-------

ALTER TABLE EMPLOYEE
ADD State_of_Origin varchar (50)

select * from employee

UPDATE EMPLOYEE
SET State_of_Origin = 'Ekiti'
where staffid = 'AB268'

-----create another table called PAYMENT TABLE------
CREATE TABLE Payment (
paymentid int AUTO_INCREMENT primary key,
Account_No bigint not null,
staffid int,
Bank varchar (255) default 'Zenith Bank',
Payment_Method varchar (50) check (Payment_Method = 'Cash' or Payment_Method = 'Transfer')
)

alter table payment
modify column staffid varchar (30)

select * from Payment


(2034562241, 'AB270',  'cash'),
(2234556302, 'AB104',  'transfer'),
(2033037705, 'AB268',  'cash'),
(2033030306, 'AB270',  'cash'),
(2455657509, 'AB300',  'transfer')

insert into Payment (account_no,staffid,payment_method )
values (2198773830, 'AB299',  'transfer'),
(2024656569, 'AB405', 'cash'),
(2222444933, 'AB200',   'transfer'),
(5674842300, 'AB278', 'transfer'),
(2222444933, 'AB200', 'transfer'),
(2034537300, 'AB278',  'transfer')

------those receive their salary by cash-----
SELECT * FROM Payment
WHERE Payment_Method = 'Cash'

select * from Payment
where Payment_Method = 'TRANSFER'

SELECT COUNT(*)  AS ZenithStaff FROM Payment
where Bank = 'Zenith Bank'

SELECT COUNT(*)  FROM Payment
where Bank = 'GT BANK'

SELECT COUNT(*)  FROM Payment
where Payment_Method = 'Transfer'

SELECT COUNT(*)  FROM Payment
where Payment_Method = 'cASH'

---Analysis on Employee table------

select * from Employee
update employee set state_of_origin = 'Kano'
where staffid = 'AB200'
select count(*)  from employee 
where stViewsate_of_origin  = 'Ekiti'

select count(*)  from employee 
where gender  = 'male'

select * from Salary

select count(*)  from Salary
where department  = 'Human Resources'

select  * from Salary LIMIT 5

select * from Salary
where salary > 700000

select Staffid, salary from Salary
where salary < 700000


select max(salary) as max_salary from Salary

select min(salary) as min_salary from Salary


SELECT * FROM Salary
--------------------------------17/09/2024--------------------------------------------------------

select * from employee
 
select * from Salary
 
--------GROUP BY------------------------------

select count(staffid) as StaffPerSate, state_of_origin from Employee

GROUP BY State_of_Origin

 
select count(staffid), department from Salary

group by department
 
select count(*)  from Salary where department = 'human resources'
select * from salary

 
---------HAVING------------------------------

select count(staffid) as StaffPerSate, state_of_origin 

from Employee

GROUP BY State_of_Origin

HAVING COUNT(staffid) >=3
 
select count(staffid) as staffperdepart, department 

from Salary

group by department

having count(Staffid) >= 2
 
-------order by----------------

select count(staffid) as StaffPerSate, state_of_origin 

from Employee

GROUP BY State_of_Origin

order by  count(staffid) desc
 
select count(staffid) as StaffPerSate, state_of_origin 

from Employee

GROUP BY State_of_Origin

order by  count(staffid) asc
 
-------sort by column index------------
 
select count(staffid) as StaffPerSate, state_of_origin 

from Employee

GROUP BY State_of_Origin

order by  1 desc
 
----Comparison/Relational Operator--------------------
< = less than
> = greater than
<> = not equal
 
select * from Salary

where salary = 100560.934
 
select * from Salary

where salary <> 100560.934
 
select * from Salary

where salary > 100560.934
 
select * from Salary

where salary < 100560.934
 
-------range operators---------------------

Between 

Not Between
 
select * from Salary

where salary between 500000 and 900000
 
select * from Salary

where salary not between 500000 and 900000
 

----------------19/09/2024----------------

---List operator------------------
--IN
--NOT IN

SELECT * FROM EMPLOYEE
WHERE FIRSTNAME IN ('SANNI', 'DEBORAH', 'MERCY')

SELECT * FROM Salary
WHERE department IN ('ACCOUNT', 'LOGISTICS','HUMAN RESOURCES')

SELECT * FROM Salary
WHERE department NOT IN 
('ACCOUNT', 'LOGISTICS','HUMAN RESOURCES')

----------LOGICAL OPERATORS----------------------
----AND
---OR

SELECT * FROM EMPLOYEE
WHERE FIRSTNAME = 'JUSTIN'

SELECT * FROM EMPLOYEE
WHERE FIRSTNAME = 'JUSTIN' AND GENDER = 'FEMALE'

SELECT * FROM EMPLOYEE
WHERE FIRSTNAME = 'JOHNSON' AND GENDER = 'FEMALE'

----OR

SELECT * FROM EMPLOYEE
WHERE FIRSTNAME = 'JUSTIN' OR GENDER = 'FEMALE'

SELECT * FROM  EMPLOYEE
WHERE GENDER = 'MALE' AND DATE_OF_BIRTH <= '1990-01-01'
AND STATE_OF_ORIGIN = 'LAGOS'

SELECT * FROM  EMPLOYEE
WHERE GENDER = 'MALE' AND DATE_OF_BIRTH >= '1990-01-01'
AND STATE_OF_ORIGIN = 'LAGOS'



SELECT * FROM EMPLOYEE
WHERE FIRSTNAME = 'JOHNSON' OR GENDER = 'GIRL,'

SELECT * FROM EMPLOYEE
WHERE FIRSTNAME = 'FEMI' OR GENDER = 'GIRL,'

-------UPDATE--------

SELECT * FROM Salary

UPDATE Salary
SET FIRSTNAME = 'Emeka'
where Staffid = 'AB212'

UPDATE SALARY SET STAFFID = 'AB550' WHERE STAFFID = 'AB254'

---SALARY = 5% (0.05)

UPDATE SALARY
SET SALARY = SALARY +(SALARY * 0.05)
WHERE STAFFID IN ('AB200', 'AB268','AB278')

UPDATE SALARY
SET SALARY = SALARY * 1.05
WHERE STAFFID IN ('AB200', 'AB268','AB278')

UPDATE SALARY
SET SALARY = SALARY * (1 + 0.05)
WHERE STAFFID IN ('AB200', 'AB268','AB278')

SELECT * FROM Salary

--------------JOIN-----------------------

INNER JOIN
LEFT JOIN
RIGHT JOIN
FULL JOIN

SELECT * FROM EMPLOYEE
SELECT * FROM SALARY
SELECT * FROM PAYMENT 

-----JOIN 2 TABLES----------------
 --EMPLOYEE  =  7 COLUMNS ( STAFFID, FIRSTNAME, GENDER, HIREDATE, STATE)
 --SALARY  = 6 COLUMNS (DEPARTMENT, SALARY)

 select employee.staffid, employee.firstname, employee.gender,
			 employee.hiredate,employee.state_of_origin, Salary.department,
			 Salary.salary
from employee
join Salary
on salary.Staffid = employee.staffid


-------inner join----------------
 select employee.staffid, employee.firstname, employee.gender,
			 employee.hiredate,employee.state_of_origin, Salary.department,
			 Salary.salary
from employee
join Salary
on salary.Staffid = employee.staffid



-------left join---------------------

 select employee.staffid, employee.firstname, employee.gender,
			 employee.hiredate,employee.state_of_origin, Salary.department,
			 Salary.salary
from employee
left join Salary
on salary.Staffid = employee.staffid

-------right join---------------
 select employee.staffid, employee.firstname, employee.gender,
			 employee.hiredate,employee.state_of_origin, Salary.department,
			 Salary.salary
from employee
right join Salary
on salary.Staffid = employee.staffid

-----full join---------------------

 select employee.staffid, employee.firstname, employee.gender,
			 employee.hiredate,employee.state_of_origin, Salary.department,
			 Salary.salary
from employee
full join Salary
on salary.Staffid = employee.staffid

------join 3 tables-------------------

select employee.staffid,
           employee.firstname, 
		   employee.gender,
		   employee.hiredate,
			employee.state_of_origin,
			Salary.department,
			 Salary.salary,
			 Payment.Account_No,
			 Payment.Bank,
			 Payment.Payment_Method
from employee
inner join Salary
on salary.Staffid = employee.staffid
inner join Payment
on Payment.staffid = salary.Staffid


-------------------
select p.staffid, 
           p.firstname, 
		   p.gender,
			 p.hiredate,
			 p.state_of_origin, 
			 a.department,
			 a.salary
from employee p
join Salary a
on a.Staffid = p.staffid

------union vs union all
create table  LITA_Store_Lekki (
customerID INT not null,
firstname varchar (max),
lastname  varchar (max),
Customer_gender nvarchar(max),
age int,
address varchar (max),
transaction_amount decimal (18, 4)
)

insert into LITA_Store_Lekki(customerID,firstname, lastname, Customer_gender, age, address, transaction_amount)
values ( 100, 'ramesh', 'abdukl', 'male', 24, '8 ahmed road', 2000.00),
   (121,'khilan', 'delhi', 'female',33, '9 delhi stree, okun', 1500.33),
    (111,'malik', 'delhi', 'female',39, '2 agriiv stree, makunn', 1999.33),
	 (110, 'kara', 'ogun', 'male',40, '10 hahroh road, ottawa', 3400.33),
	  (109,'sunkanmi','alade','male', 44, '9 orebiyi street, okun', 37575.00),
	   (108,'orobiyi', 'kekerekun', 'male',24, '88 malele road, ijebu', 6500.33),
	    (115,'igbati', 'bunmi', 'male',29, '90 delhi street, abeokunta', 1000.69),
		 (120,'mummry', 'akinbho','female', 25, '9 babaoluwa quarter, ipaha', 9000.50),
		  (119,'latana', 'jerremy', 'male',33, '9 ifelofudn quarter, ado', 15090.35),
		    (108,'orobiyi', 'kekerekun', 'male',24, '88 malele road, ijebu', 6500.33),
			 (111,'malik', 'delhi', 'female',39, '2 agriiv stree, makunn', 1999.33)
 
select * from LITA_Store_Lekki

create table  LITA_Store_Marina (
customerID INT not null,
firstname varchar (max),
lastname  varchar (max),
Customer_gender nvarchar(max),
age int,
address varchar (max),
transaction_amount decimal (18, 4)
)

insert into LITA_Store_Marina( customerID,firstname, lastname, Customer_gender, age,address, transaction_amount)
values ( 200,'Femk', 'abdukl',  'male',24, '9 old road', 88000.00),
   (201, 'isaiah', 'john','male', 55, '22 alaly stree, okun', 1590.33),
    ( 206,'emma', 'abu','male', 39, '7 ababa street, makunn', 6788.33),
	 (210, 'kara', 'ogun','female' ,40, '10 hahroh road, ottawa', 3400.33),
	  ( 211,'sunkanmi', 'osagie', 'female' ,49, '9 agric butstop street, okun', 89875.00),
	   (209,'oge', 'kunle', 'male',88, '10 iwo street, liverpool', 7860.33),
	    (204, 'igbayin', 'elizabeth', 'female',78, '100 kukuma street, epe', 89100.69),
		 (219,'mummry', 'akinbho','female', 25, '9 babaoluwa quarter, ipaha', 9000.50),
		  (220,'latana', 'jerremy','male', 33, '9 ifelofudn quarter, ado', 15090.35),
		  (216, 'marvelous', 'jerremy', 'female',96, '9 jo grey quarter, igbo', 53590.35),
		   (210, 'kara', 'ogun','female' ,40, '10 hahroh road, ottawa', 3400.33),
	  ( 211,'sunkanmi', 'osagie', 'female' ,49, '9 agric butstop street, okun', 89875.00),
	   ( 206,'emma', 'abu','male', 39, '7 ababa street, makunn', 6788.33)

-------union all------
	select * from LITA_Store_Lekki
	union all
	select * from LITA_Store_Marina

	------union-----------
select  customerID, Customer_gender, transaction_amount
from LITA_Store_Lekki
union 
select customerID, Customer_gender, transaction_amount
from LITA_Store_Marina


select * from LITA_Store_Lekki
union all
select * from LITA_Store_Marina

select 'Lekki Store' as [BRANCHES], customerID AS [CUSTOMERID],
           firstname as [FIRST NAME], lastname as [LAST NAME], 
		   customer_gender as [GENDER],age as AGE, address as [ADDRESS], 
		   transaction_amount as [TRANSACTION AMOUNT]
FROM LITA_Store_Lekki
UNION ALL
select 'Marina Store' as [BRANCHES], customerID AS [CUSTOMERID],
           firstname as [FIRST NAME], lastname as [LAST NAME], 
		    customer_gender as [GENDER], age as AGE, address as [ADDRESS], 
		   transaction_amount as [TRANSACTION AMOUNT]
from LITA_Store_Marina
