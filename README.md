# Train Ticket Reservation System 
<!-- - Youtube video for local setup of similar project: https://www.youtube.com/watch?v=mLFPodZO8Iw -->
<!-- - Live Url: https://traintickets.herokuapp.com <br>  -->
<!-- - Login Credentials: admin/admin -->

### About:
This project is about the Train-Ticket-Reservation-System which is used to view Train Schedule, search trains, Seat availability, Train timings. We can also enquire about fare of different trains. We can get information about train between two stations. We can book seats online. This provides a safe and secure seat reservation system. 
### Online Train Information and Reservation
<span style="color:blue">**This Website is built for following purpose:-**</span>
- View Trains Schedule
- Search Trains
- Seat Availability
- Train Timings
- Fare Enquiry
- Trains Between Stations
- Booking seats online.
- Login and Logout Security
- Password Changes
- Payment Gateway
- Ticket Booking History

<span style="color:blue">**The Admin have the following access to this website:-**</span>
- Login
- Add Trains
- Update Trains
- Remove  or cancle Trains
- View Trains
- Profile Edit
- Logout

<span style="color:blue">**The Users have the following Access:-**</span>
- Register
- Login
- View Trains
- Check Seat Availability
- Search Trains
- Train Avaiablity and Fare Between Stations
- Books Tickets
- View Booking History
- View Profile
- Update Profile
- Change Password
- Logout

### Technologies used:-
1. Front-End Development:
- HTML
- CSS
- Bootstrap

2. Back-End Development
- Java [J2EE]
- JDBC
- Servlet
- MySQL ( SQL )

### ==== Software And Tools Required ======
- : Git 
- : Java JDK 8+ 
- : Eclipse EE 
- : Apache Maven 
- : Tomcat v8.0+ 
- : MySQL database

### ========== Dummy Database Initialization ===========

STEP 1: Open Mysql database

STEP 2: Login and connect to database using administrator username and password

STEP 3 : Create a new user:

STEP 4: Now execute the below sql query in query tools in created database

```SQL

-- Create the user
CREATE USER 'RESERVATION'@'%' IDENTIFIED BY 'Manager@123';

-- Grant all privileges (equivalent to DBA role in Oracle)
GRANT ALL PRIVILEGES ON *.* TO 'RESERVATION'@'%' WITH GRANT OPTION;

-- Apply the changes
FLUSH PRIVILEGES;

CREATE TABLE CUSTOMER (	
    MAILID VARCHAR(40) PRIMARY KEY, 
    PWORD VARCHAR(20) NOT NULL, 
    FNAME VARCHAR(20) NOT NULL, 
    LNAME VARCHAR(20), 
    ADDR VARCHAR(100), 
    PHNO BIGINT NOT NULL  -- MySQL does not have NUMBER(12), so use BIGINT
);

CREATE TABLE ADMIN (	
    MAILID VARCHAR(40) PRIMARY KEY, 
    PWORD VARCHAR(20) NOT NULL, 
    FNAME VARCHAR(20) NOT NULL, 
    LNAME VARCHAR(20), 
    ADDR VARCHAR(100), 
    PHNO BIGINT NOT NULL
);

CREATE TABLE TRAIN (	
    TR_NO INT PRIMARY KEY, 
    TR_NAME VARCHAR(70) NOT NULL, 
    FROM_STN VARCHAR(20) NOT NULL, 
    TO_STN VARCHAR(20) NOT NULL, 
    SEATS INT NOT NULL, 
    FARE DECIMAL(6,2) NOT NULL 
);

CREATE TABLE HISTORY (	
    TRANSID VARCHAR(36) PRIMARY KEY, 
    MAILID VARCHAR(40), 
    TR_NO INT, 
    DATE DATE, 
    FROM_STN VARCHAR(20) NOT NULL, 
    TO_STN VARCHAR(20) NOT NULL, 
    SEATS INT NOT NULL, 
    AMOUNT DECIMAL(8,2) NOT NULL,
    FOREIGN KEY (MAILID) REFERENCES CUSTOMER(MAILID),
    FOREIGN KEY (TR_NO) REFERENCES TRAIN(TR_NO)
);

INSERT INTO ADMIN VALUES ('admin@demo.com', 'admin', 'System', 'Admin', 'Demo Address 123 colony', 9874561230);
INSERT INTO CUSTOMER VALUES ('sajal@demo.com', 'sajal', 'Sajal', 'Garg', 'Kolkata, West Bengal', 954745222);

INSERT INTO TRAIN VALUES (10001, 'JODHPUR EXP', 'HOWRAH', 'JODHPUR', 152, 490.50);
INSERT INTO TRAIN VALUES (10002, 'YAMUNA EXP', 'GAYA', 'DELHI', 52, 550.50);
INSERT INTO TRAIN VALUES (10003, 'NILANCHAL EXP', 'GAYA', 'HOWRAH', 92, 451.00);
INSERT INTO TRAIN VALUES (10004, 'JAN SATABDI EXP', 'RANCHI', 'PATNA', 182, 550.00);
INSERT INTO TRAIN VALUES (10005, 'GANGE EXP', 'MUMBAI', 'KERALA', 12, 945.00);
INSERT INTO TRAIN VALUES (10006, 'GARIB RATH EXP', 'PATNA', 'DELHI', 1, 1450.75);

INSERT INTO HISTORY VALUES ('BBC374-NSDF-4673', 'sajal@demo.com', 10001, '2024-02-02', 'HOWRAH', 'JODHPUR', 2, 981.00);
INSERT INTO HISTORY VALUES ('BBC375-NSDF-4675', 'sajal@demo.com', 10004, '2024-01-12', 'RANCHI', 'PATNA', 1, 550.00);
INSERT INTO HISTORY VALUES ('BBC373-NSDF-4674', 'sajal@demo.com', 10006, '2024-07-22', 'PATNA', 'DELHI', 3, 4352.25);
```
STEP 5: Now Execute the below query one by one to check if the tables are created successfully
```SQL
SELECT * FROM ADMIN;
SELECT * FROM CUSTOMER;
SELECT * FROM TRAIN;
SELECT * FROM HISTORY;

```
Note: If any of the above commands fails, please try to fix it first and then proceed to next step
	
