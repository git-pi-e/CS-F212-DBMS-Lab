# Lab 3

## Problem Statement

Convert the following E-R diagram of Internet book store database system to relational schema and apply DML, DQL commands to learn the concept of referential integrity
constraint.

## Constraints

**One customer can order many books but same book cannot be ordered by many customers on same date.** Orderbook relation keeps records of the existing books ordered by existing customers.

create database lab3;  
use lab3;

### Q1a

CREATE TABLE book (isbn VARCHAR(12) PRIMARY KEY, TITLE VARCHAR(50) NOT NULL, author VARCHAR(50) NOT NULL, qty_in_stock integer(10) NOT NULL, price decimal(6,2) NOT NULL, pubyear integer(4));

### Q1b

create table book( isbn varchar(12) primary key , title varchar(50) not null, author varchar(50) not null, qty_in_stock integer(10) not null, price decimal(6,2) not null, pubyear integer(4));  
select * from book;

### Q2a

create table customer(cid varchar(6) primary key, cname varchar(20) not null, address varchar(50), age integer(2));  

### Q2b

insert into customer values ('c1', 'Amar', '23, M.G. road, Ahmadabad', 20),('c2', 'Akbar', 'D-20, Sainivas, Mumbai', 19),('c3', 'Pooja', 'sector no. 23, Vashi, Mumbai', 24),('c4', 'Saloni', 'Hyderabad', 22),('c5', 'John', 'Pune, Shivajinagar', 18);  
select * from customer;

### Q3a

create table orderbook(oisbn varchar(12), ocid varchar(6), qty integer(10) not null, order_date Date);  
desc orderbook;  
alter table orderbook add constraint fkey1 Foreign key (ocid) references customer(cid);  
desc orderbook;  
alter table orderbook add constraint fkey2 Foreign key (oisbn) references book(isbn);  
desc orderbook;  

### Q3b

Satisfy yourself

desc orderbook;  

### Q3c

insert into orderbook values ('A1234', 'c2', 2, '2013-10-01'),
('A1234', 'c1', 1, '2012-07-02'),
('A1236', 'c3', 2, '2013-12-12'),
('A1236', 'c5', 4, '2012-12-30'),
('A1236', 'c1', 5, '2012-05-14'),
('A1238', 'c4', 10, '2012-06-15');

### Q4

### Q5

same as 3(a) but add :
alter table orderbook add constraint fkey1 Foreign key (ocid) references customer(cid) on delete cascade on update cascade;  
alter table orderbook add constraint fkey2 Foreign key (oisbn) references book(isbn) on delete cascade on update cascade;

### Q6

update book set isbn='A1239' where isbn='A1238';

### Q7


### Q8

select cr.cname,bk.title,ok.order_date from customer cr natural join book bk natural join orderbook ok where cr.cname like "A%";

### Q9
