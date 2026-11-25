The following code describes the steps required to create a Servlet to process a request.

Class Name: src/main/java/com/oracle/jdbc/samples/web/WebController.java

Github Location: [WebController.java](https://github.com/oracle/oracle-db-examples/blob/master/java/HRWebApp/src/main/java/com/oracle/jdbc/samples/web/WebController.java)

Description: This is the main servlet that controls all the flows of the application. For every new functionality of the application, we will be adding the code to handle the new requests and responses in `doPost()` and `processResponse() `respectively.

Steps to be Performed:

6\. Create a servlet WebController.java and reportError() method

7\. Create a method processRequest() – This method processes both GET and POST HTTP requests.

8\. Create a method doGet() – Add details toget the employee details from the database and show the results in JSON. JSON will be the output format of the results that is shown on the HTML.

9\. Create a method getServletInfo() – To display some generic information about the servlet.

10\. Create a logger to log exceptions and other error messages.

Step 6: Instructions for creating a WebController.java and reportError() method

1\. Declare the package for the WebController.java.

`package com.oracle.jdbc.samples.web;`

2\. Import `Employee` class as it contains the employee details and also, the `EmployeeBeanImpl. `

    import com.oracle.jdbc.samples.entity.Employee;
       import com.oracle.jdbc.samples.bean.EmployeeBean;
       import com.oracle.jdbc.samples.bean.EmployeeBeanImpl;

3\. Import the GSON (Google GSON) for displaying the Employee results.

`import com.google.gson.Gson; import com.google.gson.reflect.TypeToken;`

4\. Import other dependent classes as shown below. If the particular class is not imported, then JDeveloper will display a message reminding you to import the required package. Press the Alt+Enter keys to import it.

    import javax.servlet.ServletException;
        import javax.servlet.annotation.WebServlet;
        import javax.servlet.http.*;
        import java.io.IOException;
        import java.io.PrintWriter;
        import java.io.BufferedReader;
        import java.util.ArrayList;
        import java.util.List;
        import java.util.Map;

        import java.util.logging.Logger;

5\. Add the annotation to the servlet.

`@WebServlet(name = "WebController", urlPatterns = {"/WebController"})`

6\. Add the following class declaration WebController that extends HttpServlet. Add an open parenthesis ({) and closing parenthesis (}). Place the cursor in between the parenthesis.

    public class WebController extends HttpServlet {

7\. Declare an object “employeeBean” of the type `EmployeeBeanImpl`. This will be a global variable and available for all the methods such as `reportError()`, `processRequest()`, and `doGet()` to use.

8\. Declare an object “gson” of the type Gson. This will be a global variable and available for all the methods such as `reportError()`, `processRequest()`, and `doGet()` to use.

`Gson gson = new Gson();`

9\. Declare a method reportError as shown below. This is to capture the error and show it on the page.

`private void reportError(HttpServletResponse response, String message) throws ServletException, IOException {`

10\. Set the response content type to be “text/html” and charset=UTF-8 as shown below.

`response.setContentType("text/html;charset=UTF-8");`

11\. Create a PrintWriter object and print the error message as shown.

try (PrintWriter out = response.getWriter()) {

    try (PrintWriter out = response.getWriter()) {
    out.println("<!DOCTYPE html>");
    out.println("<html>");
    out.println("<head>");
    out.println("<title>Servlet WebController</title>");
    out.println("</head>");
    out.println("<body>");
    out.println("<h1>" + message + "</h1>");
    out.println("</body>");
    out.println("</html>");
    }

Step 7: Instructions for Creating Process Request:

1\. Add the following method declaration for processRequest(req, res). Add open and close parentheses ({, }) and position the cursor in between the parenthesis.

`protected void processRequest(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {`

2\. Declare a variable employeeList of the List type that contains Employee objects.Declare the variable gson to process Gson object.

`List<Employee> employeeList = null;`

3\. Instantiate the employeeList object by invoking getEmployees method of EmployeeBean.

`employeeList = employeeBean.getEmployees();`

4\. Check if the employeeList is not NULL

`if (employeeList != null) { `

5\. Set the content type to “application/json”

`response.setContentType("application/json");`

6\. Invoke the method toJson(…) and convert the employeeList to JSON.

    gson.toJson(employeeList,
                new TypeToken<ArrayList<Employee>>() {}.getType(),
    response.getWriter());

7\. End of if condition. Close the parenthesis (})

8\. Add an else condition to cover the error scenario when the employeeList is empty.

    else {
      response.setStatus(HttpServletResponse.SC_NOT_FOUND);
    }

Step 8: Instructions for Creating `doGet()`:

1\. Add the following method declaration for doGet().Add open and close parentheses ({, }) and position the cursor in between the parenthesis.

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {

2\. Invoke the method `processRequest(request, response) `by passing the `HTTPServletRequest `and `HTTPServletResponse `response objects.

`processRequest(request, response);`

Step 9: Instructions for Creating `getServletInfo()`:

1\. Add the following method declaration for getServletInfo().Add open and close parentheses ({, }) and position the cursor in between the parenthesis.

`public String getServletInfo() {`

2\. In the return statement, set a message about the servlet.

`return "JdbcWebServlet: Reading Employees table using JDBC and transforming it as a JSON. ";`

Step 10: Instructions for Creating Logger ():

1\. Create a variable logger of the type Logger at the end of the class, before closing the parenthesis for the class WebController.java.

    private static final Logger logger =
    Logger.getLogger(WebController.class.getName());
