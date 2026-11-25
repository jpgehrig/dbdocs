If you publish Java methods as functions, then you can call them from SQL `SELECT`, `INSERT`, `UPDATE`, `DELETE`, `CALL`, `EXPLAIN PLAN`, `LOCK TABLE`, and `MERGE` statements. For example, assume that the executable for the following Java class is stored in Oracle Database:

    public class Formatter
    {
      public static String formatEmp (String empName, String jobTitle)
      {
        empName = empName.substring(0,1).toUpperCase() +
                                         empName.substring(1).toLowerCase();
        jobTitle = jobTitle.toLowerCase();
        if (jobTitle.equals("analyst"))
          return (new String(empName + " is an exempt analyst"));
        else
          return (new String(empName + " is a non-exempt " + jobTitle));
      }
    }

The `Formatter` class has the `formatEmp()` method, which returns a formatted string containing a staffer's name and job status. Write the call specification for this method, as follows:

    CREATE OR REPLACE FUNCTION format_emp (ename VARCHAR2, job VARCHAR2)
    RETURN VARCHAR2
    AS LANGUAGE JAVA
    NAME 'Formatter.formatEmp (java.lang.String, java.lang.String)
    return java.lang.String';

Now, call the `format_emp` function to format a list of employees:

    SQL> SELECT format_emp(first_name, job_id) AS "Employees" FROM employees
      2   WHERE job_id NOT IN ('AC_MGR', 'AD_PRES') ORDER BY first_name;

    Employees
    --------------------------------------------
    Adams is a non-exempt clerk
    Allen is a non-exempt salesman
    Ford is an exempt analyst
    James is a non-exempt clerk
    Martin is a non-exempt salesman
    Miller is a non-exempt clerk
    Scott is an exempt analyst
    Smith is a non-exempt clerk
    Turner is a non-exempt salesman
    Ward is a non-exempt salesman

### Restrictions

A Java method must adhere to the following rules, which are meant to control side effects:

- When you call a method from a `SELECT` statement or parallel `INSERT`, `UPDATE`, or `DELETE` statements, the method cannot modify any database tables.

- When you call a method from an `INSERT`, `UPDATE`, or `DELETE` statement, the method cannot query or modify any database tables modified by that statement.

- When you call a method from a `SELECT`, `INSERT`, `UPDATE`, or `DELETE` statement, the method cannot run SQL transaction control statements, such as `COMMIT`, session control statements, such as `SET ROLE`, or system control statements, such as `ALTER SYSTEM`. In addition, the method cannot run data definition language (DDL) statements, such as `CREATE`, because they are followed by an automatic commit.

If any SQL statement inside the method violates any of the preceding rules, then you get an error at run time.
