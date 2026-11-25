The HR Web Application is intended to give you access to information related to all employees of AnyCo Corporation.

The two types of users that will be able to access this application are:

- HRStaff

- HRAdmin

The HRStaff and HRAdmin accounts have different privileges.

HRStaff has read only access to the application and does not have privileges to update/delete an employee record. HRStaff can only List the employees and Search by Employee ID.

The HRAdmin, has complete control on the application and has read and write privileges. HRAdmin is the only user who has access to all functionalities of the application such as update/delete an employee record, or provide salary increment for all employees.

This Chapter has the following sections:

- Functionalities of he HR Web Application

- [Packages](aims-and-objectives-this-book.md)

### Functionalities of the HR Web Application

Following is a list of functionalities to access information related to AnyCo Corporation:

Through the hrstaff, you can perform the following functions:

- List All Employees

  Use the `List All Employees` option to retrieve employee information. This function lists information such as `Employee_ID`, `First_Name`, `Last_Name`, `Email`, `Phone_Number`, `Job_Id`, and `Salary`.

- Search By Employee ID

  Use the`primary key` (which is the Employee ID) to search for a particular employee.

  Through the hradmin user, you can perform the following functions:

  The hradmin user has full control of the application and has both read and update privileges.

- Update Employee Record

  You can update employee records, using the `Update Employee Record` function. First, search for employees, based on the name of the employee. You can then update employee details in the record, such as `first_name`, `last_name`, `email`, `phone_number`, `job_id` and `salary` using the `UPDATE` function.

  Use the `DELETE` function to the delete the entire employee record from the database.

- Increment Salary

  Through the increment salary tab, you can alter (increase or decrease) the percentage of salary for hike.

- About

  This page provides an overview of the HR Application and explains the various functionalities it offers.
