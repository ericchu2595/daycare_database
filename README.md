# daycare_database
Fall 2020 Database Project

I.    Business Scenario
 
A narrative description of the business used for the project or application being created. This should also include a description of the problem or opportunity being addressed.

Our daycare company has been operating in Brooklyn, New York for the past 10 years. Over the course of our business, we have realized that each child needs his/her proper attention, and that there are a lot of people, steps, and various moving parts in the process. Customers can sign up for certain programs, and plans, and it is our job to keep everything in order. We have been collecting information about our clients and children in an outdated way, in which we were heavily Excel and spreadsheet based. Now, as we continue to grow, we are looking for a new and more technological way to keep all of our information in an easy to navigate, and organized database. We are seeking to replace our previous manual method of tracking the business with a more efficient and scalable database where we can more easily store, manage, update, and retrieve our data. Through organizing our data in a more effective and automated way, we will be able to provide our customers with better service, and continue to grow our business as a whole. 

Identification of the information needs – what information would help solve the problem or allow one to take advantage of the opportunity.

The information needed in order to take advantage of this opportunity, and create an efficient database includes customer information like name, cell phone number, address, etc. We will also need to know what the parents (customers) are looking for in terms of taking care of their child, such as what program/services they would like their child to be in, which meal plan they would need, toys they would want, how long the child would be at the daycare, medical needs and other specifications. It's also important to keep track of the different vendors the daycare would need supplies from, such vendors for food, toys and managing finances. In addition, we need to monitor the Employee of the daycare, such as their hourly wages/salaries, home address and contact information among other things.

Initial list of entities (tables) that have been identified. This should come naturally from the above discussions.

Some entities may include, but are not limited to:
Guardian
Child
Program
Employee
Supplies
Vendors 


Distribution of duties for the project. List the names of each group member and what their primary role will be (e.g., systems analyst, application developer, documentation writer).

System analyst: Samuel Salzman
Application developer: Justin Joseph
SQL Codes: Sarah Natanov
Documentation writer: Eric Chu
Business Requirements: Katie Xu 


















II.   ER Model using UML Notation














Relationship Sentences:

One Guardian MAY BE (0) enrolling one or more (*) Children 0..*
One Child MUST BE (1) enrolled by one and only one (1) Guardian 1..1

One Child MUST BE (1) placed into one and only one (1) Program 1..1
One Program MAY BE (0) containing one or more (*) Children 0..*

One Program MUST BE (1) including one or more (*) Supplies 1..*
One Supply MAY BE (0) used in one or more (*) Programs 0..*

One Program MUST BE (1) employing one or more (*) Employee 1..*
One Employee MAY BE (0) working in one or more (*) Program 1..*

One Supply MAY BE (0) provided by one or more (*) Vendors 0..*
One Vendor MUST BE (1) providing one or more (*) Supplies 1..*

One Employee MUST BE (1) ordering from one or more (*) Vendors 1..*
One Vendor MAY BE (0) fulfilling an order from one or more (*) Employee 0..*


















III. Conversion to Relational Model

Relational Model:

Guardian (Guardian_ID (Key),  First_Name , Last_Name, Street_Address, City, State, Zip_Code,  Gender, SSN, Cell_Number, Home_Number, Enroll_Date)
Programs (Program_ID (Key), Program_Name, Program_Description, Age_Group, Program_Size, Days_Per_Week, Hours_Per_Day, Total_Days, Meal_Plan, Start_Date, End_Date)
Child (Child_ID (Key), First_Name, Last_Name, DOB, Gender, SSN, Age, Emergency_Contact, Food_Allergies, Meal_Preference, Napping_Hours, Start_Date, End_Date, Guardian_ID (Foreign Key), Program_ID (Foreign Key))
Supplies (Product_ID (Key), Product_Name, Date_Purchased, Supplier_Name, Cost, Quantity)
Program_Supplies (Program_ID (Foreign Key) (Key), Product_ID (Foreign Key) (Key))

Vendors (Vendor_ID (Key), Vendor_Name, Vendor_Description, Phone_Number, Street_Address, City, State, Zip_Code, Purchase_Date, Payment_Date)
Supplies_Vendors (Product_ID (Foreign Key) (Key), Vendor_ID (Foreign Key) (Key))
Employee (Employee_ID (Key), First_Name, Last_Name, Street_Address, City, State, Zip_Code, Gender, Pay_Rate, SSN, Start_Date, Job)
Employee_Vendors (Employee_ID (Foreign Key) (Key), Vendor_ID (Foreign Key) (Key))
Program_Employee (Program_ID (Foreign Key) (Key), Employee_ID (Foreign Key) (Key))	





IV.   Normalization

