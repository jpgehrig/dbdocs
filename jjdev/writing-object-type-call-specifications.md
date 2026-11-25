In SQL, object-oriented programming is based on object types, which are user-defined composite data types that encapsulate a data structure along with the functions and procedures required to manipulate the data. The variables that form the data structure are known as attributes. The functions and procedures that characterize the behavior of the object type are known as methods, which can be written in Java.

As with a package, an object type has two parts: a specification and a body. The specification is the interface to your applications and declares a data structure, which is a set of attributes, along with the operations or methods required to manipulate the data. The body implements the specification by defining PL/SQL subprogram bodies or call specifications.

If the specification declares only attributes or call specifications, then the body is not required. If you implement all your methods in Java, then you can place their call specifications in the specification part of the object type and omit the body part.

In SQL\*Plus, you can define SQL object types interactively, using the following syntax:

    CREATE [OR REPLACE] TYPE type_name
      [AUTHID {CURRENT_USER | DEFINER}] {IS | AS} OBJECT (
      attribute_name data_type[, attribute_name data_type]...
      [{MAP | ORDER} MEMBER {function_spec | call_spec},]
      [{MEMBER | STATIC} {subprogram_spec | call_spec}
      [, {MEMBER | STATIC} {subprogram_spec | call_spec}]...]
    );

    [CREATE [OR REPLACE] TYPE BODY type_name {IS | AS}
      { {MAP | ORDER} MEMBER function_body;
       | {MEMBER | STATIC} {subprogram_body | call_spec};}
      [{MEMBER | STATIC} {subprogram_body | call_spec};]...
    END;]

The `AUTHID` clause determines whether all member methods of the type run with the privileges of their definer (`AUTHID` `DEFINER`), which is the default, or invoker (`AUTHID` `CURRENT_USER`). It also determines whether unqualified references to schema objects are resolved in the schema of the definer or invoker.

This section covers the following topics:

- About Attributes

- Declaring Methods

### 6.5.1 About Attributes

In an object type specification, all attributes must be declared before any methods are. In addition, you must declare at least one attribute. The maximum number of attributes that can be declared is 1000. Methods are optional.

As with a Java variable, you declare an attribute with a name and data type. The name must be unique within the object type, but can be reused in other object types. The data type can be any SQL type, except `LONG`, `LONG RAW`, `NCHAR`, `NVARCHAR2`, `NCLOB`, `ROWID`, and `UROWID`.

You cannot initialize an attribute in its declaration using the assignment operator or `DEFAULT` clause. Furthermore, you cannot impose the `NOT NULL` constraint on an attribute. However, objects can be stored in database tables on which you can impose constraints.

### 6.5.2 Declaring Methods

After declaring attributes, you can declare methods. `MEMBER` methods accept a built-in parameter known as `SELF`, which is an instance of the object type. Whether declared implicitly or explicitly, it is always the first parameter passed to a `MEMBER` method. In the method body, `SELF` denotes the object whose method was called. `MEMBER` methods are called on instances, as follows:

    instance_expression.method()

`STATIC` methods, which cannot accept or reference `SELF`, are invoked on the object type and not its instances, as follows:

    object_type_name.method()

If you want to call a Java method that is not `static`, then you must specify the keyword `MEMBER` in its call specification. Similarly, if you want to call a `static` Java method, then you must specify the keyword `STATIC` in its call specification.

This section contains the following topics:

- Map and Order Methods

- Constructor Methods

- Examples

#### 6.5.2.1 Map and Order Methods

The values of a SQL scalar data type, such as `CHAR`, have a predefined order and, therefore, can be compared with other values. However, instances of an object type have no predefined order. To put them in order, SQL calls a user-defined `map` method.

SQL uses the ordering to evaluate boolean expressions, such as `x > y`, and to make comparisons implied by the `DISTINCT`, `GROUP BY`, and `ORDER BY` clauses. A map method returns the relative position of an object in the ordering of all such objects. An object type can contain only one map method, which must be a function without any parameters and with one of the following return types: `DATE`, `NUMBER`, or `VARCHAR2`.

Alternatively, you can supply SQL with an `order` method, which compares two objects. An `order` method takes only two parameters: the built-in parameter, `SELF`, and another object of the same type. If `o1` and `o2` are objects, then a comparison, such as `o1 > o2`, calls the `order` method automatically. The method returns a negative number, zero, or a positive number signifying that `SELF` is less than, equal to, or greater than the other parameter, respectively. An object type can contain only one `order` method, which must be a function that returns a numeric result.

You can declare a `map` method or an `order` method, but not both. If you declare either of these methods, then you can compare objects in SQL and PL/SQL. However, if you do not declare both methods, then you can compare objects only in SQL and solely for equality or inequality.

**Note:**

Two objects of the same type are equal if the values of their corresponding attributes are equal.

#### 6.5.2.2 Constructor Methods

Every object type has a constructor, which is a system-defined function with the same name as the object type. The constructor initializes and returns an instance of that object type.

