The type of the Java application determines how the client calls a Java method. The following sections discuss each of the Java application programming interfaces (APIs) available for calling a Java method:

- Using PL/SQL Wrappers

- About JNI Support

- About Utilizing SQLJ and JDBC with Java in the Database

- About Using the Command-Line Interface

- Overview of Using the Client-Side Stub

### 3.1.1 Using PL/SQL Wrappers

You can run Java stored procedures in the same way as PL/SQL stored procedures. In Oracle Database, Java is usually invoked through PL/SQL interface.

To call a Java stored procedure, you must publish it through a call specification. The following example shows how to create, resolve, load, and publish a simple Java stored procedure that returns a string:

1.  Define a class, `Hello`, as follows:
        public class Hello
        {
          public static String world()
          {
            return "Hello world";
          }
        }

    Save the file as a `Hello.java` file.
2.  Compile the class on your client system using the standard Java compiler, as follows:
        javac Hello.java

    It is a good idea to specify the `CLASSPATH` on the command line with the `javac` command, especially when writing shell scripts or make files. The Java compiler produces a Java binary file, in this case, `Hello.class`.

    You must determine the location at which this Java code will run. If you run `Hello.class` on your client system, then it searches the `CLASSPATH` for all the supporting core classes that `Hello.class` needs for running. This search should result in locating the dependent classes in one of the following:

    - As individual files in one or more directories, where the directories are specified in the `CLASSPATH`

    - Within `.jar` or `.zip` files, where the directories containing these files are specified in the `CLASSPATH`
3.  Decide on the resolver for the `Hello` class.
    In this case, load `Hello.class` on the server, where it is stored in the database as a Java schema object. When you call the `world()` method, Oracle JVM locates the necessary supporting classes, such as `String`, using a resolver. In this case, Oracle JVM uses the default resolver. The default resolver looks for these classes, first in the current schema, and then in `PUBLIC`. All core class libraries, including the `java.lang` package, are found in `PUBLIC`. You may need to specify different resolvers. You can trace problems earlier, rather than at run time, by forcing resolution to occur when you use the `loadjava` tool.
4.  Load the class on the server using the `loadjava` tool. You must specify the user name and password. Run the `loadjava` tool as follows:
        loadjava -user HR Hello.class
        Password: password
5.  Publish the stored procedure through a call specification.
    To call a Java `static` method with a SQL call, you must publish the method with a call specification. A call specification defines the arguments that the method takes and the SQL types that it returns.

    In SQL\*Plus, connect to the database and define a top-level call specification for `Hello.world()` as follows:

        sqlplus HR
        Enter password: password
        connected
        SQL> CREATE OR REPLACE FUNCTION helloworld RETURN VARCHAR2 AS
          2  LANGUAGE JAVA NAME 'Hello.world () return java.lang.String';
          3  /
        Function created.
6.  Call the stored procedure, as follows:
        SQL> VARIABLE myString VARCHAR2(20);
        SQL> CALL helloworld() INTO :myString;
        Call completed.
        SQL> PRINT myString;

        MYSTRING
        ---------------------------------------
        Hello world

        SQL>

    The `call helloworld() into :myString` statement performs a top-level call in Oracle Database. SQL and PL/SQL see no difference between a stored procedure that is written in Java, PL/SQL, or any other language. The call specification provides a means to tie inter-language calls together in a consistent manner. Call specifications are necessary only for entry points that are called with triggers or SQL and PL/SQL calls. Furthermore, JDeveloper can automate the task of writing call specifications.

**Related Topics**

- [Overview of Resolving Class Dependencies](preparing-Java-class-methods.md)
- [Schema Objects and Oracle JVM Utilities](schema-objects-and-Oracle-JVM-utilities.md)
- [Developing Java Stored Procedures](developing-Java-stored-procedures.md)

### 3.1.2 About JNI Support

The Java Native Interface (JNI) is a standard programming interface for writing Java native methods and embedding the JVM into native applications. The primary goal of JNI is to provide binary compatibility of Java applications that use platform-specific native libraries.

Native methods can cause server failure, violate security, and corrupt data. Oracle Database does not support the use of JNI in Java applications. If you use JNI, then your application is not 100 percent pure Java and the native methods require porting between platforms.

### 3.1.3 About Utilizing SQLJ and JDBC with Java in the Database

You can use SQLJ and Java Database Connectivity (JDBC) APIs from a Java client. Both APIs establish a session with a given user name and password on the database and run SQL queries against the database. The following table lists the APIs and their description:

