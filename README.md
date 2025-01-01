**Library Management System (CS504 Project)**

Overview
This project is a database management system for a public library. The system is designed to efficiently manage library resources such as books, magazines, e-books, audiobooks, and other materials. It also handles membership information, borrowing and returning processes, and generates reports for analytics. The project uses PostgreSQL for database implementation and focuses on database design, querying, and manipulation.
Features:
•	Materials Management: Tracks materials like books, magazines, e-books, and audiobooks.
•	Membership Management: Manages member details, including borrowing history.
•	Borrowing System: Allows members to borrow materials, with tracking of borrow and return dates.
•	Reporting & Analytics: Generates reports on library usage, popular materials, and more.
Entities and Relationships:
•	Materials: Stores information about books, magazines, and other items.
•	Catalog: Information about the location and availability of materials.
•	Genres: Categorizes materials by genre.
•	Members & Staff: Manages member and staff details, including borrow histories and job titles.
•	Borrow Transactions: Stores borrowing details for materials.
Database Schema
ER Diagram:
Include the Entity-Relationship (ER) diagram here that outlines the relationships between the various entities in the system. You can either attach an image of the diagram or include it as a link.
Tables:
•	Material: Stores information on each library material.
•	Catalog: Stores catalog details of materials.
•	Genre: Represents genres for materials.
•	Borrow: Manages the borrowing transactions.
•	Author: Stores information about authors.
•	Authorship: Represents the relationship between authors and materials.
•	Member: Stores member details.
•	Staff: Stores staff details.
Setup
Requirements:
•	PostgreSQL (version 12+)
•	SQL Client (e.g., pgAdmin, DBeaver)
•	A text editor (e.g., VSCode, Sublime Text)
Usage
Common Queries
Here are some example queries you can use to interact with the library management system:
1.	Which materials are currently available in the library?
SELECT * FROM Material WHERE Material_ID NOT IN (SELECT Material_ID FROM Borrow WHERE Return_Date IS NULL);
2.	Which materials are overdue?
SELECT Material.Title, Borrow.Borrow_Date, Borrow.Due_Date
FROM Borrow
JOIN Material ON Borrow.Material_ID = Material.Material_ID
WHERE Borrow.Due_Date < '2023-01-04' AND Borrow.Return_Date IS NULL;
3.	How many books has the author Lucas Piki written?
SELECT COUNT(*) FROM Authorship
JOIN Author ON Authorship.Author_ID = Author.Author_ID
WHERE Author.Name = 'Lucas Piki';
4.	How do you update a returned book?
UPDATE Borrow
SET Return_Date = '2023-01-04'
WHERE Material_ID = (SELECT Material_ID FROM Material WHERE Title = 'Harry Potter and the Philosopher\'s Stone')
  AND Return_Date IS NULL;
5.	How do you delete a member and all related records?
DELETE FROM Borrow WHERE Member_ID = (SELECT Member_ID FROM Member WHERE Name = 'Emily Miller');
DELETE FROM Member WHERE Name = 'Emily Miller';
Example Usage of System:
•	A library staff member can check out materials for a member.
•	The system will track borrowing dates and due dates.
•	Reports can be generated to analyze library usage, such as which books are borrowed the most or which genres are the most popular.
Tests
The system has been tested with sample data to ensure proper functionality. Below is a list of test queries:
•	Query 1: Check materials that are currently available in the library.
•	Query 2: Identify materials that are overdue.
•	Query 3: Display the top 10 most borrowed materials.
•	Query 4: Count the number of books written by a specific author.
•	Query 5: List materials borrowed in a specific date range.
Documentation
The project includes the following documentation:
•	ER Diagram: Visual representation of the database schema.
•	SQL Code: DDL (Data Definition Language) and DML (Data Manipulation Language) queries used for database creation and data population.
•	Sample Queries: Examples of common SQL queries to interact with the system.

