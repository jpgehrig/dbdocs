Class Name: src/main/java/com/oracle/jdbc/samples/bean/EmployeeBeanImpl.java

Github Location: EmployeeBeanImpl.java

Description: This is an implementation class. All the methods declared in EmployeeBean.java are implemented in this class. New methods related to each one of the features will be added in the next chapters. To begin with, we will be adding the implementation of the method required for “ListAll” functionality.

Steps to be performed:

Step 4: Create a method getConnection() – to establish a connection to the database. Ensure you update connection URL, DB username and DB password to point to your database.

Step 5: Create a method getEmployees() – To retrieve a list of employees from employees table. Update the SELECT query to be used by choosing the columns that you want from the Employees table.

Step 4: Instructions for creating getConnection() method:

1\. Declare the package for the EmployeeBean.java.

`package com.oracle.jdbc.samples.bean;`

2\. Import Employee class as it contains the employee details.

`Import com.oracle.jdbc.samples.entity.Employee;`

3\. Import other dependent classes as shown below. If the particular class is not imported, JDeveloper will display a message reminding you to import the required package. Press the Alt+Enter keys to import the class:

    import java.sql.*;
    import java.util.ArrayList;
    import java.util.List;
    import java.util.logging.Level;
    import java.util.logging.Logger;

    import java.sql.PreparedStatement;
    import oracle.jdbc.OracleStatement;
    import oracle.jdbc.OracleConnection;
    import oracle.jdbc.driver.OracleDriver;
    import oracle.jdbc.OracleTypes;
    import java.sql.PreparedStatement;
    import oracle.jdbc.OracleStatement;
    import oracle.jdbc.OracleConnection;

    import oracle.ucp.jdbc.PoolDataSourceFactory;
    import oracle.ucp.jdbc.PoolDataSource;

4\. Add the following class declaration EmployeeBeanImpl that implements EmployeeBean. Add an open parenthesis ({) and closing parenthesis (}). Place the cursor in between the parenthesis.

`public class EmployeeBeanImpln implements EmployeeBean {`

5\. Declare a static method getConnection() to establish the connection. Add an open parenthesis ({) and closing parenthesis (}). Place the cursor in between the parenthesis.

`public static Connection getConnection() throws SQLException {`

6\. Register a driver as shown below.

`DriverManager.registerDriver(new oracle.jdbc.OracleDriver());`

7\. Get a connection by passing the database URL and database username and password.

`Connection connection = DriverManager.getConnection("jdbc:oracle:thin:@//myorclhost:5521/myorcldbservice", "hr", "hr");`

8\. Return the database connection.

`return connection;`

Instructions to Create getEmployees() method:

1\. Declare the method getEmployees(). Add an open parenthesis ({) and closing parenthesis (}). Place the cursor in between the parenthesis.

`Public List<Employee> getEmployees()throws SQLException {`

2\. Declare a variable for the return value of type List\<Employee\>

`List<Employee> returnValue = new ArrayList<>();`

3\. Start a try block. The source code is compiled with JDK8 and we use auto-closeable statements which means that there is no need to explicitly specify `catch` and `finally` blocks. The first try block is for getting a database connection by invoking the method `getConnection()`. Declare a variable connection to establish a database connection.

`try (Connection connection = getConnection()) {`

4\. Start another try block for creating a `Statement`.

`try (Statement statement = connection.createStatement()) {`

5\. Start another try block for ResultSet. Include the query that needs to be executed. Make sure to retrieve all the required fields of the employee in the query.

`try (ResultSet resultSet = statement.executeQuery("SELECT Employee_Id, First_Name, Last_Name, Email, Phone_Number, Job_Id, Salary FROM EMPLOYEES")) {`

6\. Start a while loop to capture the list of employees retrieved from the ResultSet.

    while(resultSet.next()) {
      returnValue.add(new Employee(resultSet));
    }

7\. Ensure you close the parenthesis for all the try blocks.

8\. Catch the SQLException and log the message in logger as shown below.

    catch (SQLException ex) {
      logger.log(Level.SEVERE, null, ex);
      ex.printStackTrace();
    }

9\. Return the List of employees from the method `getEmployees()`

`return returnValue;`