Normalization (Steps):
Child (Child_ID, First_Name, Last_Name, DOB, Gender, SSN, Age, Emergency_Contact, Food_Allergies, Meal_Preference, Napping_Hours, Start_Date, End_Date, GuardianID, Program_ID)
Key: Child_ID
FD1: Child_ID → First_Name, Last_Name, DOB, Gender, SSN, Age, Emergency_Contact, Food_Allergies, Meal_Preference, Napping_Hours, Start_Date, End_Date, Guardian_ID, Program_ID

Guardian (Guardian_ID,  First_Name, Last_Name, Street_Address, City, State, Zip_Code,  Gender, SSN, Cell_Number, Home_Number, Enroll_Date)
Key: Guardian_ID
FD1: Guardian_ID →  First_Name , Last_Name, Street_Address, City, State, Zip_Code,  Gender, SSN, Cell_Number, Home_Number, Enroll_Date

Supplies (Product_ID, Product_Name, Date_Purchased, Supplier_Name, Cost, Quantity)
Key: Product_ID
FD1: Product_ID → Product_Name, Date_Purchased, Supplier_Name, Cost, Quantity

Programs (Program_ID, Program_Name, Program_Description, Age_Group, Program_Size,  Days_Per_Week, Hours_Per_Day, Total_Days, Meal_Plan, Start_Date, End_Date)
Key: Program_ID
FD1: Program_ID → Program_Name, Program_Description, Age_Group, Program_Size,  Days_Per_Week, Hours_Per_Day, Total_Days, Meal_Plan, Start_Date, End_Date

Vendors (Vendor_ID, Vendor_Name, Vendor_Description, Phone_Number, Street_Address, City, State, Zip_Code, Purchase_Date, Payment_Date)
Key: Vendor_ID
FD1: Vendor_ID → Vendor_Name, Vendor_Description, Phone_Number, Street_Address, City, State, Zip_Code, Purchase_Date, Payment_Date

Employee (Employee_ID, First_Name, Last_Name, Street_Address, City, State, Zip_Code,  Gender, Pay_Rate, SSN, Start_Date, Job)
Key: Employee_ID 
FD1: Employee_ID → First_Name, Last_Name, Street_Address, City, State, Zip_Code, Gender, Pay_Rate, SSN, Start_Date, Job


























Final Set of Relations
Child (Child_ID, First_Name, Last_Name, DOB, Gender, SSN, Age, Emergency_Contact, Food_Allergies, Meal_Preference, Napping_Hours, Start_Date, End_Date, Guardian_ID, Program_ID)
Key: Child_ID
FD1: Child_ID → First_Name, Last_Name, DOB, Gender, SSN, Age, Emergency_Contact, Food_Allergies, Meal_Preference, Napping_Hours, Start_Date, End_Date, Guardian_ID, Program_ID

1NF: Meets the definition of a relation
2NF: No partial Key dependencies
3NF: No transitive dependencies


Guardian (Guardian_ID,  First_Name , Last_Name, Street_Address, City, State, Zip_Code,  Gender, SSN, Cell_Number, Home_Number, Enroll_Date)
Key: Guardian_ID
FD1: Guardian_ID →  First_Name , Last_Name, Street_Address, City, State, Zip_Code,  Gender, SSN, Cell_Number, Home_Number, Enroll_Date

1NF: Meets the definition of a relation
2NF: No partial Key dependencies
3NF: No transitive dependencies

Supplies (Product_ID, Product_Name, Date_Purchased, Supplier_Name, Quantity, Cost) 	
Key: Product_ID
FD1: Product_ID → Product_Name, Date_Purchased, Supplier_Name, Quantity, Cost

1NF: Meets the definition of a relation
2NF: No partial Key dependencies
3NF: No transitive dependencies

Programs (Program_ID, Program_Name, Program_Description, Age_Group, Program_Size,  Days_Per_Week, Hours_Per_Day, Total_Days, Meal_Plan, Start_Date, End_Date)
Key: Program_ID
FD1: Program_ID → Program_Name, Program_Description, Age_Group, Program_Size,  Days_Per_Week, Hours_Per_Day, Total_Days, Meal_Plan, Start_Date, End_Date

1NF: Meets the definition of a relation
2NF: No partial Key dependencies
3NF: No transitive dependencies

Vendors (Vendor_ID, Vendor_Name, Vendor_Description, Phone_Number, Street_Address, City, State, Zip_Code)
Key: Vendor_ID
FD1: Vendor_ID  → Vendor_Name, Vendor_Description, Phone_Number, Street_Address, City, State, Zip_Code

1NF: Meets the definition of a relation
2NF: No partial Key dependencies
3NF: No transitive dependencies