| API  | Description                                                                                                                       |
|:-----|:----------------------------------------------------------------------------------------------------------------------------------|
| JDBC | Use this API for more complex or dynamic SQL queries. JDBC requires you to establish the session, construct the query, and so on. |
| SQLJ | Use this API for easy SQL queries, both static and dynamic. SQLJ typically runs against a known table with known column names.    |

This section covers the following topics:

- Using JDBC

- Using SQLJ

- Example Comparing JDBC and SQLJ

- SQLJ Strong Typing Paradigm

- Translating a SQLJ Program

- Interaction with PL/SQL

#### 3.1.3.1 Using JDBC

JDBC is an industry-standard API that lets you embed SQL statements as Java method arguments. JDBC is based on the X/Open SQL Call Level Interface (CLI) and complies with the Entry Level of SQL-92 standard. Each vendor, such as Oracle, creates its JDBC implementation by implementing the interfaces of the standard `java.sql` package. Oracle provides the following JDBC drivers that implement these standard interfaces:

- The JDBC Thin driver, a 100 percent pure Java solution that you can use for either client-side applications or applets and requires no Oracle client installation.

- The JDBC OCI driver, which you use for client-side applications and requires an Oracle client installation.

- The server-side JDBC driver embedded in Oracle Database.

Using JDBC is a step-by-step process of performing the following tasks:

1.  Obtaining a connection handle
2.  Creating a statement object of some type for your desired SQL operation
3.  Assigning any local variables that you want to bind to the SQL operation
4.  Carrying out the operation
5.  Optionally retrieving the result sets

This process is sufficient for many applications, but becomes cumbersome for any complicated statements. Dynamic SQL operations, where the operations are not known until run time, require JDBC. However, in typical applications, this represents a minority of the SQL operations.

**See Also:**

[Oracle Database JDBC Developer’s Guide](../jjdbc/introducing-JDBC.md)

#### 3.1.3.2 Using SQLJ

SQLJ offers an industry-standard way to embed any static SQL operation directly into the Java source code in one simple step, without requiring the multiple steps of JDBC. Oracle SQLJ complies with the X3H2-98-320 American National Standards Institute (ANSI) standard.

SQLJ consists of a translator, which is a precompiler that supports standard SQLJ programming syntax, and a run-time component. After creating your SQLJ source code in a `.sqlj` file, you process it with the translator. The translator translates the SQLJ source code to standard Java source code, with SQL operations converted to calls to the SQLJ run time. In Oracle Database SQLJ implementation, the translator calls a Java compiler to compile the Java source code. When your SQLJ application runs, the SQLJ run time calls JDBC to communicate with the database.

SQLJ also enables you to catch errors in your SQL statements before run time. JDBC code, being pure Java, is compiled directly. The compiler cannot detect SQL errors. On the other hand, when you translate SQLJ code, the translator analyzes the embedded SQL statements semantically and syntactically, catching SQL errors during development, instead of allowing an end user to catch them when running the application.

Following is a complete example of a simple SQLJ program:

    import java.sql.*;
    import sqlj.runtime.ref.DefaultContext;
    import oracle.sqlj.runtime.Oracle;

    #sql iterator MyIter (String first_name, int employee_id, float salary);

    public class MyExample
    {
      public static void main (String args[]) throws SQLException
      {
        Oracle.connect("jdbc:oracle:thin:@localhost:5521:orcl", "HR", "<password>");
        #sql { INSERT INTO employees (first_name, employee_id, salary) VALUES ('SMITH', 32, 20000) };
        MyIter iter;
        #sql iter={ SELECT first_name, employee_id, salary FROM employees };
        while (iter.next())
        {
          System.out.println(iter.first_name()+" "+iter.employee_id()+" "+iter.salary());
        }
      }
    }

In the preceding example, you perform the following:

1.  Declare your iterators.

    SQLJ uses a strongly-typed version of JDBC result sets, known as iterators. An iterator has a specific number of columns of specific data types. You must define your iterator types before using them, as in this example.

        #sql ITERATOR MyIter (String first_name, int employee_id, float salary);

    This declaration results in SQLJ creating an iterator class, `MyIter`. Iterators of type `MyIter` can store results whose first column maps to a Java `String`, second column maps to a Java `int`, and third column maps to a Java `float`. This definition also names the three columns as `first_name`, `employee_id`, and `salary`, to match the column names of the referenced table in the database. `MyIter` is a named iterator.

