# Library-Management-System-SQL
A project based on Library Management System. It keeps track of all information about books in the library, their cost, status and total number of books available in the library. 

## Create a database named library 
*CREATE DATABASE library;*  
*use library;*  

## TABLES in the database and the attributes, display all the tables after the  values updated in the table
 **1.	Branch 
Branch_no - Set as PRIMARY KEY  
Manager_Id  
Branch_address  
Contact_no;** 

*CREATE TABLE Branch
 ( Branch_no INT PRIMARY KEY auto_increment,
  Manager_Id INT not null, 
  Branch_address VARCHAR(255) not null,
  Contact_no VARCHAR(15) not null);* 
  
*INSERT INTO Branch (Manager_Id, Branch_address, Contact_no) VALUES  
  (101, '123 Main St, Kuttanad, Kerala', '9947561223'),   
  (102, '456 Elm St, Alappuzha, Kerala', '9947561226'),      
  (103, '789 Pine St, Kochi, Kerala', '9957561225'),      
  (104, '321 Oak St, Thiruvananthapuram, Kerala', '9934561224'),   
  (105, '654 Maple St, Kollam, Kerala', '9947581221'),   
  (106, '987 Birch St, Thrissur, Kerala', '9847561222'),   
  (107, '159 Cedar St, Palakkad, Kerala', '9347565223'),  
  (108, '753 Spruce St, Malappuram, Kerala', '9957561223'),  
  (109, '852 Willow St, Kannur, Kerala', '9947561238'),  
  (110, '951 Fir St, Kozhikode, Kerala', '9947552223');*  

  select * from branch;


**2.	Employee
Emp_Id – Set as PRIMARY KEY
Emp_name
Position
Salary 
Branch_no - Set as FOREIGN KEY and it refer Branch_no in Branch table**

*CREATE TABLE Employee  
  ( Emp_Id INT PRIMARY KEY auto_increment,  
  Emp_name VARCHAR(100) not null,  
  Position VARCHAR(50) not null,  
  Salary DECIMAL(10, 2) not null,  
  Branch_no INT,  
  FOREIGN KEY (Branch_no)  REFERENCES Branch(Branch_no) );* 

  *INSERT INTO Employee (Emp_name, Position, Salary, Branch_no)  
  VALUES ('Alice Johnson', 'Librarian', 45000.00, 1),  
  ('Raju Mathew', 'Assistant Librarian', 45000.00, 2),  
  ('Radha Krishnan', 'Archivist', 80000.00, 3), 
  ('David Johnson', 'Manager', 90000.00, 1),  
  ('Jomon Varghese', 'Technician', 38000.00, 2),  
  ('Kevin Dizsuza', 'Security', 30000.00, 3),  
  ('Abu Rasheed', 'Receptionist', 35000.00, 1),  
  ('Kiran Ravi', 'House keepimg', 28000.00, 2),  
  ('steve Brown', 'Researcher', 57000.00, 3),  
  ('Abdul Rahman', 'IT Support', 46000.00, 1);* 

*select * from employee;* 

**3.	Books 
ISBN - Set as PRIMARY KEY   
Book_title   
Category   
Rental_Price   
Status [Give yes if book available and no if book not available]   
Author   
Publisher** 

*CREATE TABLE Books ( ISBN VARCHAR(20) PRIMARY KEY,   
  Book_title VARCHAR(255) not null,  
  Category VARCHAR(50) not null,  
  Rental_Price DECIMAL(10, 2)not null,  
  Status VARCHAR(3) check (status ='Yes' or status='No'),  
  Author VARCHAR(100)not null,  
  Publisher VARCHAR(100)not null);*  

