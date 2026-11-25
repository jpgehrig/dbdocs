The hradmin has the privilege to update an employee record. The hrstaff user does not have this privilege.

First, you must search for an employee in the records. Once you retrieve the information related to the employee, you will find the ‘Edit’ and ‘Delete’options to modify details related to the employee.

This Chapter shows you the classes that need to be created and code that needs to be added to build ‘Search by Employee ID’ functionality.

In this Chapter, you will learn how to:

1\. Declare a new new method getEmployeeByFn(String) in EmployeeBean.java

2\. Declare a new method updateEmployee(int) in EmployeeBean.java

3\. Implement a new method getEmployeeByFn(String) in EmployeeBeanImpl.java

4\. Implement a new method updateEmployee(int) in EmployeeBeanImpl.java

5\. Add the code to a WebController.java to process the request and response

6\. Create a HTML page (listByName.html) to display the results

Class Name:

`src/main/java/com/oracle/jdbc/samples/entity/Employee.java`

Use the `Employee.java` file that you created, earlier in the example.

### Declare a new method getEmployeeByFn(String) in EmployeeBean.java

Class Name: src/main/java/com/oracle/jdbc/samples/bean/EmployeeBean.java

Github Location: [EmployeeBean.java](https://github.com/oracle/oracle-db-examples/blob/master/java/HRWebApp/src/main/java/com/oracle/jdbc/samples/bean/JdbcBean.java)

Description: The method `getEmployeeByFn``(String)` helps you search employees based on their first name.

To modify details of the employee, the hradmin must first search for the employee based on his/her first name.

Steps to be performed:

Step 1: Declare a method `getEmployeeByFn(String)`

Step 1: Instructions for declaring getEmployeeByFn(String) method:

1\. Use the class EmployeeBean that you created on Day 1 of the exercise. You can add new methods for each of the functionalities.

2\. Declare a method `getEmployeeByFn(String)` that takes first name as a parameter.

`public List<Employee> getEmployeeByFn(String fn)throws SQLException;`

### Declare a new method updateEmployee(Employee)

Class Name: `src/main/java/com/oracle/jdbc/samples/bean/EmployeeBean.java`.

Github Location: [EmployeeBean.java](https://github.com/oracle/oracle-db-examples/blob/master/java/HRWebApp/src/main/java/com/oracle/jdbc/samples/bean/JdbcBean.java)

Description: This method allows you to update attributes of an employee such as first name, last name, salary, job_id etc

Steps to be Performed:

Step 2: Declare a method updateEmployee(Employee)

Instructions for declaring `updateEmployee(Employee)` method

1\. Use the `EmployeeBean` file that you created in the exercise from Day 1 for ‘`ListAll`’ functionality. You can use the same class and add new methods for the new functionalities.

2\. Declare a method `updateEmployee(Employee)` that takes Employee object as a parameter.

`public String updateEmployee(Employee employee) throws SQLException;`

### Implement a New Method `getEmployeebyFn()` for Search by Employee name

Class Name:

`src/main/java/com/oracle/jdbc/samples/bean/JdbcBeanImpl.java`

Github Location: [EmployeeBeanImpl.java](https://github.com/oracle/oracle-db-examples/blob/master/java/HRWebApp/src/main/java/com/oracle/jdbc/samples/bean/JdbcBeanImpl.java)

Description: Implement a new method `getEmployeeByFn(String)` to search by employee id. This method uses the employee id as an input parameter and returns an object of type Employee.

Steps to be Performed: Implement a method `getEmployeeByFn(String)`

Instructions for implementing `getEmployeeByFn(String)` method:

1\. Declare `getEmployeeByFn(String)` that returns a an Employee object.

`public List<Employee> getEmployeeByFn(String fn) throws SQLException {`

2\. Declare a variable for the return value of type `List<Employee>`

`List<Employee> returnValue = new ArrayList<>();`

3\. Create a `try` block. The `try` block will help you create a database connection by invoking the `getConnection` method.

`try (Connection connection = getConnection()) {`

4\. Create another `try` block to create a `PreparedStatement`. Add the query that will be executed to select an employee based on the employee id.

    try (PreparedStatement preparedStatement = connection.prepareStatement("SELECT Employee_Id, First_Name, Last_Name, Email, Phone_Number, Job_Id, Salary FROM EMPLOYEES WHERE First_Name LIKE ?")) {

5\. Set an input parameter — first name of the employee. The input parameter of the method is set as the IN parameter for the` preparedStatement`.

`preparedStatement.setString(1, fn + '%');`

6\. Create another `try` block for `ResultSet`. Include the query that needs to be executed.

`try (ResultSet resultSet = preparedStatement.executeQuery()) {`

7\. Include while statement to loop through the results. If any record is found, add it to the `returnValue`.

    while(resultSet.next()) {
        returnValue.add(new Employee(resultSet));
      }

8\. Ensure you close parenthesis for all `try` blocks.

9\. Catch the `SQLException` and log the message in the logger.

    catch (SQLException ex) {
      logger.log(Level.SEVERE, null, ex);
      throw ex;
    }

10\. Return the List of employees from the method` getEmployee(int) `

`return returnValue; `

### Implement a new method updateEmployee(Employee)

Class Name: src/main/java/com/oracle/jdbc/samples/bean/EmployeeBeanImpl.java.

Github Location: [EmployeeBeanImpl.java](https://github.com/oracle/oracle-db-examples/blob/master/java/HRWebApp/src/main/java/com/oracle/jdbc/samples/bean/JdbcBeanImpl.java)

Description: The method `updateEmployee(Employee)` enables you to update the employee details such as first_name, last_name etc, in the employee record.

Steps to be performed: Implement a method `updateEmployee(Employee)`

Instructions for Implementing `UpdateEmployee(Employee) `method:

1\. Declare method `updateEmployee(Employee)`.

`public String updateEmployee(Employee employee) throws SQLException {`

2\. Declare and initialize a variable for capturing the number of records updated.

`int updateCount = 0;`

3\. Create a `try` block to establish a database connection by invoking the method `getConnection()`.

`try (Connection connection = getConnection()) {`

4\. Create another try block to make a `PreparedStatement`. Include the query you will need to execute to select an employee based on the employee id.

    try (PreparedStatement preparedStatement = connection.prepareStatement("UPDATE employees SET FIRST_NAME = ?, LAST_NAME = ?, EMAIL = ?, PHONE_NUMBER = ?, SALARY = ? WHERE EMPLOYEE_ID = ?")) {

5\. Set the new values entered by the user for each attribute and execute the prepapredStatement.

    preparedStatement.setString(1, employee.getFirst_Name());
    preparedStatement.setString(2, employee.getLast_Name());
    preparedStatement.setString(3, employee.getEmail());
    preparedStatement.setString(4, employee.getPhone_Number());
    preparedStatement.setInt(5, employee.getSalary());
       preparedStatement.setInt(6, employee.getEmployee_Id());
    updateCount = preparedStatement.executeUpdate();

6\. Close parenthesis for all `try` blocks.

7\. Catch the SQLException and log the message in the logger as shown below:

    catch (SQLException ex) {
      logger.log(Level.SEVERE, "Unable to update record", ex);
      throw new SQLException("Alert! Record could not be updated, "
        +ex.getMessage(), ex);}

8\. Log the message with the number of records updated to the logger.

`logger.fine("Update count: " +updateCount);`

9\. If none of the records were updated, enter a message as follows:

    if (updateCount != 1) {
      logger.severe("Unable to update record");
      throw new SQLException("Alert! Record could not be updated");
    }

10\. Return the success message if the record was updated.

    return "Success: Record updated";

### Add the Code to a Servlet (WebController.java)

This is the start of your topic.

Class Name: src/main/java/com/oracle/jdbc/samples/web/WebController.java

Github Location: [WebController.java](https://github.com/oracle/oracle-db-examples/blob/master/java/HRWebApp/src/main/java/com/oracle/jdbc/samples/web/WebController.java)

Description: You have created the servlet in the Day 1 exercise. In this section, you will add the relevant code to give a salary raise to all employees.

Step 6: Add code to calculate salary budget, after the user enters the input percentage. This is handled in the `doPost()` method.

Instructions to add code to doPost(req, res):

1\. You have already created this method in the ‘Update an Employee’ record section.

2\. Create another `if` block to check the functionality to be invoked based on the input.

    if ("incrementSalary".equals(value)) {
      if ((value = request.getParameter(INCREMENT_PCT)) != null)   {
           try {
       System.out.println("increment% = " +value);
       response.setContentType("application/json");
    List<Employee> employeeList =   employeeBean.incrementSalary(Integer.valueOf(value));
       System.out.println("incrementSalary, employeeList: " +employeeList.toString());
       gson.toJson(employeeList,
    new TypeToken<ArrayList<Employee>>(){}.getType(),
    response.getWriter());
      }catch (Exception ea) {         response.setStatus(HttpServletResponse.SC_NOT_MODIFIED);
       }
    } else {
    response.setStatus(HttpServletResponse.SC_NOT_MODIFIED);
          }
    }

3\. Ensure all the parenthesis are closed properly.

### Create a new HTML(incrementSalary.html)

Class Name: `src/main/webapp/incrementSalary.html.`

Github Location: [incrementSalary.html](https://github.com/oracle/oracle-db-examples/blob/master/java/HRWebApp/src/main/webapp/incrementSalary.html)

Description: This HTML displays an input box to enter the percentage for calculating the salary budget.

Step 7: Create the title, head, and stylesheet for the HTML page

Step 8: Create a function to submit the input field i.e, employee first name

Step 9: Create a method processResponse() – To process the JSON response and show the results on the HTML page

Step 7: Instructions to create the title, stylesheet, and body of the HTML page:

1\. Create the title, stylesheet, and body of the HTML page.

    <!DOCTYPE html>
    <html lang="en">
    <head>
    <meta charset="UTF-8">
    <title>Increment Salary</title>
    <link rel="stylesheet" type="text/css" href="css/app.css" >
    <link rel="stylesheet" href="http://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css">
    <script    src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.2/jquery.min.js">script    src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.2/jquery.min.js"></script>
    </head>

Step 8: Instructions for Handling the Input Field

1\. Start the \<body\> tag and a \<input\> tag for capturing the percentage for salary raise.

    <body>
     Enter the percentage increase in salary<inputid='incrementField' type="number" max="100" min="3">%

     <button type="button" class="btn btn-info btn-lg" onclick='javascipt:confirmUpdate()'> Increment Salaries</button> <button type="button" class="btn btn-default btn-lg" onclick='javascipt:cancelUpdate()'>Cancel</button>


    <script>
    function showStatus(c, message) {
         $('#status').text(message);
         $('#status').attr('class', c);
           }

    function confirmUpdate() {
      var increment = $('#incrementField').val();
      var res = confirm("Do you really want to Increment Salary by " +increment +"%?");
      if(res == true) {
        console.log("Salary record");
        $('#UpdateButton').hide();
        showStatus("alert alert-info", "Updating records, processing request");
        var xmlhttp = new XMLHttpRequest();
        var url = "WebController?op=incrementSalary&incrementPct=" +increment;
        xmlhttp.onreadystatechange = function() {
          if (xmlhttp.readyState == 4 && xmlhttp.status == 200) {
            processResponse(xmlhttp.responseText);
            showStatus("alert alert-success", "Updating records, successfully updated");
          }
          else {
            showStatus("alert alert-danger", "Updating records, failure, could not update records");
          }
        }
        xmlhttp.open("POST", url, true);
        xmlhttp.send();
        showStatus("alert alert-info", "Updating records, request sent");

      }
      else {
        console.log("Salary not updated");
        showStatus("alert alert-warning", "Updating records, attempt cancelled");

      }
    }

    </script>

Step 9: Instructions to Create `processResponse()` method:

1\. Create the function `processRequest()` to display the JSON results on HTML page.

    unction processResponse(response) {
      var arr = JSON.parse(response);
      var i;
      var out = "<table>";
    keys = Object.keys(arr[0]);

      // Print headers
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

### Creating Login Users in Tomcat

The HR Web Application will have two users — `hradmin` and `hrstaff`.

After you login on the home scree using your credentials, you will be able to see the landing page, with details of the web application. The hradmin and hrstaff have different privileges and access to different features.

This Chapter will show you the required classes that you need to create and how to build the ‘Login’ functionality in Tomcat.

- Create a XML file (tomcat-users.xml) for login functionality

- Create a HTML page (login.html) to login the user

- Create a HTML page (login-failed.html) to display the error message

- Create a web.xml to authenticate the users during login

- Create a HTML page (about.html) to show more details about the application

- Create a landing page (index.html) and define the html pages for redirection

- Add code to the servlet (WebController.java) to process logout

#### Create an XML file (tomcat-users.xml) for login functionality

Class Name: `/java/HRWebApp/tomcat-users.java`

Github Location: [tomcat-users.xml](https://github.com/oracle/oracle-db-examples/blob/master/java/HRWebApp/tomcat-users.xml)

Description: Create an XML file tomcat-users.xml and list down the login users you want to allow access to. Specify both username and password for each one of the users.

Step 1: Create a new file tomcat-user.xml

Instructions for creating tomcat-users.xml:

1\. Create the file `tomcat-users.xml`. Place this file under `TOMCAT_HOME/conf /tomcat-users.xml`

    <?xml version='1.0' encoding='utf-8'?> z
    <tomcat-users xmlns="http://tomcat.apache.org/xml"
             xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://tomcat.apache.org/xml tomcat-users.xsd" version="1.0">
    <role rolename="manager"/>
    <role rolename="staff"/>
    <user username="hradmin" password="welcome" roles="manager,staff"/>
    <user username="hrstaff" password="welcome" roles="staff"/>
    </tomcat-users>

#### Create a new HTML (login.html)

Class Name: src/main/webapp/login.html

Github Location: [login.html](https://github.com/oracle/oracle-db-examples/blob/master/java/HRWebApp/src/main/webapp/login.html)

Description: The login page is displayed when you invoke the main page of the web application. The login page shows up fields to capture username and password.

Step 2: Create the title, head, and stylesheet for login.html

Step 3: Create the \<body\> to capture input fields and submit the form

Step 2: Instructions to create title, head and stylesheet for `login.html:`

1\. Create the file `tomcat-users.xml`. Place this file `TOMCAT_HOME/conf/tomcat-users.xml`.

    <!DOCTYPE html>
    <html lang="en">
    <head>
    <meta charset="UTF-8">
    <title>Login to Jdbc Web Sample application</title>
    <link rel="stylesheet" href="http://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css">
    <style>
    #cent {
        position:absolute;
        top:50%;
        left:50%;
        margin-top:-50px; /* this is half the height of your div*/
        margin-left:-100px; /*this is half of width of your div*/
      }
       td {
         height: 30px;
       }

    </style>
    </head>

Step 3: Instructions to Create the \<body\> and submit the form:

1\. Create the \<body\> and \<form\> to submit the login credentials entered by the user.

    <body>

    <form method="POST" action="j_security_check">
    <table>
    <tr>
    <td colspan="2">Login to the Jdbc Web Sample application:</td>
    </tr>
    <td>Name:</td>
    <td><input type="text" name="j_username" /></td>
    </tr>
    <tr>
    <td>Password:</td>
    <td><input type="password" name="j_password"/></td>
    </tr>
    <tr>
    <td colspan="2"><input type="submit" value="Go" /></td>
    </tr>
    </table>
    </form>

    </body>

#### Create a new HTML (login-failed.html)

Class Name: src/main/webapp/login-failed.html

Github Location: [login-failed.html](https://github.com/oracle/oracle-db-examples/blob/master/java/HRWebApp/src/main/webapp/login-failed.html)

Description: This the html page that will be displayed if the login is unsuccessful.

Step 4: Create the new page login-failed.html to show a message during unsuccessful login attempts

Instructions to Create a new HTML page `login-failed.html`.

1\. Create the `login-failed.html` as shown below.

    <!DOCTYPE html>
    <html lang="en">
    <head>
    <meta charset="UTF-8">
    <title>Login Failed</title>
    </head>
    <body>
    <p>
    Sorry, login failed!
    </p>
    </body>
    </html>

#### Create a web.xml to authenticate the users during login

Class Name: `src/main/webapp/WEB-INF/web.xml`

Github Location: [web.xml](https://github.com/oracle/oracle-db-examples/blob/master/java/HRWebApp/src/main/webapp/WEB-INF/web.xml)

Description: The web.xml file consists of descriptors to authenticate the users when the login page is shows to the user.

Steps: Create the file web.xml as shown below.

Instructions for creating `web.xml`

1\. Use the following steps to create the web.xml file:

    <!DOCTYPE web-app PUBLIC
     "-//Sun Microsystems, Inc.//DTD Web Application 2.3//EN"
     "http://java.sun.com/dtd/web-app_2_3.dtd">
    <web-app>
    <display-name>Jdbc Web Sample</display-name>
    <security-role>
    <role-name>manager</role-name>
    </security-role>
    <security-role>
    <role-name>staff</role-name>
    </security-role>
    <security-constraint>
    <web-resource-collection>
    <web-resource-name>Wildcard means whole app requires
    authentication</web-resource-name>
    <url-pattern>/*</url-pattern>
    <http-method>GET</http-method>
    <http-method>POST</http-method>
    </web-resource-collection>
    <auth-constraint>
    <role-name>manager</role-name>
    </auth-constraint>
    <user-data-constraint>
    <transport-guarantee>NONE</transport-guarantee>
    </user-data-constraint>
    </security-constraint>
    <security-constraint>
    <web-resource-collection>
    <web-resource-name>Wildcard means whole app requires
    authentication</web-resource-name>
    <url-pattern>/*</url-pattern>
    <http-method>GET</http-method>
    </web-resource-collection>
    <auth-constraint>
    <role-name>staff</role-name>
    </auth-constraint>
    <user-data-constraint>
    <transport-guarantee>NONE</transport-guarantee>
    </user-data-constraint>
      </security-constraint>
    <login-config>
    <auth-method>FORM</auth-method>
    <form-login-config>
    <form-login-page>/login.html</form-login-page>
    <form-error-page>/login-failed.html</form-error-page>
    </form-login-config>
    </login-config>
    </web-app>

#### Create a HTML page (about.html) to describe the web application

Class Name: `src/main/webapp/about.html`

Github Location: [about.html](https://github.com/oracle/oracle-db-examples/blob/master/java/HRWebApp/src/main/webapp/about.html)

Description: The `about.html` file displays information about the HR Application, users and functionalities.

Step 6: Download the [about.html](https://github.com/oracle/oracle-db-examples/blob/master/java/HRWebApp/src/main/webapp/about.html) and use it in your application.

#### Create a landing page (index.html) and define the pages for redirection

Class Name: `src/main/webapp/index.html`

Github Location: [index.html](https://github.com/oracle/oracle-db-examples/blob/master/java/HRWebApp/src/main/webapp/index.html)

Description: The index.html file consists of all details about the HR Web Application. It describes in detail its users and functionalities.

Step 7: Create the title, head, and stylesheet for index.html

Step 8: Create the `<body> `to invoke the html pages for redirecting the requests

7\. Instructions to Create title, head and stylesheet for index.html:

1\. Create the index.html file.

    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="utf-8">
    <title>Employee table listing</title>
    <link rel="stylesheet" type="text/css" href="css/app.css" >
    <style>
    iframe:focus {
    outline: none;
    }
    iframe[seamless] {
    display: block;
    }
    </style>
    </head>
    <body>

Step 8: Instructions to Create \<body\>, redirection, and actions for buttons:

1\. Create `<body>` and actions for the features through navigation links and logout.

    <body>


    ×
    List All
    Search By Id

    Update Employee Record
    Increment Salary
    About



    myrole
    Logout


     Java 2 Days HR Web Application


    <iframe id="content"
    src="about.html"
    frameborder="0"
    style="overflow:hidden; height:100%; width:100%"
    height="100%"
    width="100%"></iframe>


    <script>
    function openNav() {
      document.getElementById("sideNav").style.width = "256px";
      document.getElementById("main").style.marginLeft = "256px";
    }

    function closeNav() {
      document.getElementById("sideNav").style.width = "0";
      document.getElementById("main").style.marginLeft= "0";
    }

    function switchSrc(src) {
      document.getElementById('content').src = src;
    }

    function logout() {

      var xmllogout = new XMLHttpRequest();
      xmllogout.open("GET", "WebController?logout=true", true, "_", "_");
      xmllogout.withCredentials = true;
      // Invlalid credentials to fake logout
      xmllogout.setRequestHeader("Authorization", "Basic 00001");
      xmllogout.send();

      xmllogout.onreadystatechange = function() {
        window.location.replace("index.html");
      }

     return true;
    }

    var xmlhttp = new XMLHttpRequest();
    var url = "getrole";

    xmlhttp.onreadystatechange = function() {
      if (xmlhttp.readyState == 4 && xmlhttp.status == 200) {
        role = xmlhttp.responseText;
        console.log("role: " +role);
        if (role == "staff") {
          console.log ("disabling manager");
          var x = document.getElementsByClassName('manager');
          for(i = 0; i < x.length; ++i) {
            x[i].style.display = 'none';
          }
        }
        document.getElementById('myrole').innerHTML = ' '+role+' ';
      }
    }
    xmlhttp.open("GET", url, true);
    xmlhttp.send();
    </script>
    </body>

#### Add code to the servlet (WebController.java) to process logout

Class Name: `src/main/java/com/oracle/jdbc/samples/web/WebController.java`

Github Location: [WebController.java](https://github.com/oracle/oracle-db-examples/blob/master/java/HRWebApp/src/main/java/com/oracle/jdbc/samples/web/WebController.java)

Description: You have created this servlet in the Day 1 exercise. In this step, you will add relevant code to implement logout and login.

Step 9: Update the method `processRequest(req, res)`for log out functionality

Instructions to Update the Method `processRequest (req, res):`

1\. You have created a method in the “ListAll” feature in the earlier steps. In this step, you will add code for the `logout` functionality.

2\. Create an `if` block to verify the functionality you will invoke based on input. Check if the input valuie is ‘`LOGOUT`’. Then, invoke the relevant method to log out the user.

    if ((value = request.getParameter(LOGOUT)) != null) {
    /* Getting session and then invalidating it */

     HttpSession session = request.getSession(false);
    if (request.isRequestedSessionIdValid() && session != null)   {
      session.invalidate();
    }
    handleLogOutResponse(request,response);
       response.setStatus(HttpServletResponse.SC_UNAUTHORIZED);
    return;
    }

    private void handleLogOutResponse(HttpServletRequest request,
    HttpServletResponse response) {
        Cookie[] cookies = request.getCookies();
        for (Cookie cookie : cookies) {
          cookie.setMaxAge(0);
          cookie.setValue(null);
          cookie.setPath("/");
          response.addCookie(cookie);

        }
      }

3\. Verify that all parenthesis are closed properly.
