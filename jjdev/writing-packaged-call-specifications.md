A PL/SQL package is a schema object that groups logically related types, items, and subprograms. Usually, packages have two parts, a specification and a body. The specification is the interface to your applications and declares the types, constants, variables, exceptions, cursors, and subprograms available for use. The body defines the cursors and subprograms.

In SQL\*Plus, you can define PL/SQL packages interactively, using the following syntax:

    CREATE [OR REPLACE] PACKAGE package_name
      [AUTHID {CURRENT_USER | DEFINER}] {IS | AS}
      [type_definition [type_definition] ...]
      [cursor_spec [cursor_spec] ...]
      [item_declaration [item_declaration] ...]
      [{subprogram_spec | call_spec} [{subprogram_spec | call_spec}]...]
    END [package_name];

    [CREATE [OR REPLACE] PACKAGE BODY package_name {IS | AS}
      [type_definition [type_definition] ...]
      [cursor_body [cursor_body] ...]
      [item_declaration [item_declaration] ...]
      [{subprogram_spec | call_spec} [{subprogram_spec | call_spec}]...]
    [BEGIN
      sequence_of_statements]
    END [package_name];]

The specification holds public declarations, which are visible to your application. The body contains implementation details and private declarations, which are hidden from your application. Following the declarative part of the package is the body, which is the optional initialization part. It holds statements that initialize package variables. It is run only once, the first time you reference the package.

A call specification declared in a package specification cannot have the same signature, that is, the name and parameter list, as a subprogram in the package body. If you declare all the subprograms in a package specification as call specifications, then the package body is not required, unless you want to define a cursor or use the initialization part.

The `AUTHID` clause determines whether all the packaged subprograms run with the privileges of their definer (`AUTHID DEFINER`), which is the default, or invoker (`AUTHID CURRENT_USER`). It also determines whether unqualified references to schema objects are resolved in the schema of the definer or invoker.

Example 6-5 provides an example of packaged call specification.

Example 6-5 Packaged Call Specification

Consider a Java class, `DeptManager`, which consists of methods for adding a new department, dropping a department, and changing the location of a department. Note that the `addDept()` method uses a database sequence to get the next department number. The three methods are logically related, and therefore, you may want to group their call specifications in a PL/SQL package.

    import java.sql.*;
    import java.io.*;
    import oracle.jdbc.*;

    public class DeptManager
    {
      public static void addDept (String deptName, String deptLoc) throws SQLException
      {
        Connection conn = DriverManager.getConnection("jdbc:default:connection:");
        String sql = "SELECT deptnos.NEXTVAL FROM dual";
        String sql2 = "INSERT INTO dept VALUES (?, ?, ?)";
        int deptID = 0;
        try
        {
          PreparedStatement pstmt = conn.prepareStatement(sql);
          ResultSet rset = pstmt.executeQuery();
          while (rset.next())
          {
            deptID = rset.getInt(1);
          }
          pstmt = conn.prepareStatement(sql2);
          pstmt.setInt(1, deptID);
          pstmt.setString(2, deptName);
          pstmt.setString(3, deptLoc);
          pstmt.executeUpdate();
          rset.close();
          pstmt.close();
        }
        catch (SQLException e)
        {
          System.err.println(e.getMessage());
        }
      }

      public static void dropDept (int deptID) throws SQLException
      {
        Connection conn = DriverManager.getConnection("jdbc:default:connection:");
        String sql = "DELETE FROM dept WHERE deptno = ?";
        try
        {
          PreparedStatement pstmt = conn.prepareStatement(sql);
          pstmt.setInt(1, deptID);
          pstmt.executeUpdate();
          pstmt.close();
        }
        catch (SQLException e)
        {
          System.err.println(e.getMessage());
        }
      }

      public static void changeLoc (int deptID, String newLoc) throws SQLException
      {
        Connection conn = DriverManager.getConnection("jdbc:default:connection:");
        String sql = "UPDATE dept SET loc = ? WHERE deptno = ?";
        try
        {
          PreparedStatement pstmt = conn.prepareStatement(sql);
          pstmt.setString(1, newLoc);
          pstmt.setInt(2, deptID);
          pstmt.executeUpdate();
          pstmt.close();
        }
        catch (SQLException e)
        {
          System.err.println(e.getMessage());
        }
      }
    }

Suppose you want to package the methods `addDept()`, `dropDept()`, and `changeLoc()`. First, you must create the package specification, as follows:

    CREATE OR REPLACE PACKAGE dept_mgmt AS
    PROCEDURE add_dept (dept_name VARCHAR2, dept_loc VARCHAR2);
    PROCEDURE drop_dept (dept_id NUMBER);
    PROCEDURE change_loc (dept_id NUMBER, new_loc VARCHAR2);
    END dept_mgmt;

Then, you must create the package body by writing the call specifications for the Java methods, as follows:

    CREATE OR REPLACE PACKAGE BODY dept_mgmt AS
    PROCEDURE add_dept (dept_name VARCHAR2, dept_loc VARCHAR2)
    AS LANGUAGE JAVA
    NAME 'DeptManager.addDept(java.lang.String, java.lang.String)';

    PROCEDURE drop_dept (dept_id NUMBER)
    AS LANGUAGE JAVA
    NAME 'DeptManager.dropDept(int)';

    PROCEDURE change_loc (dept_id NUMBER, new_loc VARCHAR2)
    AS LANGUAGE JAVA
    NAME 'DeptManager.changeLoc(int, java.lang.String)';
    END dept_mgmt;

To reference the stored procedures in the `dept_mgmt` package, use the dot notation, as follows:

    CALL dept_mgmt.add_dept('PUBLICITY', 'DALLAS');
