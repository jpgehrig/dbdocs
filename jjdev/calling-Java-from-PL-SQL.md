You can call Java stored procedures from any PL/SQL block, subprogram, or package. For example, assume that the executable for the following Java class is stored in Oracle Database:

    import java.sql.*;
    import oracle.jdbc.*;

    public class Adjuster
    {
      public static void raiseSalary (int empNo, float percent) throws SQLException
      {
        Connection conn = DriverManager.getConnection("jdbc:default:connection:");
        String sql = "UPDATE employees SET salary = salary * ? WHERE employee_id = ?";
        try
        {
          PreparedStatement pstmt = conn.prepareStatement(sql);
          pstmt.setFloat(1, (1 + percent / 100));
          pstmt.setInt(2, empNo);
          pstmt.executeUpdate();
          pstmt.close();
        }
        catch (SQLException e)
        {
          System.err.println(e.getMessage());
        }
      }
    }

The `Adjuster` class has one method, which raises the salary of an employee by a given percentage. Because `raiseSalary()` is a `void` method, you must publish it as a procedure, as follows:

    CREATE OR REPLACE PROCEDURE raise_salary (empno NUMBER, pct NUMBER)
    AS LANGUAGE JAVA
    NAME 'Adjuster.raiseSalary(int, float)';

In the following example, you call the `raise_salary` procedure from an anonymous PL/SQL block:

    DECLARE
    emp_id NUMBER;
    percent NUMBER;
    BEGIN
    -- get values for emp_id and percent
    raise_salary(emp_id, percent);
    ...
    END;

In the following example, you call the `row_count` function, which defined in [Example 6-3](writing-top-level-call-specifications.md), from a standalone PL/SQL stored procedure:

    CREATE PROCEDURE calc_bonus (emp_id NUMBER, bonus OUT NUMBER) AS
    emp_count NUMBER;
    ...
    BEGIN
    emp_count := row_count('employees');
    ...
    END;

In the following example, you call the `raise_sal` method of the `Employee` object type, which is defined in "[Implementing Object Type Methods](writing-object-type-call-specifications.md)", from an anonymous PL/SQL block:

    DECLARE
    emp_id NUMBER(4);
    v emp_type;
    BEGIN
    -- assign a value to emp_id
    SELECT VALUE(e) INTO v FROM emps e WHERE empno = emp_id;
    v.raise_sal(500);
    UPDATE emps e SET e = v WHERE empno = emp_id;
    ...
    END;
