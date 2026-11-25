Oracle Database is a relational database that you can use to store, modify and use data.

The Java Database Connectivity (JDBC) standard is used by Java applications to access and manipulate data in relational databases.

JDBC is an industry-standard application programming interface (API) that lets you access a RDBMS using SQL from Java. JDBC complies with the Entry Level of the JDBC escape standard. Each vendor implements the JDBC Specification with its own extensions.

Universal Connection Pool (UCP) is a connection pool used to cache the database connection objects to reuse the connections, thus improving the performance.

Java in the Database (OJVM) helps group SQL operations with Java data logic and load them into the database for in-place processing.

**See Also:**

[`http://www.oracle.com/technetwork/java/overview-141217.html`](http://www.oracle.com/technetwork/java/overview-141217.html)

This chapter introduces you to the JDBC driver, Universal Connection Pool (UCP) and Java in the Database (OJVM) with Oracle Database 12c Release 2 (12.2)

- Java Database Connectivity Driver (JDBC)

- Universal Connection Pool (UCP)

- Java in the Database (OJVM)

### Java Database Connectivity Driver (JDBC)

JDBC is a database access protocol that enables you to connect to a database and run SQL statement and queries on the database. JDBC drivers implement and comply with the latest JDBC specifications. Java application need to have `ojdbc8.jar` compatible with JDK8 in their classpath.

The core Java class libraries provide the JDBC APIs, `java.sql` and `javax.sql`

The following sections describe Oracle support for the JDBC standard:

- Oracle JDBC Thin Driver

- Oracle JDBC Packages

#### Oracle JDBC Thin Driver

Oracle recommends using the JDBC Thin Driver for most requirements. The JDBC Thin Driver will work on any system with a suitable Java Virtual Machine. (JVM). Some other client drivers that Oracle provides are JDBC thin driver, Oracle Call Interface (OCI) driver, Server side thin driver, and server side internal driver.

The JDBC Thin Driver is a pure Java, Type IV driver. The JDBC driver version )ojdbc8.jar) inludes support for JDK 8.

JDBC Thin Driver communicates with the server using SQL\*Net to access the database.

**See Also:**

Oracle Database JDBC Developer’s Guide

Action Item 1: Change the DB_URL to point to your database. If you need help, refer to the DataSourceSample.java on Github.

    import java.sql.Connection;
    import java.sql.SQLException;
    import java.sql.DatabaseMetaData;

    import oracle.jdbc.pool.OracleDataSource;
    import oracle.jdbc.OracleConnection;

    public class DataSourceSample {
      // The recommended format of a connection URL is the long format with the
      // connection descriptor.
      // final static String DB_URL= "jdbc:oracle:thin:@(DESCRIPTION=(ADDRESS=(HOST=myhost)(PORT=1521)(PROTOCOL=tcp))(CONNECT_DATA=(SERVICE_NAME=myorcldbservicename)))";

      final static String DB_URL= "jdbc:oracle:thin:@(DESCRIPTION=(ADDRESS=(HOST=localhost)(PORT=5521)(PROTOCOL=tcp))(CONNECT_DATA=(SERVICE_NAME=service name)))";
      final static String DB_USER = "username";
      final static String DB_PASSWORD = password;

      public static void main (String args[]) throws SQLException {

        OracleDataSource ods = new OracleDataSource();
        ods.setURL(DB_URL);
        ods.setUser(DB_USER);
        ods.setPassword(DB_PASSWORD);

        // With AutoCloseable, the connection is closed automatically.
        try (OracleConnection connection = (OracleConnection)
          ods.getConnection()) {
          // Get the JDBC driver name and version
          DatabaseMetaData dbmd = connection.getMetaData();
          System.out.println("Driver Name: " + dbmd.getDriverName());
          System.out.println("Driver Version: " +
            dbmd.getDriverVersion());
          System.out.println("Database Username is: " +
            connection.getUserName());
        }
      }
    }

### Universal Connection Pool

Connection pools help improve performance by reusing connection objects and reducing the number of times that connection objects are created.