Employee(Employee_ID, First_Name, Last_Name, Street_Address, City, State, Zip_Code,  Gender, Pay_Rate, SSN, Start_Date, Job)
Key: Employee_ID 
FD1: Employee_ID → First_Name, Last_Name, Street_Address, City, State, Zip_Code, Gender, Pay_Rate, SSN, Start_Date, Job

1NF: Meets the definition of a relation
2NF: No partial Key dependencies
3NF: No transitive dependencies

Program_Supplies(Program_ID), Product_ID)

1NF: Meets the definition of a relation
2NF: No partial Key dependencies
3NF: No transitive dependencies

Supplies_Vendors (Product_ID, Vendor_ID)

1NF: Meets the definition of a relation
2NF: No partial Key dependencies
3NF: No transitive dependencies

Employee_Vendors (Employee_ID, Vendor_ID)

1NF: Meets the definition of a relation
2NF: No partial Key dependencies
3NF: No transitive dependencies

Program_Employee (Program_ID, Employee_ID)	
1NF: Meets the definition of a relation
2NF: No partial Key dependencies
3NF: No transitive dependencies

As you can see, all of our final set of relations are in 3NF. We first checked to see if our relations were in first normal form, which they are since all of our relations meet the definition of a relation. Second, we found that our relations were in second normal form since there were no partial key dependencies found in any of our relations. Finally, all of our relations were also in third normal form, since no transitive dependencies were found either. It is important to note that we originally had a functional dependency for our Guardian, Employee and Vendors relations of “Zip Code→City, State.” However, for the purposes of this small project, we denormalized City and State back to their original relations.










V.   Creating the Database Schema with SQL

CREATE SQL
CREATE TABLE Child
( 
Child_ID 			VARCHAR (25) NOT NULL, 
First_Name		VARCHAR (15) NOT NULL, 
Last_Name			VARCHAR (15) NOT NULL, 
DOB				DATE, 
Gender			VARCHAR (6) NOT NULL, 
SSN				VARCHAR (11) NOT NULL, 
Age				NUMBER, 
Emergency_Contact	VARCHAR (25), 	
Food_Allergies		VARCHAR (50), 
Meal_Preference	VARCHAR (50), 
Napping_Hours		VARCHAR (20), 
Start_Date		DATE, 
End_Date			DATE, 
Guardian_ID		VARCHAR(25) NOT NULL, 
Program_ID		VARCHAR(25) NOT NULL,
CONSTRAINT 	pk_Child
PRIMARY KEY (Child_ID)
);

CREATE TABLE Guardian 
(
Guardian_ID		VARCHAR(25) NOT NULL,
First_Name		VARCHAR(35) NOT NULL,
Last_Name			VARCHAR(35) NOT NULL,
Street_Address		VARCHAR(35),
City				VARCHAR(35),
State			VARCHAR(2),
Zip_Code			VARCHAR(12),
Gender			VARCHAR(6) NOT NULL,
SSN				VARCHAR(11) NOT NULL, 
Cell_Number		VARCHAR(11),
Home_Number		VARCHAR(35),
Enroll_Date		DATE,
CONSTRAINT 	pk_Guardian 
PRIMARY KEY (Guardian_ID)
);


CREATE TABLE Supplies (
Product_ID		VARCHAR(25) NOT NULL,
Product_Name	   	VARCHAR(20) NOT NULL,
Date_Purchased		DATE,
Supplier_Name		VARCHAR(20) NOT NULL,
Quantity			NUMBER,
Cost				NUMBER,
CONSTRAINT 	pk_Supplies 
PRIMARY KEY(Product_ID)
 );

CREATE TABLE Programs
(
Program_ID 		VARCHAR(25) NOT NULL,
Program_Name		VARCHAR(20) NOT NULL,
Program_Description VARCHAR(200) NOT NULL,
Age_Group 		VARCHAR(20) NOT NULL,
Program_Size  	 	NUMBER,
Days_Per_Week 		NUMBER,
Hours_Per_Day 	 	NUMBER,
Total_Days 		NUMBER,
Meal_Plan 		VARCHAR(20),
Start_Date 		DATE,
End_Date		 	DATE,
CONSTRAINT	pk_Programs
	PRIMARY KEY (Program_ID)
);

CREATE TABLE Vendors 
(
Vendor_ID			VARCHAR(20) NOT NULL,
Vendor_Name		VARCHAR(25) NOT NULL,
Vendor_Description  VARCHAR(250) NOT NULL,
Phone_Number		VARCHAR(11) NOT NULL,
Street_Address		VARCHAR(50) NOT NULL,
City      		VARCHAR(20) NOT NULL,
State    			VARCHAR(2) NOT NULL,
Zip_Code			VARCHAR(12) NOT NULL,
CONSTRAINT 	pk_Vendors 
PRIMARY KEY(Vendor_ID)
 );