*INSERT INTO Books (ISBN, Book_title, Category, Rental_Price, Status, Author, Publisher) VALUES   
  ('978-3-16-148410-0', 'Introduction to SQL', 'Education', 575.00, 'Yes', 'John Doe', 'Tech Publishers'),  
  ('978-1-234-56789-7', 'Advanced SQL Techniques', 'Education', 750.00, 'No', 'Jane Smith', 'Knowledge Books'),  
  ('978-0-987-65432-1', 'Database Design Principles', 'Education', 1500.00, 'Yes', 'Mark Brown', 'Data Insights'),  
  ('978-3-16-148411-7', 'Python for Data Science', 'Education', 1000.00, 'Yes', 'Emily White', 'Science Press'),  
  ('978-1-234-56788-0', 'Machine Learning Basics', 'Technology', 1500.00, 'No', 'Laura Grey', 'Tech World'),  
  ('978-0-987-65431-4', 'Anna Karenina', 'Finction', 890.00, 'Yes', 'Leo Tolstoy', 'Fiction Press'),  
  ('978-3-16-148412-4', 'Pride and Prejudice', 'Fiction', 900.00, 'Yes', 'Jane Austen', 'Fiction Publishers'),  
  ('978-1-234-56787-3', 'War and Peace', 'Fiction', 899.00, 'No', 'Leo Tolstoy', 'Fiction Press'),   
  ('978-0-987-65430-7', 'The Alchemist ', 'Adventure', 650.00, 'Yes', 'Paulo Coelho', 'Sam publishers'),  
  ('978-3-16-148413-1', 'SQL Advanced Guide', 'Education', 1750.00, 'Yes', 'Evelyn King', 'Knowledge Books');* 

  *select * from books;*   

 **4.	Customer  
  Customer_Id - Set as PRIMARY KEY  
  Customer_name  
  Customer_address  
  Reg_date**  

  *CREATE TABLE Customer (Customer_Id INT PRIMARY KEY,   
  Customer_name VARCHAR(100)  not  null,   
  Customer_address VARCHAR(255) not null,   
  Reg_date DATE not null);* 

  *INSERT INTO Customer (Customer_Id, Customer_name, Customer_address, Reg_date) VALUES  
  (1, 'kannan Nair', '12 Cherry Ln, Kuttanad, Kerala', '2022-01-01'),  
  (2, 'Maya Ravi', '34 Maple St, Alappuzha, Kerala', '2020-02-20'),   
  (3, 'Frank Wilson', '56 Birch Ave, Kochi, Kerala', '2022-03-25'),   
  (4, 'Manu david', '78 Pine St, Thiruvananthapuram, Kerala', '2024-04-10'),   
  (5, 'Greeshma Anil', '90 Elm St, Kollam, Kerala', '2020-05-05'),   
  (6, 'Ali Hassan', '123 Cedar St, Thrissur, Kerala', '2021-06-15'),   
  (7, 'Abdul Salam', '45 Spruce St, Palakkad, Kerala', '2024-07-20'),   
  (8, 'Maria Michael', '67 Willow St, Malappuram, Kerala', '2020-08-30'),   
  (9, 'Suresh Nair', '89 Fir St, Kannur, Kerala', '2024-01-25'),  
  (10, 'Jaya Surendran', '101 Oak St, Kozhikode, Kerala', '2024-03-10');*  

  select * from customer;  

  **5.	IssueStatus  
  Issue_Id - Set as PRIMARY KEY   
  Issued_cust – Set as FOREIGN KEY and it refer customer_id in CUSTOMER table  
  Issued_book_name   
  Issue_date  
  Isbn_book – Set as FOREIGN KEY and it should refer isbn in BOOKS table**  

  *CREATE TABLE IssueStatus (Issue_Id INT PRIMARY KEY,  
  Issued_cust INT not null,  
  Issued_book_name VARCHAR(255) not null,  
  Issue_date DATE not null,  
  Isbn_book VARCHAR(20) not null,  
  FOREIGN KEY (Issued_cust) REFERENCES Customer(Customer_Id),  
  FOREIGN KEY (Isbn_book) REFERENCES Books(ISBN));*  

  *INSERT INTO IssueStatus (Issue_Id, Issued_cust, Issued_book_name,  
  Issue_date, Isbn_book) VALUES (1, 1, 'Introduction to SQL', '2024-01-20', '978-3-16-148410-0'),  
  (2, 2, 'Advanced SQL Techniques', '2024-02-25', '978-1-234-56789-7'),  
  (3, 3, 'Database Design Principles', '2024-03-30', '978-0-987-65432-1'),   
  (4, 4, 'Python for Data Science', '2024-04-15', '978-3-16-148411-7'),  
  (5, 5, 'Machine Learning Basics', '2024-05-10', '978-1-234-56788-0'),   
  (6, 6, 'Anna Karenina', '2024-06-05', '978-0-987-65431-4'),  
  (7, 7, 'Pride and Prejudice', '2024-07-20', '978-3-16-148412-4'),    
  (8, 8, 'War and Peace', '2024-08-25', '978-1-234-56787-3'),  
  (9, 9, 'The Alchemist ', '2024-09-15', '978-0-987-65430-7'),   
  (10, 10, 'SQL Advanced Guide', '2024-10-05', '978-3-16-148413-1');*  

  *select * from issuestatus;*

  