Oracle Universal Connection Pool (UCP) is a feature rich Java connection pool that provides connection pool functionalities, along with high availability, scalability and load balancing with the help of tighter integration with Oracle Database configurations.

A Java application or container must have `ucp.jar` in their classpath, along with the `ojdbc8.jar` (JDK8), to be able to use UCP.

**See Also:**

Oracle Universal Connection Pool Developer’s Guide

Action Item 2: Change the DB_URL to point to your database.

    Import java.sql.Connection;
    import java.sql.ResultSet;
    import java.sql.SQLException;
    import java.sql.Statement;

    import oracle.ucp.jdbc.PoolDataSourceFactory;
    import oracle.ucp.jdbc.PoolDataSource;

    public class UCPSample {
      // final static String DB_URL=   "jdbc:oracle:thin:@(DESCRIPTION=(ADDRESS=(HOST=myhost)(PORT=1521)(PROTOCOL=tcp))(CONNECT_DATA=(SERVICE_NAME=myorcldbservicename)))";

      final static String DB_USER = "username";
      final static String DB_PASSWORD = "pwd";
      final static String CONN_FACTORY_CLASS_NAME = "oracle.jdbc.pool.OracleDataSource";

      /*
       * The sample demonstrates UCP as client side connection pool.
       */
      public static void main(String args[]) throws Exception {
        // Get the PoolDataSource for UCP
        PoolDataSource pds = PoolDataSourceFactory.getPoolDataSource();

        // Set the connection factory first before all other properties
        pds.setConnectionFactoryClassName(CONN_FACTORY_CLASS_NAME);
        pds.setURL(DB_URL);
        pds.setUser(DB_USER);
        pds.setPassword(DB_PASSWORD);
        pds.setConnectionPoolName("JDBC_UCP_POOL");

        // Default is 0. Set the initial number of connections to be
        // created when UCP is started.
        pds.setInitialPoolSize(5);

        // Default is 0. Set the minimum number of connections
        // that is maintained by UCP at runtime.
        pds.setMinPoolSize(5);

        // Default is Integer.MAX_VALUE (2147483647). Set the maximum
        // number of connections allowed on the connection pool.
        pds.setMaxPoolSize(20);

        // Default is 30secs. Set the frequency in seconds to enforce
        // the timeout properties. Applies to
        // inactiveConnectionTimeout(int secs),
        // AbandonedConnectionTimeout(secs)&
        //TimeToLiveConnectionTimeout(int secs).
        // Range of valid values is 0 to Integer.MAX_VALUE.
        pds.setTimeoutCheckInterval(5);

        // Default is 0. Set the maximum time, in seconds, that a
        // connection remains available in the connection pool.
        pds.setInactiveConnectionTimeout(10);

        System.out.println("Available connections before checkout: "
            + pds.getAvailableConnectionsCount());
        System.out.println("Borrowed connections before checkout: "
            + pds.getBorrowedConnectionsCount());
        // Get the database connection from UCP.
        try (Connection conn = pds.getConnection()) {
          System.out.println("Available connections after checkout: "
              + pds.getAvailableConnectionsCount());
          System.out.println("Borrowed connections after checkout: "
              + pds.getBorrowedConnectionsCount());
          // Perform a database operation
          printEmployees(conn);
        } catch (SQLException e) {
          System.out.println("UCPSample - " + "SQLException occurred : "
              + e.getMessage());
        }
        System.out.println("Available connections after checkin: "
            + pds.getAvailableConnectionsCount());
        System.out.println("Borrowed connections after checkin: "
            + pds.getBorrowedConnectionsCount());
      }
     /*
      * Displays first_name and last_name from the employees table.
      */
      public static void printEmployees(Connection connection)
         throws SQLException {
        // Statement and ResultSet are AutoCloseable and closed
        // automatically.
        try (Statement statement = connection.createStatement()) {
          try (ResultSet resultSet = statement
              .executeQuery("select first_name, last_name from
                employees")) {
            System.out.println("FIRST_NAME" + "  " + "LAST_NAME");
            System.out.println("---------------------");
            while (resultSet.next())
              System.out.println(resultSet.getString(1) + " "
                  + resultSet.getString(2) + " ");
          }
        }
      }
    }

### Java in the Database (OJVM)

Oracle Database has a Java Virtual Machine (JVM) that resides in the server. It helps Java applications running in the Oracle JVM on the server to access data present on the same system and same process.

Java in the Database is recommended for applications that are data-intensive. JVM has the ability to use the underlying Oracle RDBMS libraries directly, without the use of a network connection between the Java code and SQL data. This helps improve performance and execution. For data access, Oracle Database uses server-side internal driver when Java code runs on the server.

Action Item 3: Connect to the database through SQLPlus and run [ServersideConnect.sql](https://github.com/oracle/oracle-db-examples/blob/master/java/ojvm/ServersideConnect.sql) before invoking [ServersideConnect.java](https://github.com/oracle/oracle-db-examples/blob/master/java/ojvm/ServersideConnect.java). For more information, refer to the samples of Github.

ServersideConnect.sql

    Rem NAME
    Rem ServersideConnect.sql
    Rem
    Rem DESCRIPTION
    Rem SQL for invoking the method which gets a server side connection to
    rem Reads the content of the Java source from ServersideConnect.java
    rem then compiles it
    connect username/pwd
    CREATE OR REPLACE AND COMPILE JAVA SOURCE NAMED ServersideConnect_src AS
    @ ServersideConnect.java
    /
    show error
    rem A wrapper (a.k.a. Call Spec), to invoke Java
    rem function in the database from SQL, PL/SQL, and client applications
    CREATE OR REPLACE PROCEDURE ServersideConnect_proc AS
    LANGUAGE JAVA NAME 'ServersideConnect.jrun ()';
    /
    rem running the sample
    connect username/pwd
    SET SERVEROUTPUT ON SIZE 10000
    CALL dbms_java.set_output (10000);

    execute ServersideConnect_proc;

    InternalT2Server.java
    import java.sql.Connection;
    import java.sql.ResultSet;
    import java.sql.SQLException;
    import java.sql.Statement;

    import oracle.jdbc.driver.OracleDriver;
    import oracle.jdbc.pool.OracleDataSource;

    public class ServersideConnect {

      static public void jrun() throws SQLException {
        // For testing ServersideConnect
        // test("jdbc:oracle:kprb:@");
        method1("jdbc:default:connection");
        method2();
      }
     /*
      * Shows using the server side Type 2 driver a.k.a KPRB driver
      */
     static public void method1 (String url) throws SQLException {
        Connection connection = null;
        try {
         // Method 1: Using OracleDataSource
          OracleDataSource ods = new OracleDataSource();
          ods.setURL(url);
          connection = ods.getConnection();
          System.out.println("Method 1: Getting Default Connection "
              + "using OracleDataSource");
          // Perform database operation
          printEmployees(connection);
        }
    }

    static public void method2 () throws SQLException {
       Connection connection = null;
       try {
            OracleDriver ora = new OracleDriver();
            connection = ora.defaultConnection();
            System.out.println("Method 2: Getting Default Connection "
              + "using OracleDriver");
            // Perform database operation
            printEmployees(connection);
       }
    }

     /*
      * Displays employee_id and first_name from the employees table.
      */
      static public void printEmployees(Connection connection)
         throws SQLException {
        ResultSet resultSet = null;
        Statement statement = null;
        try {
          statement = connection.createStatement();
          resultSet = statement.executeQuery("SELECT employee_id, first_name"
             +    " FROM employees order by employee_id");
          while (resultSet.next()) {
            System.out.println("Emp no: " + resultSet.getInt(1) + " Emp name: "
                + resultSet.getString(2));
          }
        }
        catch (SQLException ea) {
          System.out.println("Error during execution: " + ea);
          ea.printStackTrace();
        }
        finally {
          if (resultSet != null) resultSet.close();
          if (statement != null) statement.close();
        }
      }
    }
