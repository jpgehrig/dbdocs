Class Name: src/main/java/com/oracle/jdbc/samples/entity/Employee.java

Github Location: [Employee.java](https://github.com/oracle/oracle-db-examples/blob/master/java/HRWebApp/src/main/java/com/oracle/jdbc/samples/entity/Employee.java)

Description: This is a class that contains the getter and setter methods for all the attributes of an employee. Example: First_name, Last_Name, Employee_Id etc., will have a getter and setter methods.

Steps to be Performed:

1\. Create a constructor Employee() as shown in the sample.

2\. Create a getter and setter method for all the attributes of an employee to show it on the web application.

Creating Employee.java:

1\. Declare the package for the class Employee.java.

`package com.oracle.jdbc.samples.entity;`

2\. Import the following packages required for the Employee class

    import java.sql.ResultSet;
    import java.sql.SQLException;
    import java.sql.Timestamp;

3\. Declare an Employee class. Add an open parenthesis ({) and closing parenthesis (}). Place the cursor in between the parenthesis:

`public class Employee {`

4\. Declare the following variables for each one of the attributes of an employee.

    private int Employee_Id;
    private String First_Name;
    private String Last_Name;
    private String Email;
    private String Phone_Number;
    private String Job_Id;
    private int Salary;

5\. Create a constructor for Employee that takes ResultSet as the input and throws SQLExceptio. In this constructor, set all the values for the attributes of the Employee.

    public Employee(ResultSet resultSet) throws SQLException {
      this.Employee_Id = resultSet.getInt(1);
      this.First_Name = resultSet.getString(2);
      this.Last_Name = resultSet.getString(3);
      this.Email = resultSet.getString(4);
      this.Phone_Number = resultSet.getString(5);
      this.Job_Id = resultSet.getString(6);
      this.Salary = resultSet.getInt(7);
    }

Instructions for Creating Getter and Setter Methods:

Getter and Setter methods are used to get and set the value of X which is the way to achieve encapsulation. Create the getX and setX methods for all the attributes of the Employee such as employee_id, first_name, last_name, salary, etc.

1\. Create the getter and setter methods for the Employee_Id as shown below

    public int getEmployee_Id() {
       return Employee_Id;
    }
      public void setEmployee_Id(int Employee_Id) {
         this.Employee_Id = Employee_Id;
      }

2\. Create the getter and setter methods for the First_Name of an employee

    public String getFirst_Name() {
      return First_Name;
    }
    public void setFirst_Name(String First_Name) {
      this.First_Name = First_Name;
    }

3\. Create the getter and setter methods for the Last_Name of an employee

    public String getLast_Name() {
      return Last_Name;
    }
    public void setLast_Name(String Last_Name) {
      this.Last_Name = Last_Name;
    }

4\. Create the getter and setter methods for Email of an employee

`public String getEmail() { return Email; ``} public void setEmail(String Email) { this.Email = Email; }`

5\. Create the getter and setter methods for Phone Number of an employee

`public String getPhone_Number() { `

`return Phone_Number; } `

`public void setPhone_Number(String Phone_Number) { `

`this.Phone_Number = Phone_Number; `

}

6\. Create the getter and setter methods for JobId of an employee

`public String getJob_Id() { return Job_Id;}public void setJob_Id(String Job_Id) { this.Job_Id = Job_Id;}`

7\. Create the getter and setter methods for Salary of an employee

    public int getSalary() {
      return Salary;
    }
    public void setSalary(int Salary) {
      this.Salary = Salary;
    }