**6.	ReturnStatus  
Return_Id - Set as PRIMARY KEY  
Return_cust   
Return_book_name  
Return_date   
Isbn_book - Set as FOREIGN KEY and it should refer isbn in BOOKS table**  

*INSERT INTO ReturnStatus (Return_Id, Return_cust, Return_book_name,   
  Return_date, Isbn_book) VALUES   
  (1, 1, 'Introduction to SQL', '2024-02-01', '978-3-16-148410-0'),   
  (2, 2, 'Advanced SQL Techniques', '2024-03-01', '978-1-234-56789-7'),   
  (3, 3, 'Database Design Principles', '2024-04-01', '978-0-987-65432-1'),   
  (4, 4, 'Python for Data Science', '2024-05-01', '978-3-16-148411-7'),   
  (5, 5, 'Machine Learning Basics', '2024-06-01', '978-1-234-56788-0'),   
  (6, 6, 'Anna Karenina', '2024-07-01', '978-0-987-65431-4'),   
  (7, 7, 'Pride and Prejudice', '2024-08-01', '978-3-16-148412-4'),   
  (8, 8, 'War and Peace', '2024-09-01', '978-1-234-56787-3'),   
  (9, 9, 'The Alchemist', '2024-10-01', '978-0-987-65430-7'),   
  (10, 10, 'SQL Advanced Guide', '2024-11-01', '978-3-16-148413-1');*  

  select * from teturnstatus;  

  ## Write the following queries:  
  
**1.	Retrieve the book title, category, and rental price of all available books**  

*select book_title,category,rental_price from books
order by book_title;*


**2.	List the employee names and their respective salaries in descending order of salary**  

*select emp_name,salary from employee 
order by salary desc;*  

**3.	Retrieve the book titles and the corresponding customers who have issued those books**

*select customer_name,Issued_book_name from customer,IssueStatus where customer_id=Issued_cust;*

**4.	Display the total count of books in each category**  

*select category,count(book_title) from books group by category;*  

**5.	Retrieve the employee names and their positions for those employees whose salaries are above Rs.50,000**  

*select emp_name as 'Employee Name',position,salary from employee where  salary > 50000;* 

**6.	List the customer names who registered before 2022-01-01 and have not issued any books yet**  
*SELECT customer_id,customer_name,reg_date   
FROM customer   
WHERE reg_date<'2022-01-01' and customer_id NOT IN  
 ( SELECT issued_cust   
    FROM issuestatus  
    WHERE customer_id=issued_cust);*  

 **7.	Display the branch numbers and the total count of employees in each branch**  

 *select branch_no,count(emp_name)
  from employee group by branch_no;*  

  
*8.	Display the names of customers who have issued books in the month of June 2024**  

*select customer_name,customer_id,issue_date from customer,issuestatus  
where customer_id=issued_cust  
and issue_date between '2024-06-01' and '2024-06-30';***

**9.	Retrieve book_title from book table containing history**    
*select book_title,author from books  
  where category like 'adv%';*
  

**10.Retrieve the branch numbers along with the count of employees for branches having more than 3 employees**- 
  
*select branch_no,count(emp_name)  
  from employee group by branch_no   
  having count(emp_name)>3;** 

**11.	Retrieve the names of employees who manage branches and their respective branch addresses**  

*SELECT e.emp_name,e.branch_no,b.branch_address from employee e  
INNER JOIN branch b  ON e.branch_no = b.branch_no  
where e.position like '%manager';* 

**12.Display the names of customers who have issued books with a rental price higher than Rs. 25**

*SELECT  
customer_id,customer_name,  
book_title,rental_price  
FROM  
books  
JOIN  
issuestatus ON ISBN_book = isbn  
JOIN  
customer ON issued_cust = customer_id  
WHERE  
rental_price>25  
order by customer_id;*  









  

 



















  
  










  

  







  
  



