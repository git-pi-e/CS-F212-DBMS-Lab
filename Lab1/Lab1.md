# Lab 1

## Question 1

show databases;  
create database db212BITSStream;  
show databases;  
use db212BITSStream;  
desc albums;  
CREATE TABLE artists (ArtistID int PRIMARY KEY, Name varchar(20) NOT NULL, ActiveSince date NOT NULL, RetirementDate date, NumberOfFollowers int, Nationality varchar(20));  
desc artists;  
CREATE TABLE users (UserID int, UserName varchar(30), EmailID varchar(20) UNIQUE NOT NULL, MembershipCategory enum('P','F') DEFAULT 'F', PRIMARY KEY(UserID, UserName));  
desc users;  

## Question 3

### 1)

desc users;  
alter table users change MembershipCategory Account_Type enum('P','F') DEFAULT 'F';  
desc users;  

### 2)

desc artists;  
alter table artists drop column Nationality;
desc artists;  

### 3)

desc albums;  
alter table albums modify HoursStreamed decimal(6,2) DEFAULT 0;  
desc albums;

## Question 4

show create table albums;

## Question 5

INSERT INTO albums(AlbumID, AlbumName, ArtistName, HoursStreamed, Label, Genre, ReleaseDate) VALUES (39391, 'A Thousand Suns', 'Linkin Park', 128, 'Warner Bros', 'Rock', '2016-06-17');  
INSERT INTO albums(AlbumID, AlbumName, ArtistName, HoursStreamed, Label, Genre, ReleaseDate) VALUES (14573, 'Overexposed', 'Maroon 5',  452, 'A&M', 'Funk', '2016-11-11');  
INSERT INTO albums(AlbumID, AlbumName, ArtistName, HoursStreamed, Label, Genre, ReleaseDate) VALUES (14573, 'Overexposed', 'Maroon',  452, 'A&M', 'Funk', '2016-11-31'); // will show error  


