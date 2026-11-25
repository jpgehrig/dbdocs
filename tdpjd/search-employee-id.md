###

“Search by Employee Id” is the functionality where we can search for a particular employee based on their employee Id which is the primary key. The user needs to input the employee Id and submit the request.

### Employee Java Bean

Class Name: `src/main/java/com/oracle/jdbc/samples/bean/EmployeeBean.java`

Github Location: EmployeeBean.java

Description: New method getEmployee(int) for searching employee by ID.

Steps to be performed:

Step 1: Declare a method `getEmployee(int)`

Step 1:Instructions for Declaring `getEmployee(int) `method:

1\. The file EmployeeBean is already created on Day 1 for “ListAll” functionality. We can use the same class and add new methods for each one of the functionalities.

2\. On the new line, declare a method getEmployee(int) that takes EmployeeId as a parameter.

`public List<Employee> ``getEmployee(int empId)`;

Implement a new method `getEmployee(int)` in `EmployeeBeanImpl.java`.

Github Location: [EmployeeBeanImpl.java](https://github.com/oracle/oracle-db-examples/blob/master/java/HRWebApp/src/main/java/com/oracle/jdbc/samples/bean/JdbcBeanImpl.java)

Description: Implement a new method getEmployee(int) to search employee by id. This method takes the employee Id as input parameter and returns an object of type Employee.

Steps to be Performed:

Step 2: Implement a new method `getEmployee(int)`:

Step 2: Instructions to create `getEmployee(int)` Method:

1\. Declare the method getEmployee(int) that returns a List of the objects of type Employee.

`public List<Employee> getEmployee(int empId) { `

2\. Declare a variable for the return value of type List\<Employee\>

`List<Employee> returnValue = new ArrayList<>(); `

3\. The first try block is for the getting a database connection by invoking the method getConnection(). Declare a variable connection to establish a database connection.

`try (Connection connection = getConnection()) {`

4\. Start another try block for creating a PreparedStatement. PreparedStatement includes the query that needs to be executed to select an employee based on the employee id.

    try (PreparedStatement preparedStatement = connection.prepareStatement("SELECT Employee_Id, First_Name, Last_Name, Email, Phone_Number, Job_Id, Salary FROM EMPLOYEES WHERE Employee_Id = ?")) {

5\. Set the input parameter which is the employee id for the query.

`preparedStatement.setInt(1, empId);`

6\. Start another try block for ResultSet.

`try (ResultSet resultSet = preparedStatement.executeQuery()) {`

7\. Check if there is anything returned. If yes, then add it to returnValue; otherwise, throw an exception.

    if(resultSet.next()) {
        returnValue.add(new Employee(resultSet));
      } else {
        throw new SQLException("No recrods found");
      }

8\. Make sure to close the parenthesis for all the try blocks. There are a total of 3 try blocks which need to be closed.

9\. Catch the SQLException and log the message in logger as shown below.

    catch (SQLException ex) {
      logger.log(Level.SEVERE, null, ex);
      throw ex;
    }

10\. Return the List of Employees from the method getEmployee(int)

`return returnValue;`

### Add the code to a Servlet to process the request

Class Name: src/main/java/com/oracle/jdbc/samples/web/WebController.java

Github Location: [WebController.java](https://github.com/oracle/oracle-db-examples/blob/master/java/HRWebApp/src/main/java/com/oracle/jdbc/samples/web/WebController.java)

Description: This servlet has already been created in Day 1. We will be adding the relevant code to search by employee id.

Steps to be performed:

Step 3: Add the code to search by employee id to the method `processRequest()`.

Step 3: Instruction for adding code to `processRequest()`:

1\. Declare a varianle ID_KEY to capture the employee id. This is a global variable, hence, needs to be declared outside the method `processRequest()` but within the `WebController` class.

`private static final String ID_KEY = “id”;`

2\. The method processRequest() is already created in the “ListAll” feature. Now, we will add the code to implement “Search by employee id” functionality.

3\. Declare a variable value of the String type to capture the input from the user.

`String value = null;`

4\. In addition to what was added for “ListAll” feature, we will add an if condition to handle the new functionality. Get the employee id entered by the user and invoke the method getEmployee(int) to verify if the employee record exists.

    if ((value = request.getParameter(ID_KEY)) != null) {
          int empId = Integer.valueOf(value).intValue();
          employeeList = employeeBean.getEmployee(empId);
       } else {
          // Previously used getEmployees() method for Listall feature
          employeeList = employeeBean.getEmployees();
       }

### Create a New HTML for Search by Employee Id

Class Name:

`src/main/webapp/listById.html`

Github Location: [listById.html](https://github.com/oracle/oracle-db-examples/blob/master/java/HRWebApp/src/main/webapp/listById.html)

Description: This is the HTML that shows an input box for user to enter the employee id. If the employee record is found, then the details of the employee will be shown on the page, otherwise, an error message will be displayed.

Steps to be performed:

Step 4: Create the title, head, and stylesheet for the HTML page.

Step 5: Create a function to submit the input field i.e, employee id

Step 6: Create a method processResponse() – To process the JSON response and show the results on the HTML page.

1\. Create the title, stylesheet, and body for the HTML page.

    <!DOCTYPE html>
    <html lang="en">
    <head>
    <meta charset="UTF-8">
    <title>List Employee by Id</title>
    <!-- Specify the stylesheet here -->
    <link rel="stylesheet" type="text/css" href="css/app.css" >
    <!-- Bootstrap JS for the UI -->
    <link rel="stylesheet"
    href="http://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css">
    </head>

Step 5: Instructions for handling the input field:

1\. Start the \<body\> tag and a \<input\> tag for capturing the employee id.

    <body>
    <label>Employee Id: </label>
    <input id="empId" type="textfield"
    onkeypress="return waitForEnter(event)"\>

    <br/>
    <br/>
    <script>
    function waitForEnter(e) {
      if (e.keyCode == 13) {
        var tb = document.getElementById("empId");
        fetchElementById(tb.value)
        return false;
      }
    }
    <script>
    var xmlhttp = new XMLHttpRequest();
    var url = "WebController";

3\. Define the action when the requests are sent i.e., when the links for each one of the functionalities is selected.

    xmlhttp.onreadystatechange=function() {
         if (xmlhttp.readyState == 4 && xmlhttp.status == 200) {
           processResponse(xmlhttp.responseText);
         }
       }
    xmlhttp.open("GET", url, true);
    xmlhttp.send();

Step 6: Instructions for Creating `processResponse()` method:

1\. Create the function `processResponse()` to display JSON results on HTML page.

    function processResponse(response) {
    //Process the JSON respnse into an array.
    var arr = JSON.parse(response);
         var i;
    var out = "<table>";
    keys = Object.keys(arr[0]);

    // Print Headers
    out += "<tr>"
    for(i = 0; i < keys.length; ++i) {
    out += "<th>"+keys[i]+"</th>"
    }
    out += "</tr>";
    // Print values
    for(j = 0; j < arr.length; j++) {
    out += "<tr>"
    for(i = 0; i < keys.length; ++i) {
    out += "<td>"+arr[j][keys[i]]+"</td>"

    }
    out += "</tr>"
    }
    out += "</table>";
    document.getElementById("id-emp").innerHTML = out;
    }
