# SQL-Commands

create databse mydatabase;

 

use mydatabase;

 

CREATE TABLE Persons(

PersonID int,

FirstName varchar(255),

LastName varchar(255),

Address varchar (255),

City varchar(255)

);

 

 

INSERT INTO Persons(FirstName,LastName,Address,City )

VALUES('john','Doe','Delhi','Noida');

 

 

select*from Persons;

 

 

UPDATE Employee SET FirstName='marry' WHERE FirstName='john';

 

 

DELETE FROM persons WHERE FirstName='john';--delete only one record

 

 

DELETE FROM persons=======delete all records.

 

ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'anoop@1234';------authentication-

 

ALTER TABLE Employee

ADD DateOfBirth date;----add,delete ,modify in existing record--

 

with --id

 

CREATE TABLE Shop(

ShopId int auto_increment,

Name varchar(255),

Address varchar (255),

City varchar(255),

PRIMARY KEY(ShopId)

);

 

TRUNCATE TABLE shop;----------delete the all row in the table--

 

DROP TABLE shop-------delete the all structure and record in the table--

 

DELETE FROM shop-----delete the particuler row and data

 

DELETE from Shop where ShopId =7;

ROLLBACK;  

 

DELETE from Shop where ShopId =7;

COMMIT;

 

--front end questions---

--list in html -- ol,ul,dl 1-dt,2-dd --(description list..)

 

grid ,flex box--

---------------------------------------------------------------------------------------------------------------------------------

CREATE TABLE Customers(

customers_id int auto_increment,

last_name varchar (50),

first_name varchar (50),

favourite_website varchar(100),

PRIMARY KEY (customers_id)

);

 

INSERT INTO Customers (last_name,first_name,favourite_website) VALUES('doe','john','leetcode.com'),('marry','sun','hacker.com'),('laso','roky','hackerrank.com'),('sinha','joh','w3schools.com');

select* from Customers;

 

 

CREATE TABLE Orders(

order_id int auto_increment,

customer_id int (50),

order_date date,

primary key (order_id),

foreign key (customer_id) REFERENCES Customers (customers_id)

);

 

 

insert into Orders(customer_id, order_date) VALUES(2, '2016-04-18'),(3, '2017-05-19'),(4, '2018-09-22');

 

--------JOIN------

 

SELECT Customers.customers_id, Orders.order_id,Orders.order_date FROM Customers JOIN Orders ON Customers.customers_id=Orders.order_id;

------------------------------------------------------------------------------------------------------------------------------------------

 

-------procedures------

 

CREATE PROCEDURE SelectAllCustomers

AS

SELECT * FROM customers

GO;

 

EXEC SelectAllCustomers;

 

------------------------------------------------------------

 

---alter------------

 

alter table orders add address varchar(50);

alter table orders add country varchar(50) first;

alter table orders add pin_code int after customer_id;

alter table orders drop column pin_code;

 

----------------------------------------------

--select distinct--->> return only different value means dont allow duplicate value..

 

select distinct last_name, first_name from customers;-->>>return only different value no duplicacy

select last_name, first_name from customers;-->>return all

 

 

------------------------------------------------

 

select * from customers where Country="india" AND city="delhi";

 

=================================

==alises---gives the temp name--

 

select first_name as n1, last_name as l1 from customers;

 

=========================================

find first 3 records

 

select TOP 3 * from customers;

 

------------------------

like- search pattern in column--

 

select*from customers where first_name like 'j%';-- starting name wid j

 

select * from customers where first_name like '%y';--end name

 

 

-------------------------------------------------------------------------

 

triggers---

 

create table Passenger(

Name varchar (20),

id int(20),

address varchar(20),

charges int(10),

primary key(id)

);

select*from Passenger;

insert into Passenger values('gaurav',459,'delhi',5000);

insert into Passenger values('mahesh',460,'noida',7000);

insert into Passenger values('ravi',980,'gurgaon',9000);

insert into Passenger values('priyanshi',600,'kocchi',10000);

insert into Passenger values('sashi',496,'raipur',10000);

insert into Passenger values('xyz',799,'ranchi',10000);

 

create trigger flight

before insert

on Passenger

for each row

set new.charges=new.charges-2000;

 

syntax ----

 

create trigger trigger name

before|after

insert|delte|update

on table name

for each row

trigger body;

---

SHOW TRIGGERS;

 

----------------------------------------------------------------

 

all cmd

 

use mydatabase;

select* from orders;

alter table orders add address varchar(50);

alter table orders add country varchar(50) first;

alter table orders add pin_code int after customer_id;

alter table orders drop column pin_code;

delete from orders where order_id =1;

select* from persons;

select*from customers;

select distinct last_name, first_name from customers;

select last_name, first_name from customers;

select * from customers where Country="india" AND city="delhi";

 

INSERT INTO Persons(FirstName,LastName,Address,City )

VALUES('john','Doe','Delhi','Noida'),('xyz','kl','noida','gzb');

 

SELECT TOP 3 *  FROM customers;

SELECT TOP 3 * FROM customers;

SELECT * FROM customers

WHERE ROWNUM <= 3;

select first_name as n1, last_name as l1 from customers;

 

select*from customers where first_name like 'j%';

