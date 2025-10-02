# Creating-Views
# In this repo, i have created 2 tables Student and Teacher having a common column between them and created views for multiple sets and shown how to join two tables in view

create database class;
use class;
create table Student(
Sid int,
Sname varchar(20),
perc int,
Gender varchar(6),
Branch varchar(8));
insert into Student(Sid,Sname,perc,Gender,Branch) values
(101,'Hari',99,'male','CSE'),(102,'Ramya',90,'female','ECE'),(103,'Sandeep',95,'male','CSE'),(104,'Sony',78,'female','CSE'),(105,'Saradhi',88,'male',
'CIVIL'),(106,'Yamini',98,'female','ECE'),(107,'Ramu',60,'male','ECE')

-- create a view for student who are only from cse branch
create view CSE_Students as 
select * from Student where Branch='CSE'; 

-- show students after creating view for cse students
select * from CSE_Students ;

-- creating a view for ECE branch students
create view ECE_Student as
select * from Student where Branch='ECE';

-- show students from ECE branch after creating view
select * from ECE_Student;

-- changing percentage of student who have student id=103
update Student set perc=96 where sid=103;

-- after changing data on Student table belongs to cse, it will make automatic change on view table CSE_Student
select * from CSE_Students;

-- changing percentage of student who have student id=107
update ECE_Student set perc=62 where sid=107;

-- after changing data on ECE_Student  it will make automatic change on Student table which belongs to ECE
select * from Student;

-- creating a table Teacher
create table Teacher(
Tid varchar(3),
Tname varchar(20),
Gender varchar(8),
Branch varchar(20));


insert into Teacher(Tid,Tname,Gender,Branch) values
('T01','Sunil','male','CSE'),('T02','Sumona','female','CSE'),('T03','Samir','male','ECE'),('T04','Suresh','male','ECE'),('T05','Rama','female','CIVIL')


-- create a view for both student and teacher and join them by inner join
create  view Student_Teacher as 
select S.Branch,
 S.Sname as Student_name,
 S.perc as Student_percentage,
 S.Gender as Student_gender,
 T.Tname as Teacher_name,
T.Gender as Teacher_gender,
T.Branch as Teacher_Branch
 from Student S 
inner join Teacher  T on S.Branch = T.Branch;

-- show view table of joined student and teacher 
select * from Student_Teacher;