2.  Connect to the database.

        Oracle.connect("jdbc:oracle:thin:@localhost:5521:orcl","HR", "<password>");

    SQLJ provides the `Oracle` class and its `connect()` method accomplishes the following important tasks:

    1.  Registers Oracle JDBC drivers that SQLJ uses to access the database, in this case, the JDBC Thin driver.

    2.  Opens a database connection for the specified schema, in this case, user `HR` with the specified password, at the specified URL. In this case, the URL points to host `localhost`, port `5521`, and SID `orcl`.

    3.  Establishes this connection as the default connection for the SQLJ statements. Although each JDBC statement must explicitly specify a connection object, a SQLJ statement can either implicitly use a default connection or optionally specify a different connection.

3.  Process a SQL statement. The following is accomplished:

    1.  Insert a row into the `employees` table:

            #sql {INSERT INTO employees (first_name, employee_id, salary) VALUES ('SMITH', 32, 20000)};

    2.  Instantiate and populate the iterator:

            MyIter iter;
            #sql iter={SELECT first_name, employee_id, salary FROM employees};

4.  Access the data that was populated within the iterator.

        while (iter.next())
        {
          System.out.println(iter.first_name()+" "+iter.employee_id()+" "+iter.salary());
        }

    The `next()` method is common to all iterators and plays the same role as the `next()` method of a JDBC result set, returning `true` and moving to the next row of data, if any rows remain. You can access the data in each row by calling iterator accessor methods whose names match the column names. This is a characteristic of all named iterators. In this example, you access the data using the methods `first_name()`, `employee_id()`, and `salary()`.

**See Also:**

[Oracle Database SQLJ Developer’s Guide](../jsqlj/intro-to-SQLJ.md)

#### 3.1.3.3 Example Comparing JDBC and SQLJ

The following is an example of a JDBC code and a SQLJ code that perform a simple operation:

##### JDBC:

    // Assume you already have a JDBC Connection object conn
    // Define Java variables
    String name;
    int id=37115;
    float salary=20000;

    // Set up JDBC prepared statement.
    PreparedStatement pstmt = conn.prepareStatement
    ("SELECT first_name FROM employees WHERE employee_id=? AND salary>?");
    pstmt.setInt(1, id);
    pstmt.setFloat(2, salary);

    // Execute query; retrieve name and assign it to Java variable.
    ResultSet rs = pstmt.executeQuery();
    while (rs.next())
    {
      name=rs.getString(1);
      System.out.println("Name is: " + name);
    }

    // Close result set and statement objects.
    rs.close()
    pstmt.close();

Assume that you have established a JDBC connection, `conn`. Next, you must do the following:

1.  Define the Java variables, `name`, `id`, and `salary`.

2.  Create a `PreparedStatement` instance.

    You can use a prepared statement whenever values in the SQL statement must be dynamically set. You can use the same prepared statement repeatedly with different variable values. The question marks (?) in the prepared statement are placeholders for Java variables. In the preceding example, these variables are assigned values using the `pstmt.setInt()` and `pstmt.setFloat()` methods. The first ? refers to the `int` variable `id` and is set to a value of `37115`. The second ? refers to the `float` variable `salary` and is set to a value of `20000`.

3.  Run the query and return the data into a `ResultSet` object.

4.  Retrieve the data of interest from the `ResultSet` object and display it. In this case, the `first_name` column. A result set usually contains multiple rows of data, although this example has only one row.

##### SQLJ:

    String name;
    int id=37115;
    float salary=20000;
    #sql {SELECT first_name INTO :name FROM employees WHERE employee_id=:id AND salary>:salary};
    System.out.println("Name is: " + name);

In addition to allowing SQL statements to be directly embedded in Java code, SQLJ supports Java host expressions, also known as bind expressions, to be used directly in the SQL statements. In the simplest case, a host expression is a simple variable, as in this example. However, more complex expressions are allowed as well. Each host expression is preceded by colon (:). This example uses Java host expressions, `name`, `id`, and `salary`. In SQLJ, because of its host expression support, you do not need a result set or equivalent when you are returning only a single row of data.

**Note:**

All SQLJ statements, including declarations, start with the `#sql` token.

#### 3.1.3.4 SQLJ Strong Typing Paradigm

