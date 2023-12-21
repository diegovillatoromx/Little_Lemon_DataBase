# Little Lemon DataBase
Little Lemon needs to build a robust relational database system in MySQL to store large amounts of data which they can also easily manage and locate as required. 

## Table of Contents 

- [Have you created a GitHub repository to house your code?](#have-you-created-a-github-repository-to-house-your-code)
- [Have you generated an ER diagram of the tables in the Little Lemon database?](#have-you-generated-an-er-diagram-of-the-tables-in-the-little-lemon-database)
- [Have you implemented a procedure called `GetMaxQuantity()` that returns the maximum quantity in an order?](#have-you-implemented-a-procedure-called-getmaxquantity-that-returns-the-maximum-quantity-in-an-order)
- [Have you implemented a procedure called `ManageBooking()` that manages bookings in the Little Lemon database?](#have-you-implemented-a-procedure-called-managebooking-that-manages-bookings-in-the-little-lemon-database)
- [Have you implemented the Python client so that you can communicate with your database using Python?](#have-you-implemented-the-python-client-so-that-you-can-communicate-with-your-database-using-python)
- [Have you implemented a procedure called `UpdateBooking()` that alters an existing booking in the Little Lemon database?](#have-you-implemented-a-procedure-called-updatebooking-that-alters-an-existing-booking-in-the-little-lemon-database)
- [Have you implemented a procedure called `CancelBooking()` that allows you remove bookings from the Little Lemon database?](#have-you-implemented-a-procedure-called-cancelbooking-that-allows-you-remove-bookings-from-the-little-lemon-database)

  
## Have you created a GitHub repository to house your code?

Yes, I have created a repository on GitHub, which serves not only to host the code but also to facilitate collaboration. I am open to contributions and suggestions, and you can find all the necessary information to contribute in the README file. Here is the link to the [repository](https://github.com/diegovillatoromx/Little_Lemon_DataBase/tree/main).

## Have you generated an ER diagram of the tables in the Little Lemon database? 
In this section, I provide an overview of the steps and processes undertaken in developing the relational database system for Little Lemon. My primary objective was to create a comprehensive and efficient database model that would cater to the data management needs of Little Lemon, a dynamic and bustling restaurant environment.

Generating the EER Diagram
To kickstart the process, I utilized MySQL Workbench, a powerful visual tool, for designing and modeling the database. The journey began with the conceptualization of the necessary tables and their relationships, considering both the operational requirements and data integrity of the Little Lemon restaurant.

![EER_diagrama](https://github.com/diegovillatoromx/Little_Lemon_DataBase/blob/main/WEEK1/EER_diagram.png)

Through careful analysis and normalization practices, I identified key entities such as bookings, orders, menu items, customer details, and staff information. The relationships between these entities were meticulously defined to ensure a seamless flow of data and to uphold the principles of relational database design.

Once the entities and relationships were clearly outlined, I employed MySQL Workbench's Model Editor to visually construct the Entity-Relationship (ER) diagram. This diagram serves as a blueprint of the database structure, illustrating how different tables are interlinked through primary and foreign keys, thereby facilitating a clear understanding of the database's layout and functionality.

The generated ER diagram not only visualizes the database structure but also aids in identifying potential areas for optimization and future scalability.

SQL Scripts for Database Implementation
As part of the database implementation, two key SQL scripts were developed:

**`populate_little_lemon_database.sql`**: [This script](https://github.com/diegovillatoromx/Little_Lemon_DataBase/blob/main/WEEK1/populate_little_lemon_database.sql) is pivotal for initializing the database. It encompasses all the necessary SQL commands to populate the tables with data. This step is crucial for setting up a realistic test environment that mirrors the actual operational data of the Little Lemon restaurant. By executing this script, the database tables are filled with data, making the database ready for use and testing.

** `little_lemon.sql`**: Generated directly from MySQL Workbench, [this script](https://github.com/diegovillatoromx/Little_Lemon_DataBase/blob/main/WEEK1/populate_little_lemon_database.sql) encapsulates the entire database schema as defined in the ER diagram. It includes the SQL statements for creating tables, defining relationships, and setting up constraints. This script is instrumental in deploying the database onto a server, ensuring that the database structure aligns precisely with the designed model.

Both scripts are integral to the project, offering a comprehensive setup and deployment mechanism for the Little Lemon database.


## Have you implemented a procedure called `GetMaxQuantity()` that returns the maximum quantity in an order? 

Yes, I have successfully implemented a stored procedure named `GetMaxQuantity()` in the Little Lemon database (`littlelemondb`). This procedure is designed to retrieve the maximum quantity of an item in a single order from the Orders table.

The following SQL script demonstrates the creation and execution of the `GetMaxQuantity()` procedure:

```sql
-- Setting the current database to littlelemondb
USE littlelemondb;

-- Changing the delimiter to create the stored procedure
DELIMITER //

-- Creating the stored procedure
CREATE PROCEDURE GetMaxQuantity()
BEGIN
    SELECT Quantity as `Max Quantity in Order` FROM Orders
    ORDER BY Quantity DESC
    LIMIT 1;
END //
DELIMITER ;

-- Calling the stored procedure to retrieve the maximum quantity
CALL GetMaxQuantity;
```
The `GetMaxQuantity()` procedure operates by selecting the Quantity field from the Orders table. It orders the results in descending order based on the quantity and limits the output to only the top record. This approach ensures that the procedure returns the order with the highest quantity of items.

Executing the `CALL GetMaxQuantity;` statement invokes the stored procedure, which then outputs the maximum quantity found in any order within the database.

Through this implementation, it is possible to quickly identify the largest order by quantity, which can be useful for various analytical and operational purposes within the Little Lemon business context.


## Have you implemented a procedure called `ManageBooking()`  that manages bookings in the Little Lemon database?

Yes, I have developed a stored procedure named `CheckBooking()` for the Little Lemon database (`littlelemondb`). The purpose of this procedure is to check whether a particular table is booked on a given date. This functionality is particularly useful for managing reservations and optimizing table allocations.

Here's the SQL script for the `CheckBooking()` procedure:

```sql
-- Setting the current database to littlelemondb
USE littlelemondb;

-- Dropping the procedure if it exists to avoid any conflicts
DROP PROCEDURE IF EXISTS CheckBooking;

-- Changing the delimiter for the stored procedure creation
DELIMITER //

-- Creating the stored procedure
CREATE PROCEDURE CheckBooking (IN booking_date DATE, IN table_no INT)
BEGIN
    IF EXISTS(SELECT 1 FROM Bookings WHERE BookingDate = booking_date AND TableNumber = table_no)
    THEN
        SELECT CONCAT("Table ", table_no, " is already booked.") AS `Booking status`; 
    ELSE
        SELECT CONCAT("Table ", table_no, " is not yet booked.") AS `Booking status`; 
    END IF;
END //

DELIMITER ;

```

The `CheckBooking()` procedure operates by checking the `Bookings` table for an existing booking that matches the given date and table number. If such a booking exists, it returns a message stating that the table is already booked. Otherwise, it indicates that the table is not yet booked.

This procedure enhances the operational efficiency of booking management by providing a quick and reliable way to check the availability of tables. It's an essential tool for the staff at Little Lemon to manage reservations effectively and provide better service to the customers.


## Have you implemented the Python client so that you can communicate with your database using Python?

Yes, I have successfully implemented a Python client to communicate with the Little Lemon database. Using the `mysql-connector-python` library, I established a connection to the database and performed various operations, including querying data and executing SQL commands.

Here is the code I used for this purpose:

```python
# Necessary module import
!pip install mysql-connector-python
import mysql.connector as connector

# Establishing connection to the database
connection = connector.connect(user="your_user", password="your_password", db="your_database")
cursor = connection.cursor()

# Query to show all tables in the database
show_tables_query = "SHOW tables"
cursor.execute(show_tables_query)
results = cursor.fetchall()

# Printing the tables in the database
for row in results:
    print(row)

# Query to select specific data from customers and orders
query_stmt = """
SELECT Customers.FullName, Customers.ContactNumber, Orders.TotalCost AS `BillAmount`
FROM Customers
JOIN Orders
ON Customers.CustomerID = Orders.CustomerID
WHERE Orders.TotalCost > 60;
"""
cursor.execute(query_stmt)
results = cursor.fetchall()

# Printing the results
print(cursor.column_names)
for row in results:
    print(row)

# Closing the cursor and the connection
cursor.close()
connection.close()

```


## Have you implemented a procedure called `UpdateBooking()`  that alters an existing booking in the Little Lemon database?

Yes, I have implemented a stored procedure named `UpdateBooking()` in the littlelemondb database. This procedure is designed to update the booking date for an existing booking in the Bookings table, identified by its booking ID.

Here's the SQL script for the `UpdateBooking()` procedure:

```sql
-- Setting the current database to littlelemondb
USE littlelemondb;

-- Dropping the procedure if it already exists to avoid conflicts
DROP PROCEDURE IF EXISTS UpdateBooking;

-- Changing the delimiter to create the stored procedure
DELIMITER //

-- Creating the stored procedure
CREATE PROCEDURE UpdateBooking (IN booking_id INT, IN booking_date DATE)
BEGIN
    START TRANSACTION;
    IF NOT EXISTS(SELECT 1 FROM Bookings WHERE (BookingID = booking_id))
    THEN
        SELECT CONCAT("Booking ", booking_id, " does not exist.") AS `Message`;
        ROLLBACK;
    ELSE
        UPDATE Bookings SET BookingDate = booking_date WHERE BookingID = booking_id;
        COMMIT;
        -- SELECT CONCAT("Booking ", booking_id, " updated.") AS `Confirmation`; 
    END IF;
END //

DELIMITER ;
```


## Have you implemented a procedure called `CancelBooking()` that allows you remove bookings from the Little Lemon database?

Yes, I have implemented a stored procedure called `CancelBooking()` in the Little Lemon database (`littlelemondb`). This procedure enables the deletion of a specific booking based on the provided booking ID.

Below is the SQL script for the `CancelBooking()` procedure:

```sql
-- Setting the current database to littlelemondb
USE littlelemondb;

-- Dropping the procedure if it already exists to ensure a clean setup
DROP PROCEDURE IF EXISTS CancelBooking;

-- Changing the delimiter for the stored procedure creation
DELIMITER //

-- Creating the stored procedure
CREATE PROCEDURE CancelBooking (IN booking_id INT)
BEGIN
    START TRANSACTION;
    IF NOT EXISTS(SELECT 1 FROM Bookings WHERE (BookingID = booking_id))
    THEN
        SELECT CONCAT("Booking ", booking_id, " does not exist.") AS `Message`;
        ROLLBACK;
    ELSE
        DELETE FROM Bookings WHERE BookingID = booking_id;
        COMMIT;
        -- SELECT CONCAT("Booking ", booking_id, " cancelled.") AS `Confirmation`; 
    END IF;
END //

DELIMITER ;
```

The `CancelBooking()` procedure initiates by checking if the booking with the specified ID exists in the Bookings table. If the booking is not found, the procedure rolls back any transaction and displays a message stating that the booking ID does not exist. In case the booking is present, it proceeds to delete the booking from the Bookings table and then commits the transaction.

This implementation ensures the safe removal of bookings, as it uses a transaction to prevent unintended deletions. The ROLLBACK command is triggered if no matching booking ID is found, thereby maintaining the integrity of the database. When a valid booking ID is provided, the corresponding booking is securely removed from the database.

The `CancelBooking()` procedure thus offers a reliable method to manage the deletion of bookings in the Little Lemon database, enhancing the functionality and efficiency of the database management.