CREATE TABLE Employee
(
Employee_ID		VARCHAR(25) NOT NULL,
First_Name		VARCHAR(25) NOT NULL, 
Last_Name			VARCHAR(25) NOT NULL, 
Street_Address		VARCHAR (50), 
City				VARCHAR(20), 
State			VARCHAR(2), 
Zip_Code			VARCHAR(10),  
Gender			VARCHAR(10),
Pay_Rate			NUMBER, 
SSN				VARCHAR(11) NOT NULL,
Start_Date		DATE,
Job				VARCHAR(50) NOT NULL,
CONSTRAINT 	pk_Employee
PRIMARY KEY(Employee_ID)
);

CREATE TABLE Program_Supplies
(
Program_ID		VARCHAR(35) NOT NULL,
Product_ID		VARCHAR(35) NOT NULL,
CONSTRAINT 	pk_Program_Supplies
PRIMARY KEY(Program_ID, Product_ID)
);






CREATE TABLE Supplies_Vendors
(
Product_ID		VARCHAR(35) NOT NULL,
Vendor_ID			VARCHAR(35) NOT NULL,
CONSTRAINT 	pk_Supplies_Vendors
PRIMARY KEY(Product_ID, Vendor_ID)
);

CREATE TABLE Employee_Vendors 
(
Employee_ID		VARCHAR(35) NOT NULL,	
Vendor_ID			VARCHAR(35) NOT NULL,
CONSTRAINT 	pk_Employee_Vendors
PRIMARY KEY(Employee_ID, Vendor_ID)
);

CREATE TABLE Program_Employee
(
Program_ID		VARCHAR(35) NOT NULL,
Employee_ID		VARCHAR(35) NOT NULL,
CONSTRAINT 	pk_Program_Employee
PRIMARY KEY(Program_ID, Employee_ID)
)	


ALTER SQL
ALTER TABLE Child
    ADD CONSTRAINT fk_Guardian
    FOREIGN KEY (Guardian_ID)
    REFERENCES Guardian (Guardian_ID) ;
 
ALTER TABLE Child
    ADD CONSTRAINT fk_Programs
    FOREIGN KEY (Program_ID)
    REFERENCES Programs (Program_ID);
 
ALTER TABLE Program_Supplies 
ADD CONSTRAINT fk_Program_Supplies
FOREIGN KEY (Program_ID) 
REFERENCES Programs (Program_ID);
 
ALTER TABLE Program_Supplies 
ADD CONSTRAINT fk_Program_Supplies2
FOREIGN KEY (Product_ID) 
REFERENCES Supplies (Product_ID);
 
ALTER TABLE Supplies_Vendors 
ADD CONSTRAINT fk_Supplies_Vendors
FOREIGN KEY (Product_ID) 
REFERENCES Supplies (Product_ID);
 
ALTER TABLE Supplies_Vendors 
ADD CONSTRAINT fk_Supplies_Vendors2
FOREIGN KEY (Vendor_ID) 
REFERENCES Vendors (Vendor_ID);
 
 
ALTER TABLE Employee_Vendors 
ADD CONSTRAINT fk_Employee_Vendors
FOREIGN KEY (Employee_ID)
REFERENCES Employee (Employee_ID);
 
ALTER TABLE Employee_Vendors 
ADD CONSTRAINT fk_Employee_Vendors2
FOREIGN KEY (Vendor_ID)
REFERENCES Vendors (Vendor_ID);
 
ALTER TABLE Program_Employee
ADD CONSTRAINT fk_Program_Employee
FOREIGN KEY (Program_ID) 
REFERENCES Programs (Program_ID);
 
ALTER TABLE Program_Employee
ADD CONSTRAINT fk_Program_Employee2
FOREIGN KEY (Employee_ID) 
REFERENCES Employee (Employee_ID);
 
 
 

INSERT Statements
INSERT INTO Programs (Program_ID, Program_Name, Program_Description, Age_Group, Program_Size,  Days_Per_Week, Hours_Per_Day, Total_Days, Meal_Plan, Start_Date, End_Date)
VALUES ( 'P101', 'Program A', 'Class will run from 10:30-3:30, where the children will play, do arts and crafts, and other fun activities. Nap time will be from 12:00-1:00. Children of this program will be ages 2 years old.', 2, 15, 4, 5, 172, 'Plan A and Plan B', '09/01/2020', '06/23/2021' )