SQLJ uses strong typing, such as iterators, instead of result sets. This enables the SQL instructions to be checked against the database during translation. For example, SQLJ can connect to a database and check your iterators against the database tables that will be queried. The translator will verify that they match, enabling you to catch SQL errors during translation that would otherwise not be caught until a user runs your application. Furthermore, if changes are subsequently made to the schema, then you can determine if these changes affect the application by rerunning the translator.

#### 3.1.3.5 Translating a SQLJ Program

Integrated development environments (IDEs), such as Oracle JDeveloper, can translate, compile, and customize your SQLJ program as you build it. Oracle JDeveloper is a Microsoft Windows-based visual development environment for Java programming. If you are not using an IDE, then use the front-end SQLJ utility, `sqlj`. You can run it as follows:

    %sqlj MyExample.sqlj

The SQLJ translator checks the syntax and semantics of your SQL operations. You can enable online checking to check your operations against the database. If you choose to do this, then you must specify an example database schema in your translator option settings. It is not necessary for the schema to have data identical to the one that the program will eventually run against. However, the tables must have columns with corresponding names and data types. Use the user option to enable online checking and specify the user name, password, and URL of your schema, as in the following example:

    %sqlj -user=HR@jdbc:oracle:thin:@localhost:5521:orcl MyExample.sqlj
    Password: password

#### 3.1.3.6 Interaction with PL/SQL

All Oracle JDBC drivers communicate seamlessly with Oracle SQL and PL/SQL, and it is important to note that SQLJ interoperates with PL/SQL. You can start using SQLJ without having to rewrite any PL/SQL stored procedures. Oracle SQLJ includes syntax for calling PL/SQL stored procedures and also lets you embed anonymous PL/SQL blocks in SQLJ statements.

### 3.1.4 About Using the Command-Line Interface

The command-line interface to Oracle JVM is analogous to using the JDK or JRE shell commands. You can:

- Use the standard `-classpath` syntax to indicate where to find the classes to load

- Set the system properties by using the standard `-D` syntax

The interface is a PL/SQL function that takes a string (`VARCHAR2`) argument, parses it as a command-line input and if it is properly formed, runs the indicated Java method in Oracle JVM. To do this, PL/SQL package `DBMS_JAVA` provides the following functions:

- runjava

- runjava_in_current_session

#### runjava

This function takes the Java command line as its only argument and runs it in Oracle JVM. The return value is null on successful completion, otherwise an error message. The format of the command line is the same as that taken by the JDK shell command, that is:

    [option switches] name_of_class_to_execute [arg1 arg2 ... argn]

You can use the option switches `-classpath, -D, -Xbootclasspath,` and `-jar.` This function differs from the `runjava_in_current_session` function in that it clears any Java state remaining from previous use of Java in the session, prior to running the current command. This is necessary, in particular, to guarantee that static variable values derived at class initialization time from `-classpath` and `-D` arguments reflect the values of those switches in the current command line.

    FUNCTION runjava(cmdline VARCHAR2) RETURN VARCHAR2;

#### runjava_in_current_session

This function is the same as the `runjava` function, except that it does not clear Java state remaining from previous use of Java in the session, prior to executing the current command line.

    FUNCTION runjava_in_current_session(cmdline VARCHAR2) RETURN VARCHAR2;

#### Syntax

The syntax of the command line is of the following form:

    [-options] classname [arguments...]
    [-options] -jar jarfile [arguments...]

#### Options

    -classpath
    -D
    -Xbootclasspath
    -Xbootclasspath/a
    -Xbootclasspath/p
    -cp

**Note:**

The effect of the first form is to run the main method of the class identified by classname with the arguments. The effect of the second form is to run the main method of the class identified by the `Main-Class` attribute in the manifest of the JAR file identified by JAR. This is analogous to how the JDK/JRE interprets this syntax.

#### Argument Summary

The following table summarizes the command-line arguments.

Table 3-1 Command Line Argument Summary

