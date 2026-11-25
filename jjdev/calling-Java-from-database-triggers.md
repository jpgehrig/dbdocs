A database trigger is a stored program that is associated with a specific table or view. Oracle Database runs the trigger automatically whenever a data manipulation language (DML) operation affects the table or view.

When a triggering event occurs, the trigger runs and either a PL/SQL block or a `CALL` statement performs the action. A statement trigger runs once, before or after the triggering event. A row trigger runs once for each row affected by the triggering event.

In a database trigger, you can reference the new and old values of changing rows by using the correlation names `new` and `old`. In the trigger-action block or `CALL` statement, column names must be prefixed with `:new` or `:old`.

The following are examples of calling Java stored procedures from a database trigger:

- Example 7-3

- Example 7-4

Example 7-3 Calling Java Stored Procedure from Database Trigger - I

Assume you want to create a database trigger that uses the following Java class to log out-of-range salary increases:

    import java.sql.*;
    import java.io.*;
    import oracle.jdbc.*;

    public class DBTrigger
    {
      public static void logSal (int empID, float oldSal, float newSal)
                                                            throws SQLException
      {
        Connection conn = DriverManager.getConnection("jdbc:default:connection:");
        String sql = "INSERT INTO sal_audit VALUES (?, ?, ?)";
        try
        {
          PreparedStatement pstmt = conn.prepareStatement(sql);
          pstmt.setInt(1, empID);
          pstmt.setFloat(2, oldSal);
          pstmt.setFloat(3, newSal);
          pstmt.executeUpdate();
          pstmt.close();
        }
        catch (SQLException e)
        {
          System.err.println(e.getMessage());
        }
      }
    }

The `DBTrigger` class has one method, `logSal()`, which inserts a row into the `sal_audit` table. Because `logSal()` is a `void` method, you must publish it as a procedure:

    CREATE OR REPLACE PROCEDURE log_sal (
     emp_id NUMBER,
     old_sal NUMBER,
     new_sal NUMBER
    )
    AS LANGUAGE JAVA
    NAME 'DBTrigger.logSal(int, float, float)';

Next, create the `sal_audit` table, as follows:

    CREATE TABLE sal_audit (
     empno NUMBER,
     oldsal NUMBER,
     newsal NUMBER
    );

Finally, create the database trigger, which fires when a salary increase exceeds 20 percent:

    CREATE OR REPLACE TRIGGER sal_trig
    AFTER UPDATE OF salary ON employees
    FOR EACH ROW
    WHEN (new.salary > 1.2 * old.salary)
    CALL log_sal(:new.employee_id, :old.salary, :new.salary);

When you run the following `UPDATE` statement, it updates all rows in the `employees` table:

    SQL> UPDATE employee SET salary = salary + 300;

For each row that meets the condition set in the `WHEN` clause of the trigger, the trigger runs and the Java method inserts a row into the `sal_audit` table.

    SQL> SELECT * FROM sal_audit;

         EMPNO     OLDSAL     NEWSAL
    ---------- ---------- ----------
          7369        800       1100
          7521       1250       1550
          7654       1250       1550
          7876       1100       1400
          7900        950       1250
          7934       1300       1600

    6 rows selected.

Example 7-4 Calling Java Stored Procedure from Database Trigger - II

Assume you want to create a trigger that inserts rows into a database view, which is defined as follows:

    CREATE VIEW emps AS
    SELECT empno, ename, 'Sales' AS dname FROM sales
    UNION ALL
    SELECT empno, ename, 'Marketing' AS dname FROM mktg;

The `sales` and `mktg` database tables are defined as:

    CREATE TABLE sales (empno NUMBER(4), ename VARCHAR2(10));
    CREATE TABLE mktg (empno NUMBER(4), ename VARCHAR2(10));

You must write an `INSTEAD OF` trigger because rows cannot be inserted into a view that uses set operators, such as `UNION ALL`. Instead, the trigger will insert rows into the base tables.

First, add the following Java method to the `DBTrigger` class, which is defined in Example 7-3:

    public static void addEmp (int empNo, String empName, String deptName)
                                                                  throws SQLException
    {
      Connection conn = DriverManager.getConnection("jdbc:default:connection:");
      String tabName = (deptName.equals("Sales") ? "sales" : "mktg");
      String sql = "INSERT INTO " + tabName + " VALUES (?, ?)";
      try
      {
        PreparedStatement pstmt = conn.prepareStatement(sql);
        pstmt.setInt(1, empNo);
        pstmt.setString(2, empName);
        pstmt.executeUpdate();
        pstmt.close();
      }
      catch (SQLException e)
      {
        System.err.println(e.getMessage());
      }
    }

The `addEmp()` method inserts a row into the `sales` or `mktg` table depending on the value of the `deptName` parameter. Write the call specification for this method, as follows:

    CREATE OR REPLACE PROCEDURE add_emp (
     emp_no NUMBER,
     emp_name VARCHAR2,
     dept_name VARCHAR2
    )
    AS LANGUAGE JAVA
    NAME 'DBTrigger.addEmp(int, java.lang.String, java.lang.String)';

Next, create the `INSTEAD OF` trigger, as follows:

    CREATE OR REPLACE TRIGGER emps_trig
    INSTEAD OF INSERT ON emps
    FOR EACH ROW
    CALL add_emp(:new.empno, :new.ename, :new.dname);

When you run each of the following `INSERT` statements, the trigger runs and the Java method inserts a row into the appropriate base table:

    SQL> INSERT INTO emps VALUES (8001, 'Chand', 'Sales');
    SQL> INSERT INTO emps VALUES (8002, 'Van Horn', 'Sales');
    SQL> INSERT INTO emps VALUES (8003, 'Waters', 'Sales');
    SQL> INSERT INTO emps VALUES (8004, 'Bellock', 'Marketing');
    SQL> INSERT INTO emps VALUES (8005, 'Perez', 'Marketing');
    SQL> INSERT INTO emps VALUES (8006, 'Foucault', 'Marketing');

    SQL> SELECT * FROM sales;

         EMPNO ENAME
    ---------- ----------
          8001 Chand
          8002 Van Horn
          8003 Waters

    SQL> SELECT * FROM mktg;

         EMPNO ENAME
    ---------- ----------
          8004 Bellock
          8005 Perez
          8006 Foucault

    SQL> SELECT * FROM emps;

         EMPNO ENAME      DNAME
    ---------- ---------- ---------
          8001 Chand      Sales
          8002 Van Horn   Sales
          8003 Waters     Sales
          8004 Bellock    Marketing
          8005 Perez      Marketing
          8006 Foucault   Marketing