select * from customers where first_name like '%y';

select* from customers where last_name like 'e_%';

 

create table control(

Name varchar (20),

id int(20),

address varchar(20),

charges int(10),

primary key(id)

);

select*from Passenger;

select*from control;

insert into control values('gaurav',459,'delhi',5000);

insert into control values('mahesh',460,'noida',7000);

insert into control values('ravi',980,'gurgaon',9000);

insert into Passenger values('priyanshi',600,'kocchi',10000);

insert into Passenger values('sashi',496,'raipur',10000);

insert into Passenger values('xyz',799,'ranchi',10000);

 

create trigger flight

before insert

on Passenger

for each row

set new.charges=new.charges-2000;

 

SHOW TRIGGERS;

 

show databases;

select*from control;

set autocommit=0;

commit;

rollback;

savepoint a;

delete from control;

 

-----------------------------------------------------

TCL-- transaction control language--

commit--- save the data in pemanantly..

rollback-->> undo data..

savepoint-->> save the data in stage point..

 

savepoint savepoint name-- savepoint a;

use--__>>> rollback to a;

-------------------------------------------------------

 

2nd highest slary--

 

select * from sales order by salary desc limit 1,1;  2nd highest salary

select * from sales order by salary desc limit 2,1;  3rd highest salary

select * from sales order by salary desc limit 3,1;  4th highest salary

select * from sales order by salary desc;

 

select max(salary) from sales;

select min(salary) from sales;

select avg(salary) from sales;

---------------------------------------------------------

 

subquery--->>

 

==>>> select * from sales where salary =(

select max(salary) from sales);

 

-->>

 

select * from sales where salary <(

select max(salary) from sales) order by salary desc; -->> highest salary se jo minimum salary h wo sb print ho jayegi--

 

--another way to find the 2nd highest salry--

select max(salary) from sales where salary <(select max(salary) from sales);

 

 

---------------------------------------------------------------------------------------------

 

-------joins-----

 

create database joins;

show databases;

use joins;

create table employee(

emp_id int,

name varchar(50),

gender varchar(50),

age int,

salary int

);

select* from employee;

insert into employee values(206,"aman","male",24,350000);

insert into employee values(208,"tanisha","female",27,460000);

insert into employee values(203,"harpreet","female",29,890000);

insert into employee values(201,"ram","male",23,358000);

insert into employee values(205,"vishal","male",25,560000);

insert into employee values(204,"shubham","male",29,679000);

insert into employee values(207,"rohan","male",28,700000);

insert into employee values(210,"priyanka","female",27,650000);

 

create table emp_dept(

dept_id int,

emp_id int,

department varchar(50),

city varchar(50),

pincode int

);

 

select * from emp_dept;

insert into emp_dept values(21,205,"hr","banglore", 560076);

insert into emp_dept values(23,203,"developer","delhi", 87009);

insert into emp_dept values(23,206,"developer","pune", 476501);

insert into emp_dept values(22,207,"sales","banglore", 568077);

insert into emp_dept values(21,201,"hr","pune", 564487);

insert into emp_dept values(22,210,"sales","mumbai", 656009);

insert into emp_dept values(24,209,"analyst","ahemdabad", 678879);

insert into emp_dept values(25,200,"analyst","pune", 238977);

update emp_dept set empp_id = emp_id where city="";

 

/*write a query to display all the details from employee and emp_dept where the value of emp_id

in employee is equal to the value of emp_id in emp_dept*/


select * from employee inner join emp_dept on employee.emp_id = emp_dept.empp_id;

select  * from employee join emp_dept;

 

/*write a query to display all the details from employee and common

deatils from emp_dept by using left join keyword */


select * from employee left join emp_dept on employee.emp_id=emp_dept.empp_id;

select * from employee left outer join emp_dept on employee.emp_id=emp_dept.empp_id;


/*write a query to display all the details from employee and common

deatils from emp_dept by using right join keyword */


select * from employee right join emp_dept on employee.emp_id = emp_dept.empp_id;

select * from employee right outer join emp_dept on employee.emp_id = emp_dept.empp_id;

 

---full join./ full outer join-----

select * from employee full join emp_dept on employee.emp_id = emp_dept.empp_id;


 

--natural join---

types-

natural full join

natural left join

natural right join

natural inner join..-->> it is do not return the same column name in one table ..do not apply any condition..

 

--cross join---

-->> return the cartesian product means first table of every row multiply the 2nd table in every row..

 

eg- select * from employee cross join emp_dept;

 

---self join---

 

it is used to join a table to itself ..

eg-select e1.emp_id, e2.name, e1.salary from employee e1, employee e2 where e1.salary < e2.salary;

 

select e1.salary,e1.emp_id,e2.department, e2.city from employee e1 inner join emp_dept e2 on e1.emp_id=e2.empp_id where salary>400000;

 

-------------------------------------------------------------------

 

/* join three tables */

 

select employee.emp_firstname, employee.emp_lastname, department.dept_name from employee join emp_dept  on employee.emp_id = emp_dept.emp_id 

join department on department.emp_id =  emp_dept.emp_id;

 

-------------Rename table--------------------

rename table employee to myemployee;

 

syntax -: rename table oldtable name to newtable name;