| Argument           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:-------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| classpath          | Accepts a colon (:) separated (semicolon-separated on Windows systems) list of directories, JAR archives, and ZIP archives to search for class files. In general, the value of `-classpath` or similar arguments refer to file system locations as they would in a standard Java runtime. You also have an extension to this syntax to allow for terms that refer to database resident Java objects and sets of bytes.                                                                                                                                         |
| D                  | Establishes values for system properties when there is no existing Java session state. The default behavior of the command-line interface, that is, the `runjava` function, is to terminate any existing Java session prior to running the new command. On the other hand, the alternative function, `runjava_in_current_session` leaves any existing session in place. So, values established with the `-D` option always take effect when `runjava` function is used, but the values may not take effect when `runjava_in_current_session` function is used. |
| Xbootclasspath     | Accepts a colon (:) separated (semicolon-separated on Windows systems) list of directories, JAR archives, and ZIP archives. This option is used to set search path for bootstrap classes and resources.                                                                                                                                                                                                                                                                                                                                                        |
| `Xbootclasspath/a` | Accepts a colon (:) separated (semicolon-separated on Windows systems) list of directories, JAR archives, and ZIP archives. This is appended to the end of bootstrap class path.                                                                                                                                                                                                                                                                                                                                                                               |
| `Xbootclasspath/p` | Accepts a colon (:) separated (semicolon-separated on Windows systems) list of directories, JAR archives, and ZIP archives. This is added in front of bootstrap class path.                                                                                                                                                                                                                                                                                                                                                                                    |
| `cp`               | Acts as a synonym of `-classpath`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |

**Note:**

System classes created by `create java system` are always used before using any file or folder that are found using the `-Xbootclasspath `option.

**Related Topics**

- About Using the Command-Line Interface

### 3.1.5 Overview of Using the Client-Side Stub

Oracle Database 10g introduced the client-side stub, formerly known as native Java interface, for calls to server-side Java code. It is a simplified application integration. Client-side and middle-tier Java applications can directly call Java in the database without defining a PL/SQL wrapper. The client-side stub uses the server-side Java class reflection capability.

In previous releases, calling Java stored procedures and functions from a database client required Java Database Connectivity (JDBC) calls to the associated PL/SQL wrappers. Each wrapper had to be manually published with a SQL signature and a Java implementation. This had the following disadvantages:

- The signatures permitted only Java types that had direct SQL equivalents

- Exceptions issued in Java were not properly returned

Starting from Oracle Database 12c Release 2 (12.2.0.1), you can use the Oracle JVM Web Services Call-Out Utility for generating the client-side stub.

**Related Topics**

- [Architecture of Oracle JVM Web Services Call-Out Utility](database-as-web-service-consumer.md)

#### 3.1.5.1 Using the Default Service Feature

Starting from Oracle Database 11g release 1 (11.1), Oracle Database client provides a new default connection feature. If you install Oracle Database client, then you need not specify all the details of the database server in the connection URL. Under certain conditions, Oracle Database connection adapter requires only the host name of the computer where the database is installed.

For example, in the JDBC connection URL syntax, that is:

    jdbc:oracle:driver_type:[username/password]@[//]host_name[:port][:ORCL]

,the following have become optional:

- `//` is optional.

- `:port `is optional.

  You must specify a port only if the default Oracle Net listener port (1521) is not used.

- `:ORCL` or the service name is optional.

  The connection adapter for Oracle Database Client connects to the default service on the host. On the host, this is set to `ORCL` in the `listener.ora` file.

**Note:**

Default service is a feature since Oracle Database 11g Release 1 (11.1). If you use any version prior to Oracle Database 11g Client to connect to the database, then you must specify the `SID`.

#### 3.1.5.2 Testing the Default Service with a Basic Configuration

The following code snippet shows a basic configuration of the `listener.ora` file, where the default service is defined:

    MYLISTENER = (ADDRESS_LIST=(ADDRESS=(PROTOCOL=tcp)(HOST=testserver1)(PORT=1521)))
    DEFAULT_SERVICE_MYLISTENER=dbjf.app.myserver.com
    SID_LIST_MYLISTENER = (SID_LIST=(SID_DESC=(SID_NAME=dbjf)
    (GLOBAL_DBNAME=dbjf.app.myserver.com)(ORACLE_HOME=/test/oracle))
    )

After defining the `listener.ora` file, restart the listener with the following command:

    lsnrctl start mylistener

Now, any of the following URLs should work with this configuration of the `listener.ora` file:

- `jdbc:oracle:thin:@//testserver1.myserver.com.com`

- `jdbc:oracle:thin:@//testserver1.myserver.com:1521`

- `jdbc:oracle:thin:@testserver1.myserver.com`

- `jdbc:oracle:thin:@testserver1.myserver.com:1521`

- `jdbc:oracle:thin:@(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=testserver1.myserver.com)(PORT=1521)))`

- `jdbc:oracle:thin:@(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=testserver1.myserver.com)))`

- `jdbc:oracle:thin:@(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=testserver1.myserver.com)(PORT=1521))(CONNECT_DATA=(SERVICE_NAME=)))`