### ====== Importing and Running the Project Through Eclipse EE ===========
Step 0: Open Eclipse Enterprise Edition. [Install if not available]

Step 1: Click On File > Import > Git > Projects From Git > Clone Uri  > Paste: Repository Url> Next > Select Master Branch > Next > Finish

Step 2.A: Right Click on Project > Run as > Maven Build > In the goals field enter "clean install" > apply > run

Step 2.B: Right Click On Project > Build Path > Configure Build Path > Libraries > Remove And Update Any Libraries With Red Mark > Finish

Step 3: [Only if Tomcat v8.0 is not Configured in Eclipse]: Right Click On Project > Run As > Run On Server > Select Tomcat v8.0 > (Select Tomcat V8.0 Installation Location If Asked) Next > Add <project-name> > Finish

Step 4: In The Server Tab > Double Click On Tomcat Server > Ports  > Change The Port Number For Http/1.1 To 8083 > Close And Save

Step 5: Right Click On Project > Run As > Run On Server > Select Tomcat V8.0 > Next > Add All> Done

Step 6: Check Running The Site At  <a Href="Http://localhost:8083/trainbook/">http://localhost:8083/trainbook/</a>

Step 7: Default Username And Password For Admin Is "admin@demo.com" And "admin"

Step 8: Default Username And Password For User Is "sajal@demo.com" And "Sajal"



### The Screenshots of some of the  webPages of this project are Here:

1. Search Trains Between Stations
<img width="100%" alt="Search Trains Between Stations" src="https://user-images.githubusercontent.com/34605595/232220357-54b634d6-afae-427c-b3af-57b372b70906.png">

2. View Trains
<img width="100%" alt="View Available Trains" src="https://user-images.githubusercontent.com/34605595/232219905-983eeefe-977b-40ad-a695-4ec577272dcc.png">

3. Book Trains
<img width="100%" alt="Book Trains Project" src="https://user-images.githubusercontent.com/34605595/232220107-415b251f-90b9-4e70-aff8-e94d370927f6.png">

4. Payment Gateway
<img width="100%" alt="Pay to Book Trains" src="https://user-images.githubusercontent.com/34605595/232220744-351c2c6d-e1f6-49ad-a11b-7680aa63dbe3.png">

5. Booked Ticket Information
<img width="100%" alt="Show Booked Ticket Details" src="https://user-images.githubusercontent.com/34605595/232220935-654bda38-cbde-4203-84b8-3078a32ac6ec.png">

6. Ticket Booking History
<img width="100%" alt="All Ticket Booking History" src="https://user-images.githubusercontent.com/34605595/232220491-3e7996cb-a54c-4375-a35a-6ab1d211a001.png">

7. Fare Enquiry
<img alt="Fare Enquiry between stations" src="https://github.com/shashirajraja/Train-Ticket-Reservation-System/blob/master/Screenshots/fareenquiry.png" width="100%">

8. Change Password
<img alt="Change user Password" src="https://github.com/shashirajraja/Train-Ticket-Reservation-System/blob/master/Screenshots/passwordchange.png" width="100%">

9. Add Trains By Admin
<img alt="Admin Home" src="https://github.com/shashirajraja/Train-Ticket-Reservation-System/blob/master/Screenshots/addtrains.png" width="100%">


#### "Suggestions and project Improvement are Invited"
#### Sajal Garg
##### Project Leader