INSERT INTO Programs (Program_ID, Program_Name, Program_Description, Age_Group, Program_Size,  Days_Per_Week, Hours_Per_Day, Total_Days, Meal_Plan, Start_Date, End_Date)
VALUES ( 'P102', 'Program B', 'Class will run from 10:30-3:30, where the children will play, do arts and crafts, and other fun activities. Nap time will be from 1:00-2:00. Children of this program will be ages 3 years old.', 3, 15, 4, 5, 172, 'Plan A and Plan B’, '09/01/2020', '06/23/2021' );

INSERT INTO Programs (Program_ID, Program_Name, Program_Description, Age_Group, Program_Size,  Days_Per_Week, Hours_Per_Day, Total_Days, Meal_Plan, Start_Date, End_Date)
VALUES ( 'P103', 'Program C', 'Class will run from 10:30-3:30, where the children will play, do arts and crafts, learn numbers and ABCs, and other fun activities. Nap time will be from 2:00-3:00. Children of this program will be ages 4 years old.', 4, 15, 4, 5, 172, 'Plan A and Plan B', '09/01/2020', '06/23/2021' );

INSERT INTO Programs (Program_ID, Program_Name, Program_Description, Age_Group, Program_Size,  Days_Per_Week, Hours_Per_Day, Total_Days, Meal_Plan, Start_Date, End_Date)
VALUES ( 'P104', 'Program D', 'Class will run from 10:30-3:30, where the children will play, do arts and crafts, and other fun activities. Nap time will be from 1:00-2:00. Children of this program will be ages 5 years old.', 5, 15, 4, 5, 172, 'Plan A and Plan B', '09/01/2020', '06/23/2021');

INSERT INTO Child (Child_ID, First_Name, Last_Name, DOB, Gender, SSN, Age, Emergency_Contact, Food_Allergies, Meal_Preference, Napping_Hours, Start_Date, End_Date, Guardian_ID, Program_ID)
VALUES ( 'C101', 'John', 'Stephenson', '03/22/2017', 'Male', '103-58-7984', 3, '9173471357', 'Peanuts', 'Plan A', 'From 1:00 - 2:00', '09/01/2020', '06/23/2021', 'G101', 'P102' );

INSERT INTO Child (Child_ID, First_Name, Last_Name, DOB, Gender, SSN, Age, Emergency_Contact, Food_Allergies, Meal_Preference, Napping_Hours, Start_Date, End_Date, Guardian_ID, Program_ID)
VALUES ( 'C102', 'Marc', 'Harris', '02/13/2018', 'Male', '713-47-0103', 2, '9176232291', 'Milk', 'Plan B', 'From 1:00 - 2:00', '09/01/2020', '06/23/2021', 'G102', 'P101' );

INSERT INTO Child (Child_ID, First_Name, Last_Name, DOB, Gender, SSN, Age, Emergency_Contact, Food_Allergies, Meal_Preference, Napping_Hours, Start_Date, End_Date, Guardian_ID, Program_ID)
VALUES ( 'C103', 'Lauren', 'Martin', '09/06/2017', 'Female', '020-11-4840', 3, '6161186023', 'Pollen and Cats', 'Plan B', 'From 1:00 - 2:00', '09/01/2020', '06/23/2021', 'G103', 'P102' ) ;

INSERT INTO Child (Child_ID, First_Name, Last_Name, DOB, Gender, SSN, Age, Emergency_Contact, Food_Allergies, Meal_Preference, Napping_Hours, Start_Date, End_Date, Guardian_ID, Program_ID)
VALUES ( 'C104', 'Rachel', 'Jones', '11/01/2016', 'Female', '013-32-4484', 4, '3472185812', 'None', 'Plan A', 'From 2:00 - 3:00', '09/01/2020', '06/23/2021', 'G104', 'P103' ) ;

INSERT INTO Child (Child_ID, First_Name, Last_Name, DOB, Gender, SSN, Age, Emergency_Contact, Food_Allergies, Meal_Preference, Napping_Hours, Start_Date, End_Date, Guardian_ID, Program_ID)
VALUES ( 'C105', 'Jason', 'Leonard', '04/10/2015', 'Female', '034-27-0911', 5, '2128124952', 'Strawberries and Almonds', 'Plan B', 'From 12:00 - 1:00', '09/01/2020', '06/23/2021', 'G105', 'P104' );



INSERT INTO Guardian(Guardian_ID,  First_Name , Last_Name, Street_Address, City, State, Zip_Code,  Gender, SSN, Cell_Number, Home_Number, Enroll_Date)
VALUES ('G101', 'Bob', 'Stephenson', '123 Willow Lane', 'New Hyde Park', 'NY', '11032', 'Male', '122-45-2215', '5162352912', '5162223968', '08/12/2020');

INSERT INTO Guardian(Guardian_ID,  First_Name , Last_Name, Street_Address, City, State, Zip_Code,  Gender, SSN, Cell_Number, Home_Number, Enroll_Date)
VALUES ('G102', 'James', 'Harris', '34 Manchester Road', 'Hoboken', 'NJ', '11508', 'Male', '063-12-5521', '7182341149', '7182486691', '07/29/2020');

INSERT INTO Guardian(Guardian_ID,  First_Name , Last_Name, Street_Address, City, State, Zip_Code,  Gender, SSN, Cell_Number, Home_Number, Enroll_Date)
VALUES ('G103', 'Grace', 'Martin', '24 Lexington Avenue', 'New York', 'NY', '11056', 'Female', '203-12-7853', '2051635933', '2054751922', '08/17/2020');

INSERT INTO Guardian(Guardian_ID,  First_Name , Last_Name, Street_Address, City, State, Zip_Code,  Gender, SSN, Cell_Number, Home_Number, Enroll_Date)
VALUES ('G104', 'Raymond', 'Jones', '2782 Randall Avenue', 'New Hyde Park', 'NY', '11032', 'Male', '458-21-5677', '5168631294', '5164529285', '06/11/2020');

INSERT INTO Guardian(Guardian_ID,  First_Name , Last_Name, Street_Address, City, State, Zip_Code,  Gender, SSN, Cell_Number, Home_Number, Enroll_Date)
VALUES ('G105', 'Stephanie', 'Leonard', '146 Royal Way', 'Williston Park', 'NY', '11059', 'Female', '139-49-2211', '5164599921', '5161385592', '07/18/2020');




INSERT INTO Vendors (Vendor_ID, Vendor_Name, Vendor_Description, Phone_Number, Street_Address, City, State, Zip_Code)
VALUES ('V101', 'Herman Miller', 'Sells a variety of office equipment for school and work environments', '2456132256', '125 Smith Lane', 'New York', 'NY', '11023');

INSERT INTO Vendors (Vendor_ID, Vendor_Name, Vendor_Description, Phone_Number, Street_Address, City, State, Zip_Code)
VALUES ('V102', 'Crayola', 'Sells all different types of crayons, color pencils and markers', '2112395849', '39 Hobbit Avenue', 'Whippany', 'NJ', '21059');

INSERT INTO Vendors (Vendor_ID, Vendor_Name, Vendor_Description, Phone_Number, Street_Address, City, State, Zip_Code)
VALUES ('V103', 'Scholastic', 'Home to all of your reading and writing needs for young children', '7182863419', '21 Woodbridge Lane', 'Hoboken', 'NJ', '11356');

INSERT INTO Vendors (Vendor_ID, Vendor_Name, Vendor_Description, Phone_Number, Street_Address, City, State, Zip_Code)
VALUES ('V104', 'Staples', 'Sells all office and school needs, for both students and professionals', '5162921192', '26 Johnson Boulevard', 'Garden City', 'NY', '11040');

INSERT INTO Vendors (Vendor_ID, Vendor_Name, Vendor_Description, Phone_Number, Street_Address, City, State, Zip_Code)
VALUES ('V105', 'Toys R Us', 'Sells a variety of toys and educational equipment for young children', '7459992128', '148 Devonshire Road', 'New York', 'NY', '12192');

INSERT INTO Supplies (Product_ID, Product_Name, Date_Purchased, Supplier_Name, Quantity, Cost) 	
VALUES ( 'S101', 'Office Chair', '12/22/2015', 'Herman Miller', 7, 3000 );

INSERT INTO Supplies (Product_ID, Product_Name, Date_Purchased, Supplier_Name, Quantity, Cost) 	
VALUES ( 'S102', 'Crayons', '08/11/2016', 'Crayola', 100, 250);

INSERT INTO Supplies (Product_ID, Product_Name, Date_Purchased, Supplier_Name, Quantity, Cost) 	
VALUES ( 'S103', 'Books', '08/11/2016', 'Scholastic', 100, 500);

INSERT INTO Supplies (Product_ID, Product_Name, Date_Purchased, Supplier_Name, Quantity, Cost) 	
VALUES ( 'S104', 'Copy Paper Ream', '08/12/2016', 'Staples', 50, 170);

INSERT INTO Supplies (Product_ID, Product_Name, Date_Purchased, Supplier_Name, Quantity, Cost) 	
VALUES ( 'S105', 'Toys', '08/12/2016', 'Toys R Us', 50, 250);

INSERT INTO Employee (Employee_ID, First_Name, Last_Name, Street_Address, City, State, Zip_Code, Gender, Pay_Rate, SSN, Start_Date, Job)
VALUES ('E001', 'Sara', 'Davis', '55 Coral Lane', 'Bayonne', 'NJ', '07002', 'Female', 25, '765-323-2211', '12/06/2005', 'Receptionist');

INSERT INTO Employee (Employee_ID, First_Name, Last_Name, Street_Address, City, State, Zip_Code, Gender, Pay_Rate, SSN, Start_Date, Job)
VALUES ('E002', 'Beth', 'Harmon', '221 Ford Avenue', 'Newark', 'NJ', '07114', 'Female', 42, '663-122-0941', '09/15/2009', 'Instructor');

INSERT INTO Employee (Employee_ID, First_Name, Last_Name, Street_Address, City, State, Zip_Code, Gender, Pay_Rate, SSN, Start_Date, Job)
VALUES ('E003', 'Jordan', 'Martinez', '45 Heidi Drive', 'Woodbridge', 'NJ', '08863', 'Male', 30, '123-432-7877', '04/22/1999', 'Instructor');




INSERT INTO Employee (Employee_ID, First_Name, Last_Name, Street_Address, City, State, Zip_Code, Gender, Pay_Rate, SSN, Start_Date, Job)
VALUES ('E004', 'Katrina', 'Kim', '377 Greenwich St', 'New York', 'NY', '10013', 'Female', 57, '033-215-5430', '01/24/2002', 'Nurse');

INSERT INTO Employee (Employee_ID, First_Name, Last_Name, Street_Address, City, State, Zip_Code, Gender, Pay_Rate, SSN, Start_Date, Job)
VALUES ('E005', 'Matthew', 'Mitchell', '34 Brown Blvd', 'Jersey City', 'NJ', '07304', 'Male', 36, '434-129-6544', '02/12/2000', 'Janitor');

INSERT INTO Program_Supplies (Program_ID, Product_ID)
VALUES( 'P101', 'S101');

INSERT INTO Program_Supplies (Program_ID, Product_ID)
VALUES('P103', 'S102');

INSERT INTO Program_Supplies (Program_ID, Product_ID)
VALUES('P102', 'S104');

INSERT INTO Program_Supplies (Program_ID, Product_ID)
VALUES('P101', 'S103');

INSERT INTO Program_Supplies (Program_ID, Product_ID)
VALUES('P104', 'S105');

INSERT INTO Employee_Vendors (Employee_ID, Vendor_ID)
VALUES ('E001', 'V101');

INSERT INTO Employee_Vendors (Employee_ID, Vendor_ID)
VALUES ('E002', 'V102');

INSERT INTO Employee_Vendors (Employee_ID, Vendor_ID)
VALUES ('E003', 'V103');


INSERT INTO Employee_Vendors (Employee_ID, Vendor_ID)
VALUES ('E004', 'V104');

INSERT INTO Employee_Vendors (Employee_ID, Vendor_ID)
VALUES ('E005', 'V105');

INSERT INTO Supplies_Vendors(Product_ID, Vendor_ID)
VALUES ('S101', 'V101');

INSERT INTO Supplies_Vendors(Product_ID, Vendor_ID)
VALUES ('S102', 'V102');

INSERT INTO Supplies_Vendors(Product_ID, Vendor_ID)
VALUES ('S103', 'V103');

INSERT INTO Supplies_Vendors(Product_ID, Vendor_ID)
VALUES ('S104', 'V104');

INSERT INTO Supplies_Vendors(Product_ID, Vendor_ID)
VALUES ('S105', 'V105');

INSERT INTO Program_Employee(Program_ID, Employee_ID)	
VALUES ('P101', 'E001');

INSERT INTO Program_Employee(Program_ID, Employee_ID)	
VALUES ('P102', 'E002');

INSERT INTO Program_Employee(Program_ID, Employee_ID)	
VALUES ('P103', 'E003');

INSERT INTO Program_Employee(Program_ID, Employee_ID)	
VALUES ('P104', 'E004');

INSERT INTO Program_Employee(Program_ID, Employee_ID)	
VALUES ('P105', 'E005');



VI.   Database Application

Navigation Form

The Navigation Form provided here links together our forms and reports in a user-friendly manner. The user can choose which form or report he/she wants to access by clicking on the tabs across the top of the form. This Navigation form can be selected from the list of the forms on the left tab along Access.













Forms

The Child Data Entry Form is used to add a new child to the daycare database with a new Child ID and input their related information like date of birth, allergies, etc. The Child can also be selected from the Child_ID combo box. The user will be able to save their changes by clicking the ‘save’ button, they will be able to fill out a new vendor form by clicking the ‘new’ button and once they’re done with this form they can close it by clicking the ‘close’ button.






The Employee Data Entry Form is used to look up Employees, update information, and add a new Employee. The user can input other Employee information like their home address, hourly pay rate, start date, job title, and other personal information. The user will be able to save their changes by clicking the ‘save’ button, they will be able to fill out a new vendor form by clicking the ‘new’ button and once they’re done with this form they can close it by clicking the ‘close’ button.



The purpose of the Guardian Data Entry Form is to enter different Guardian information including a new Guardian ID, first and last name, living information, and personal information. In addition, you can also view existing guardians, and the child/children associated with them. This is provided through the creation of the Child_Guardian Subform. The Guardian_ID and the Child_ID can be selected from their respective combo boxes. The user will be able to save their changes by clicking the ‘save’ button, they will be able to fill out a new vendor form by clicking the ‘new’ button and once they’re done with this form they can close it by clicking the ‘close’ button.



The Programs Form is used to query and update attributes of the programs. The user can insert all of the necessary information for each given program including its name, description, and other information about the program. This form can also be used to view the children enrolled in a specific program. This is provided through the creation of the Child_Program Subform. The Program_ID and the Child_ID can be selected from their respective combo boxes. The user will be able to save their changes by clicking the ‘save’ button, they will be able to fill out a new vendor form by clicking the ‘new’ button and once they’re done with this form they can close it by clicking the ‘close’ button.


The Supplies Data Entry Form records the supplies ordered including date purchased, quantity, and costs. The Daycare can elect to choose which Vendor to order from, along with how many of their products they’d like to purchase for use at the Daycare. The Product_ID can be selected from the combo box. The user will be able to save their changes by clicking the ‘save’ button, they will be able to fill out a new vendor form by clicking the ‘new’ button and once they’re done with this form they can close it by clicking the ‘close’ button.



The Vendors Forms lists and updates information related to the vendors. The user can enter the Vendor Name, Vendor Description, Phone Number, Street Address, City, State and Zip Code in their appropriate fields. The user will also be able to pick the appropriate Vendor_ID from the drop down option. The user will be able to save their changes by clicking the ‘save’ button, they will be able to fill out a new vendor form by clicking the ‘new’ button and once they’re done with this form they can close it by clicking the ‘close’ button.

















Reports


The Child Guardian report shows all registered children’s guardian’s contact information.

Based on query:

SELECT c.Child_ID, c.First_Name AS Child_First_Name, c.Last_Name AS Child_Last_Name, c.Age, c.Gender, g.Guardian_ID, g.First_Name AS Guardian_First_Name, g.Last_Name AS Guardian_Last_Name, g.Cell_Number, g.Street_Address
FROM Child AS c LEFT JOIN Guardian AS g ON c.Guardian_ID = g.Guardian_ID
ORDER BY c.First_Name;



This report lists each of the children’s SSN, allergies, emergency contact and the program that they are in.

Based on query: 

SELECT Child.First_Name, Child.Last_Name, Child.SSN, Child.Emergency_Contact, Child.Food_Allergies, Child.Program_ID AS Child_Program_ID
FROM Child;



This report provides the total salary of each employee for the entire length of the year. The report lists each employee’s name, total hours worked, pay rate, and their total salary. Assuming each employee works their total hours of 860 for the year, receiving their hourly pay rate, their total salary will be the result in the rightmost column. 

Based on query: 

SELECT DISTINCT e.First_Name, e.Last_Name, (p.Hours_Per_Day * p.Total_Days) AS Total_Hours, e.pay_rate AS Pay_Rate, (Total_Hours * e.Pay_Rate) AS Total_Salary
FROM Employee AS e, Programs AS p;

.


This report shows the total costs of the supplies purchased. This was calculated through multiplying the quantity of each supply order times the cost of each item of supplies. 

Based on query:

SELECT Product_Name, (Quantity*Cost) AS Total_Cost
FROM Supplies
ORDER BY Product_Name;



This report shows all of the children in P102.

Based on query:
SELECT Child_ID, First_Name, Last_Name, Program_ID
FROM Child
WHERE Program_ID = 'P102';





VII. Conclusions

Software and services used:
Zoom
Whatsapp for messaging
Lucidchart for ER model
Microsoft Access
Google Drive
Outlook for sending emails and files

Our experience with the project was smooth and collaborative at first but became a little bit of a struggle once we began implementing the database. The easiest steps were coming up with the business proposal, designing the ER model, and creating the tables. Inserting the data into the tables was not as effortless as we thought and it was even more difficult to write up queries, forms and reports. Though this project was tough, we learned many practical skills for creating a database from scratch, such as forming the relationships between entities, writing create and insert statements into Access, and using the software to filter data. If we were to redo the project, we would probably create more distinct, connected relationships with less attributes to simplify things and make sure all the SQL is accurate beforehand. With an improved foundation, the database would be more efficient and prone to less errors.