Oracle Database generates a default constructor for every object type. The formal parameters of the constructor match the attributes of the object type. That is, the parameters and attributes are declared in the same order and have the same names and data types. SQL never calls a constructor implicitly. As a result, you must call it explicitly. Constructor calls are allowed wherever function calls are allowed.

**Note:**

To invoke a Java constructor from SQL, you must wrap calls to it in a `static` method and declare the corresponding call specification as a `STATIC` member of the object type.

#### 6.5.2.3 Examples

In this section, each example builds on the previous one. To begin, you create two SQL object types to represent departments and employees. First, you write the specification for the object type `Department`. The body is not required, because the specification declares only attributes. The specification is as follows:

    CREATE TYPE Department AS OBJECT (
    deptno NUMBER(2),
    dname VARCHAR2(14),
    loc VARCHAR2(13)
    );

Then, you create the object type `Employee`. The `deptno` attribute stores a handle, called a `REF`, to objects of the type `Department`. A `REF` indicates the location of an object in an object table, which is a database table that stores instances of an object type. The `REF` does not point to a specific instance copy in memory. To declare a `REF`, you specify the data type `REF` and the object type that `REF` targets. The `Employee` type is created as follows:

    CREATE TYPE Employee AS OBJECT (
    empno NUMBER(4),
    ename VARCHAR2(10),
    job VARCHAR2(9),
    mgr NUMBER(4),
    hiredate DATE,
    sal NUMBER(7,2),
    comm NUMBER(7,2),
    deptno REF Department
    );

Next, you create the SQL object tables to hold objects of type `Department` and `Employee`. Create the `depts` object table, which will hold objects of the `Department` type. Populate the object table by selecting data from the `dept` relational table and passing it to a constructor, which is a system-defined function with the same name as the object type. Use the constructor to initialize and return an instance of that object type. The `depts` table is created as follows:

    CREATE TABLE depts OF Department AS
    SELECT Department(deptno, dname, loc) FROM dept;

Create the `emps` object table, which will hold objects of type `Employee`. The last column in the `emps` object table, which corresponds to the last attribute of the `Employee` object type, holds references to objects of type `Department`. To fetch the references into this column, use the operator `REF`, which takes a table alias associated with a row in an object table as its argument. The `emps` table is created as follows:

    CREATE TABLE emps OF Employee AS
    SELECT Employee(e.employee_id, e.first_name, e.job_id, e.manager_id, e.hire_date, e.salary, e.commission_pct,
    (SELECT REF(d) FROM departments d WHERE d.department_id = e.department_id))
    FROM employees e;

Selecting a `REF` returns a handle to an object. It does not materialize the object itself. To do that, you can use methods in the `oracle.sql.REF` class, which supports Oracle object references. This class, which is a subclass of `oracle.sql.Datum`, extends the standard JDBC interface, `oracle.jdbc2.Ref`.

##### Using Class oracle.sql.STRUCT

To continue, you write a Java stored procedure. The `Paymaster` class has one method, which computes an employee's wages. The `getAttributes()` method defined in the `oracle.sql.STRUCT` class uses the default JDBC mappings for the attribute types. For example, `NUMBER` maps to `BigDecimal`. The `Paymaster` class is created as follows:

    import java.sql.*;
    import java.io.*;
    import oracle.sql.*;
    import oracle.jdbc.*;
    import oracle.oracore.*;
    import oracle.jdbc2.*;
    import java.math.*;

    public class Paymaster
    {
      public static BigDecimal wages(STRUCT e) throws java.sql.SQLException
      {
        // Get the attributes of the Employee object.
        Object[] attribs = e.getAttributes();
        // Must use numeric indexes into the array of attributes.
        BigDecimal sal = (BigDecimal)(attribs[5]); // [5] = sal
        BigDecimal comm = (BigDecimal)(attribs[6]); // [6] = comm
        BigDecimal pay = sal;
        if (comm != null)
          pay = pay.add(comm);
        return pay;
      }
    }

Because the `wages()` method returns a value, you write a function call specification for it, as follows:

    CREATE OR REPLACE FUNCTION wages (e Employee) RETURN NUMBER AS
    LANGUAGE JAVA
    NAME 'Paymaster.wages(oracle.sql.STRUCT) return BigDecimal';

This is a top-level call specification, because it is not defined inside a package or object type.

##### Implementing the SQLData Interface

