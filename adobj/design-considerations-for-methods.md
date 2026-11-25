There are special considerations to think about when working with methods.

Topics:

- Choice of Language for Method Functions

- Static Methods

- About Using SELF IN OUT NOCOPY with Member Procedures

- Function-Based Indexes on the Return Values of Type Methods

### 9.5.1 Choice of Language for Method Functions

Method functions can be implemented in any of the languages supported by Oracle, such as PL/SQL, Java, or C.

Consider the following factors when you choose the language for a particular application:

- Ease of use

- SQL calls

- Speed of execution

- Same/different address space

In general, if the application performs intense computations, C is preferable, but if the application performs a relatively large number of database calls, PL/SQL or Java is preferable.

A method implemented in C executes in a separate process from the server using external procedures. In contrast, a method implemented in Java or PL/SQL executes in the same process as the server.

#### Example: Implementing a Method

The example described in this section involves an object type whose methods are implemented in different languages. In the example, the object type `ImageType` has an `ID` attribute, which is a `NUMBER` that uniquely identifies it, and an `IMG` attribute, which is a `BLOB` that stores the raw image. The object type `ImageType` has the following methods:

- The method `get_name` fetches the name of the image by looking it up in the database. This method is implemented in PL/SQL.

- The method `rotate` rotates the image. This method is implemented in C.

- The method `clear` returns a new image of the specified color. This method is implemented in Java.

For implementing a method in C, a `LIBRARY` object must be defined to point to the library that contains the external C routines. For implementing a method implemented in Java, this example assumes that the Java class with the method has been compiled and uploaded into Oracle.

The object type specification and its methods are shown in Example 9-12.

**Note:**

Type methods can be mapped only to static Java methods.

**See Also:**

- [Oracle Database Java Developer's Guide ](../jjdev/Java-introduction.md)for more information

- [Object Support in Oracle Programming Environments](object-support-in-oracle-programming-environments.md) for more information about choosing a language

Example 9-12 Creating an Object Type with Methods Implemented in Different Languages

    CREATE LIBRARY myCfuncs TRUSTED AS STATIC
    /

    CREATE TYPE ImageType AS OBJECT (
       id   NUMBER,
       img  BLOB,
       MEMBER FUNCTION get_name return VARCHAR2,
       MEMBER FUNCTION rotate return BLOB,
       STATIC FUNCTION clear(color NUMBER) return BLOB);/

    CREATE TYPE BODY ImageType AS
       MEMBER FUNCTION get_name RETURN VARCHAR2
       IS
        imgname  VARCHAR2(100);
        sqlstmt VARCHAR2(200);
       BEGIN
          sqlstmt := 'SELECT name INTO imgname FROM imgtab WHERE imgid = id';
          EXECUTE IMMEDIATE sqlstmt;
          RETURN imgname;
       END;

       MEMBER FUNCTION rotate RETURN BLOB
       AS LANGUAGE C
       NAME "Crotate"
       LIBRARY myCfuncs;

       STATIC FUNCTION clear(color NUMBER) RETURN BLOB
       AS LANGUAGE JAVA
       NAME 'myJavaClass.clear(oracle.sql.NUMBER) return oracle.sql.BLOB';

    END;
    /

### 9.5.2 Static Methods

Static methods differ from member methods in that the `SELF` value is not passed in as the first parameter. Methods in which the value of `SELF` is not relevant should be implemented as static methods. Static methods can be used for user-defined constructors.

Example 9-13 shows a constructor-like method that constructs an instance of the type based on the explicit input parameters and inserts the instance into the specified table:.

Example 9-13 Creating an Object Type with a STATIC Method

    CREATE TYPE atype AS OBJECT(
       a1 NUMBER,
       STATIC PROCEDURE newa (
          p1        NUMBER,
          tabname   VARCHAR2,
          schname   VARCHAR2));
    /
    CREATE TYPE BODY atype AS
        STATIC PROCEDURE newa (p1 NUMBER, tabname VARCHAR2, schname VARCHAR2)
          IS
          sqlstmt VARCHAR2(100);
        BEGIN
          sqlstmt := 'INSERT INTO '||schname||'.'||tabname|| ' VALUES (atype(:1))';
          EXECUTE IMMEDIATE sqlstmt USING p1;
        END;
    END;
    /

    CREATE TABLE atab OF atype;

    BEGIN
       atype.newa(1, 'atab', 'HR');
    END;
    /

### 9.5.3 About Using SELF IN OUT NOCOPY with Member Procedures

In member procedures, if `SELF` is not declared, its parameter mode defaults to `IN` `OUT`. However, the default behavior does not include the `NOCOPY` compiler hint. See "[Member Methods](object-methods.md)".

Because the value of the `IN` `OUT` actual parameter is copied into the corresponding formal parameter, the copying slows down execution when the parameters hold large data structures such as instances of large object types.

For performance reasons, you may want to include `SELF` `IN` `OUT` `NOCOPY` when passing a large object type as a parameter. For example:

`MEMBER PROCEDURE my_proc (SELF IN OUT NOCOPY my_LOB)`

**See Also:**

- [Oracle Database PL/SQL Language Reference](../lnpls/plsql-language-elements.md) for information on performance issues and restrictions on the use of `NOCOPY`

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-PROCEDURE.md) for information about using `NOCOPY` in the `CREATE` `PROCEDURE` statement

### 9.5.4 Function-Based Indexes on the Return Values of Type Methods

A function-based index is an index based on the return values of an expression or function. The function may be a method function of an object type.

A function-based index built on a method function precomputes the return value of the function for each object instance in the column or table being indexed and stores those values in the index. There they can be referenced without having to evaluate the function again.

Function-based indexes are useful for improving the performance of queries that have a function in the `WHERE` clause. For example, the following code contains a query of an object table `emps`:

    CREATE TYPE emp_t AS OBJECT(
      name   VARCHAR2(36),
      salary NUMBER,
      MEMBER FUNCTION bonus RETURN NUMBER DETERMINISTIC);
    /
    CREATE TYPE BODY emp_t IS
     MEMBER FUNCTION bonus RETURN NUMBER DETERMINISTIC IS
     BEGIN
      RETURN self.salary * .1;
     END;
    END;
    /

    CREATE TABLE emps OF emp_t ;

    SELECT e.name
      FROM emps e
      WHERE e.bonus() > 2000;

To evaluate this query, Oracle must evaluate `bonus()` for each row object in the table. If there is a function-based index on the return values of `bonus()`, then this work has already been done, and Oracle can simply look up the results in the index. This enables Oracle to return a result from the query more quickly.

Return values of a function can be usefully indexed only if those values are constant, that is, only if the function always returns the same value for each object instance. For this reason, to use a user-written function in a function-based index, the function must have been declared with the `DETERMINISTIC` keyword, as in the preceding example. This keyword promises that the function always returns the same value for each object instance's set of input argument values.

The following example creates a function-based index on the method `bonus()` in the table `emps`:

Example 9-14 Creating a Function-Based Index on a Method

    CREATE INDEX emps_bonus_idx ON emps x (x.bonus()) ;