To make access to object attributes more natural, create a Java class that implements the `SQLData` interface. To do so, you must provide the `readSQL()` and `writeSQL()` methods as defined by the `SQLData` interface. The JDBC driver calls the `readSQL()` method to read a stream of database values and populate an instance of your Java class. In the following example, you revise `Paymaster` by adding a second method, `raiseSal()`:

    import java.sql.*;
    import java.io.*;
    import oracle.sql.*;
    import oracle.jdbc.*;
    import oracle.oracore.*;
    import oracle.jdbc2.*;
    import java.math.*;

    public class Paymaster implements SQLData
    {
      // Implement the attributes and operations for this type.
      private BigDecimal empno;
      private String ename;
      private String job;
      private BigDecimal mgr;
      private Date hiredate;
      private BigDecimal sal;
      private BigDecimal comm;
      private Ref dept;

      public static BigDecimal wages(Paymaster e)
      {
        BigDecimal pay = e.sal;
        if (e.comm != null)
          pay = pay.add(e.comm);
        return pay;
      }

      public static void raiseSal(Paymaster[] e, BigDecimal amount)
      {
        e[0].sal = // IN OUT passes [0]
        e[0].sal.add(amount); // increase salary by given amount
      }

      // Implement SQLData interface.

      private String sql_type;

      public String getSQLTypeName() throws SQLException
      {
        return sql_type;
      }

      public void readSQL(SQLInput stream, String typeName) throws SQLException
      {
        sql_type = typeName;
        empno = stream.readBigDecimal();
        ename = stream.readString();
        job = stream.readString();
        mgr = stream.readBigDecimal();
        hiredate = stream.readDate();
        sal = stream.readBigDecimal();
        comm = stream.readBigDecimal();
        dept = stream.readRef();
      }

      public void writeSQL(SQLOutput stream) throws SQLException
      {
        stream.writeBigDecimal(empno);
        stream.writeString(ename);
        stream.writeString(job);
        stream.writeBigDecimal(mgr);
        stream.writeDate(hiredate);
        stream.writeBigDecimal(sal);
        stream.writeBigDecimal(comm);
        stream.writeRef(dept);
      }
    }

You must revise the call specification for `wages()`, as follows, because its parameter has changed from `oracle.sql.STRUCT` to `Paymaster`:

    CREATE OR REPLACE FUNCTION wages (e Employee) RETURN NUMBER AS
    LANGUAGE JAVA
    NAME 'Paymaster.wages(Paymaster) return BigDecimal';

Because the new method, `raiseSal()`, is `void`, write a procedure call specification for it, as follows:

    CREATE OR REPLACE PROCEDURE raise_sal (e IN OUT Employee, r NUMBER)
    AS LANGUAGE JAVA
    NAME 'Paymaster.raiseSal(Paymaster[], java.math.BigDecimal)';

Again, this is a top-level call specification.

##### Implementing Object Type Methods

Assume you decide to drop the top-level call specifications `wages` and `raise_sal` and redeclare them as methods of the object type `Employee`. In an object type specification, all methods must be declared after the attributes. The body of the object type is not required, because the specification declares only attributes and call specifications. The `Employee` object type can be re-created as follows:

    CREATE TYPE Employee AS OBJECT (
    empno NUMBER(4),
    ename VARCHAR2(10),
    job VARCHAR2(9),
    mgr NUMBER(4),
    hiredate DATE,
    sal NUMBER(7,2),
    comm NUMBER(7,2),
    deptno REF Department
    MEMBER FUNCTION wages RETURN NUMBER
    AS LANGUAGE JAVA
    NAME 'Paymaster.wages() return java.math.BigDecimal',
    MEMBER PROCEDURE raise_sal (r NUMBER)
    AS LANGUAGE JAVA
    NAME 'Paymaster.raiseSal(java.math.BigDecimal)'
    );

Then, you revise `Paymaster` accordingly. You need not pass an array to `raiseSal()`, because the SQL parameter `SELF` corresponds directly to the Java parameter `this`, even when `SELF` is declared as `IN OUT`, which is the default for procedures.

    import java.sql.*;
    import java.io.*;
    import oracle.sql.*;
    import oracle.jdbc.*;
    import oracle.oracore.*;
    import oracle.jdbc2.*;
    import java.math.*;

    public class Paymaster implements SQLData
    {
      // Implement the attributes and operations for this type.
      private BigDecimal empno;
      private String ename;
      private String job;
      private BigDecimal mgr;
      private Date hiredate;
      private BigDecimal sal;
      private BigDecimal comm;
      private Ref dept;

      public BigDecimal wages()
      {
        BigDecimal pay = sal;
        if (comm != null)
          pay = pay.add(comm);
        return pay;
      }

      public void raiseSal(BigDecimal amount)
      {
        // For SELF/this, even when IN OUT, no array is needed.
        sal = sal.add(amount);
      }

      // Implement SQLData interface.

      String sql_type;

      public String getSQLTypeName() throws SQLException
      {
        return sql_type;
      }

      public void readSQL(SQLInput stream, String typeName) throws SQLException
      {
        sql_type = typeName;
        empno = stream.readBigDecimal();
        ename = stream.readString();
        job = stream.readString();
        mgr = stream.readBigDecimal();
        hiredate = stream.readDate();
        sal = stream.readBigDecimal();
        comm = stream.readBigDecimal();
        dept = stream.readRef();
      }

      public void writeSQL(SQLOutput stream) throws SQLException
      {
        stream.writeBigDecimal(empno);
        stream.writeString(ename);
        stream.writeString(job);
        stream.writeBigDecimal(mgr);
        stream.writeDate(hiredate);
        stream.writeBigDecimal(sal);
        stream.writeBigDecimal(comm);
        stream.writeRef(dept);
      }
    }
