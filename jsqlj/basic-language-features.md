SQLJ statements always begin with a `#sql` token and can be broken into two main categories:

- Declarations: Used for creating Java classes for iterators, which is similar to Java Database Connectivity (JDBC) result sets, or connection contexts, which is designed to help you create strongly typed connections according to the sets of SQL entities being used.

- Executable statements: Used to execute embedded SQL operations.

This chapter discusses the following topics:

- Overview of SQLJ Declarations

- Overview of SQLJ Executable Statements

- Java Host\_ Context\_ and Result Expressions

- Single-Row Query Results: SELECT INTO Statements

- Multirow Query Results: SQLJ Iterators

- Assignment Statements (SET)

- Stored Procedure and Function Calls

### 5.1 Overview of SQLJ Declarations

A SQLJ declaration consists of the `#sql` token followed by the declaration of a class. SQLJ declarations introduce specialized Java types into your application. There are currently two kinds of SQLJ declarations, iterator declarations and connection context declarations, defining Java classes as follows:

- Iterator declarations define iterator classes. Iterators are conceptually similar to JDBC result sets and are used to receive multi-row query data. An iterator is implemented as an instance of an iterator class.

- Connection context declarations define connection context classes. Each connection context class is typically used for connections whose operations use a particular set of SQL entities, such as tables, views, and stored procedures. That is to say, instances of a particular connection context class are used to connect to schemas that include SQL entities with the same names and characteristics. SQLJ implements each database connection as an instance of a connection context class.

  SQLJ includes the predefined `sqlj.runtime.DefaultContext` connection context class. If you only require one connection context class, then you can use `DefaultContext`, which does not require a connection context declaration.

In any iterator or connection context declaration, you may optionally include the following clauses:

- The `implements` clause: Specifies one or more interfaces that the generated class will implement.

- The `with` clause: Specifies one or more initialized constants to be included in the generated class.

This section covers the following topics:

- Rules for SQLJ Declarations

- Iterator Declarations

- Connection Context Declarations

- Declaration IMPLEMENTS Clause

- Declaration WITH Clause

#### 5.1.1 Rules for SQLJ Declarations

SQLJ declarations are allowed in your SQLJ source code anywhere that a class definition would be allowed in standard Java. For example:

    SQLJ declaration;   // OK (top level scope)

    class Outer
    {
       SQLJ declaration; // OK (class level scope)

       class Inner
       {
          SQLJ declaration; // OK (nested class scope)
       }

       void func()
       {
          SQLJ declaration; // OK (method block)
       }
    }

**Note:**

As with standard Java, any public class should be declared in one of the following ways:

- Declare it in a separate source file. The base name of the file should be the same as the class name.

- Declare it at class-level scope or nested-class-level scope. In this case, it may be advisable to use `public static` modifiers.

This is a requirement if you are using the standard `javac` compiler provided with the Sun Microsystems JDK.

#### 5.1.2 Iterator Declarations

An iterator declaration creates a class that defines a kind of iterator for receiving query data. The declaration will specify the column types of the iterator instances, which must match the column types being selected from the database table.

Basic iterator declarations use the following syntax:

    #sql <modifiers> iterator iterator_classname (type declarations);

Modifiers are optional and can be any standard Java class modifiers, such as `public`, `static`, and so on. Type declarations are separated by commas.

There are two categories of iterators, named iterators and positional iterators. For named iterators, you must specify column names and types. For positional iterators, you need to specify only types.

The following is an example of a named iterator declaration:

    #sql public iterator EmpIter (String ename, double sal);

This statement results in the SQLJ translator creating a public `EmpIter` class with a `String` attribute `ename` and a `double` attribute `sal`. You can use this iterator to select data from a database table with corresponding employee name and salary columns of matching names (`ENAME` and `SAL`) and data types (`CHAR` and `NUMBER`).

Declaring `EmpIter` as a positional iterator, instead of a named iterator, can be done as follows:

    #sql public iterator EmpIter (String, double);

**See Also:**

"Multirow Query Results: SQLJ Iterators"

#### 5.1.3 Connection Context Declarations

A connection context declaration creates a connection context class, whose instances are typically used for database connections that use a particular set of SQL entities. Basic connection context declarations use the following syntax:

    #sql <modifiers> context context_classname;

As for iterator declarations, modifiers are optional and can be any standard Java class modifiers. For example:

    #sql public context MyContext;

As a result of this statement, the SQLJ translator creates a public `MyContext` class. In your SQLJ code you can use instances of this class to create database connections to schemas that include a desired set of entities, such as tables, views, and stored procedures. Different instances of `MyContext` might be used to connect to different schemas, but each schema might be expected, for example, to include an `EMPLOYEES` table, a `DEPARTMENTS` table, and a `SECURE_EMPLOYEES` stored procedure.

Declared connection context classes are an advanced topic and are not necessary for basic SQLJ applications that use only one interrelated set of SQL entities. In basic scenarios, you can use multiple connections by creating multiple instances of the `sqlj.runtime.ref.DefaultContext` class, which does not require any connection context declarations.

**See Also:**

"[Connection Considerations](key-programming-considerations.md)" and "[Connection Contexts](advanced-language-features.md)"

#### 5.1.4 Declaration IMPLEMENTS Clause

When you declare any iterator class or connection context class, you can specify one or more interfaces to be implemented by the generated class.

Use the following syntax for an iterator class:

    #sql <modifiers> iterator iterator_classname implements intfc1,..., intfcN
         (type declarations);

The portion `implements` `intfc1,..., intfcN` is known as the `implements` clause. Note that in an iterator declaration, the `implements` clause precedes the iterator type declarations.

Here is the syntax for a connection context declaration:

    #sql <modifiers> context context_classname implements intfc1,..., intfcN;

The `implements` clause is potentially useful in either an iterator declaration or a connection context declaration, but is more likely to be useful in iterator declarations, particularly in implementing the `sqlj.runtime.Scrollable` or `sqlj.runtime.ForUpdate` interface. Scrollable iterators are supported in the Oracle SQLJ implementation.

**Note:**

The SQLJ `implements` clause corresponds to the Java `implements` clause.

The following example uses an `implements` clause in declaring a named iterator class. Presume you have created a package, `mypackage`, that includes an iterator interface, `MyIterIntfc`.

    #sql public iterator MyIter implements mypackage.MyIterIntfc
         (String ename, int empno);

The declared class `MyIter` will implement the `mypackage.MyIterIntfc` interface.

The following example declares a connection context class that implements an interface named `MyConnCtxtIntfc`. Presume that it is in the package `mypackage`.

    #sql public context MyContext implements mypackage.MyConnCtxtIntfc;

**See Also:**

"[Using the IMPLEMENTS Clause in Iterator Declarations](advanced-language-features.md)" and "[Using the IMPLEMENTS Clause in Connection Context Declarations](advanced-language-features.md)"

#### 5.1.5 Declaration WITH Clause

In declaring a connection context class or iterator class, you can use a `with` clause to specify and initialize one or more constants to be included in the definition of the generated class. Most of this usage is standard, although Oracle implementation adds some extended functionality for iterator declarations.

This section covers the following topics:

- Standard WITH Clause Usage

- Oracle-Specific WITH Clause Usage

- Example: Returnability

##### 5.1.5.1 Standard WITH Clause Usage

In using a `with` clause, the constants that are produced are always `public static final`. Use the following syntax for an iterator class:

    #sql <modifiers> iterator iterator_classname with (var1=value1,..., varN=valueN)
         (type declarations);

The portion `with` `(``var1=value1,..., varN=valueN`) is the `with` clause. Note that in an iterator declaration, the `with` clause precedes the iterator type declarations.

Where there is both a `with` clause and an `implements` clause, the `implements` clause must come first. Note that parentheses are used to enclose `with` lists, but not `implements` lists.

Here is the syntax for a connection context declaration that uses a `with` clause:

    #sql <modifiers> context context_classname with (var1=value1,..., varN=valueN);

**Note:**

A predefined set of standard SQLJ constants can be defined in a `with` clause. However, not all of these constants are meaningful to Oracle Database 12c Release 2 (12.2) or to Oracle SQLJ run time.

Attempts to define constants other than the standard constants is legal with Oracle Database 12c Release 2 (12.2), but might not be portable to other SQLJ implementations and will generate a warning if you have the `-warn=portable` flag enabled.

##### Supported WITH Clause Constants

The Oracle SQLJ implementation supports the following standard constants in connection context declarations:

- `typeMap`: a `String` literal defining the name of a type map properties resource

  Oracle also supports the use of `typeMap` in iterator declarations.

- `dataSource`: a `String` literal defining the name under which a data source is looked up in the `InitialContext`

The Oracle SQLJ implementation supports the following standard constants in iterator declarations:

- `sensitivity`: `SENSITIVE`/`ASENSITIVE`/`INSENSITIVE`, to define the sensitivity of a scrollable iterator

- `returnability`: `true`/`false`, to define whether an iterator can be returned from a Java stored procedure or function

##### Unsupported WITH Clause Constants

If you have SQLJ code that uses these constants, then they will not cause an error but will result in no operation. The Oracle SQLJ implementation does not support the following standard constants in connection context declarations:

- `path`: a `String` literal defining the name of a path to be prepended for resolution of Java stored procedures and functions

- `transformGroup`: a `String` literal defining the name of a SQL transformation group that can be applied to SQL types

The Oracle SQLJ implementation does not support the following standard constants, involving cursor states, in iterator declarations:

- `holdability`: `true`/`false`, determining cursor holdability

  The concept of holdability is defined in the SQL specification. A cursor that is holdable can, subject to application request, be kept open and positioned on the current row even when a transaction is completed. Use of the cursor can then be continued in the next transaction of the same SQL session, however, subject to some limitations.

- `updateColumns`: a `String` literal containing a comma-delimited list of column names

  An iterator declaration having a `with` clause that specifies `updateColumns` must also have an `implements` clause that specifies the `sqlj.runtime.ForUpdate` interface. The Oracle SQLJ implementation enforces this, even though `updateColumns` is currently unsupported.

The following is a sample connection context declaration using `typeMap`:

    #sql public context MyContext with (typeMap="MyPack.MyClass");

The declared class `MyContext` will define a `String` attribute `typeMap` that will be `public static final` and initialized to the value `MyPack.MyClass`. This value is the fully qualified class name of a `ListResourceBundle` implementation that provides the mapping between SQL and Java types for statements executed on instances of the `MyContext` class.

The following is a sample iterator declaration using `sensitivity`:

    #sql public iterator MyAsensitiveIter with (sensitivity=ASENSITIVE)
         (String ename, int empno);

This declaration sets the cursor sensitivity to `ASENSITIVE` for the `MyAsensitiveIter` named iterator class.

The following example uses both an `implements` clause and a `with` clause:

    #sql public iterator MyScrollableIterator implements sqlj.runtime.Scrollable
         with (holdability=true) (String ename, int empno);

This declaration implements the interface `sqlj.runtime.Scrollable` and enables the cursor `holdability` for a named iterator class.

**Note:**

`holdability` is currently not supported.

##### 5.1.5.2 Oracle-Specific WITH Clause Usage

In addition to the standard `with` clause usage in a connection context declaration to associate a type map with the connection context class, the Oracle SQLJ implementation enables you to use a `with` clause to associate a type map with the iterator class in an iterator declaration. For example:

    #sql iterator MyIterator with (typeMap="MyTypeMap") (Person pers, Address addr);

If you use Oracle-specific code generation and use type maps in your application, then your iterator and connection context declarations must use the same type maps.

**See Also:**

"[Code Considerations and Limitations with Oracle-Specific Code Generation](key-programming-considerations.md)"

##### 5.1.5.3 Example: Returnability

Use `returnability=true` in the `with` clause of a SQLJ iterator declaration to specify that the iterator can be returned from a Java stored procedure to a SQL or PL/SQL statement as a REF CURSOR. With the default `returnability=false` setting, the iterator cannot be returned in this manner, and an attempt to do so will result in a SQL exception at run time.

Create the following database table:

    create table sqljRetTab(str varchar2(30));
    insert into sqljRetTab values ('sqljRetTabCol');

Define the `RefCursorSQLJ` class in the `RefCursorSQLJ.sqlj` source file as follows. Note that the iterator type `MyIter` uses `returnability=true`.

    public class RefCursorSQLJ
    {
       #sql static public iterator MyIter with (returnability=true) (String str);

       static public MyIter sqljUserRet() throws java.sql.SQLException
       {
            MyIter iter=null;
            try {
            #sql iter = {select str from sqljRetTab};
            } catch (java.sql.SQLException e)
            {
               e.printStackTrace();
               throw e;
            }
            System.err.println("iter is " + iter);
            return iter;
       }
    }

Load `RefCursorSQLJ.sqlj` into Oracle Java Virtual Machine (JVM) inside the database as follows:

    % loadjava -u HR -r -f -v RefCursorSQLJ.sqlj
    Password: password

Invoke the Java stored procedure defined for the `sqljUserRet()` method:

    create or replace package refcur_pkg as
         type refcur_t is ref cursor;
    end;
    /
    create or replace function sqljUserRet
    return refcur_pkg.refcur_t as
    language java
    name 'RefCursorSQLJ.sqljUserRet() return
    RefCursorSQLJ.MyIter';
    /
    select HR.sqljUserRet from dual;

Here is the result of the `SELECT` statement:

        SQLJRET1
        --------------------
        CURSOR STATEMENT : 1

        STR
        ------------------------------
        sqljRetTabCol

### 5.2 Overview of SQLJ Executable Statements

A SQLJ executable statement consists of the `#sql` token followed by a SQLJ clause, which uses syntax that follows a specified standard for embedding executable SQL statements in Java code. The embedded SQL operation of a SQLJ executable statement can be any SQL operation supported by the JDBC driver.

This section covers the following topics:

- Rules for SQLJ Executable Statements

- SQLJ Clauses

- Specifying Connection Context Instances and Execution Context Instances

- Executable Statement Examples

- PL/SQL Blocks in Executable Statements

#### 5.2.1 Rules for SQLJ Executable Statements

A SQLJ executable statement must adhere to the following rules:

- It is permitted in Java code wherever Java block statements are permitted. That is, it is permitted inside method definitions and static initialization blocks.

- Its embedded SQL operation must be enclosed in curly braces: `{...}`.

- It must be terminated with a semi-colon (;).

**Note:**

- It is recommended that you do not close the SQL operation with a semi-colon. The parser will detect the end of the operation when it encounters the closing curly brace of the SQLJ clause.

- Everything inside the curly braces of a SQLJ executable statement is treated as SQL syntax and must follow SQL rules, with the exception of Java host expressions.

- During offline parsing of SQL operations, all SQL syntax is checked. However, during online semantics-checking only data manipulation language (DML) operations can be parsed and checked. Data definition language (DDL) operations, transaction-control operations, or any other kinds of SQL operations cannot be parsed and checked.

#### 5.2.2 SQLJ Clauses

A SQLJ clause is the executable part of a statement, consisting of everything to the right of the `#sql` token. This consists of embedded SQL inside curly braces, preceded by a Java result expression if appropriate, such as `result` in the following example:

    #sql { SQL operation };   // For a statement with no output, like INSERT
    ...
    #sql result = { SQL operation };   // For a statement with output, like SELECT

A clause without a result expression, such as in the first SQLJ statement in the example, is known as a statement clause. A clause that does have a result expression, such as in the second SQLJ statement in the example, is known as an assignment clause.

A result expression can be anything from a simple variable that takes a stored-function return value to an iterator that takes several columns of data from a multi-row `SELECT`, where the iterator can be an instance of an iterator class or subclass.

A SQL operation in a SQLJ statement can use standard SQL syntax only or can use a clause with syntax specific to SQLJ.

Table 1 lists supported SQLJ statement clauses and Table 2 lists supported SQLJ assignment clauses. The last two entries in Table 5-1 are general categories for statement clauses that use standard SQL syntax or Oracle PL/SQL syntax, as opposed to SQLJ-specific syntax.

Table 5-1 SQLJ Statement Clauses

| Category                                          | Functionality                                                                                  | More Information                                                                                                                |
|:--------------------------------------------------|:-----------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------|
| `SELECT INTO` clause                              | Select data into Java host expressions.                                                        | "Single-Row Query Results: SELECT INTO Statements"                                                                              |
| `FETCH` clause                                    | Fetch data from a positional iterator.                                                         | "Using Positional Iterators"                                                                                                    |
| `COMMIT` clause                                   | Commit changes to the data.                                                                    | "[Using Manual COMMIT and ROLLBACK](key-programming-considerations.md)"                                                         |
| `ROLLBACK` clause                                 | Cancel changes to the data.                                                                    | "[Using Manual COMMIT and ROLLBACK](key-programming-considerations.md)"                                                         |
| `SAVEPOINT RELEASE SAVEPOINT ROLLBACK TO` clauses | Set a savepoint for future rollbacks, release a specified savepoint, roll back to a savepoint. | "[Using Savepoints](key-programming-considerations.md)"                                                                         |
| `SET TRANSACTION` clause                          | Use advanced transaction control for access mode and isolation level.                          | "[Advanced Transaction Control](advanced-language-features.md)"                                                                 |
| Procedure clause                                  | Call a stored procedure.                                                                       | "Calling Stored Procedures"                                                                                                     |
| Assignment clause                                 | Assign values to Java host expressions.                                                        | "Assignment Statements (SET)"                                                                                                   |
| SQL clause                                        | Use standard SQL syntax and functionality: `UPDATE`, `INSERT`, `DELETE`.                       | Oracle Database SQL Language Reference                                                                                          |
| PL/SQL block                                      | Use `BEGIN..END` or `DECLARE..BEGIN..END` anonymous block inside SQLJ statement.               | "PL/SQL Blocks in Executable Statements"<br>[Oracle Database PL/SQL Language Reference](../sqlrf/Introduction-to-Oracle-SQL.md) |

Table 5-2 SQLJ Assignment Clauses

| Category                   | Functionality                                 | More Information                                                                                |
|:---------------------------|:----------------------------------------------|:------------------------------------------------------------------------------------------------|
| Query clause               | Select data into a SQLJ iterator.             | "Multirow Query Results: SQLJ Iterators"                                                        |
| Function clause            | Call a stored function.                       | "Calling Stored Functions"                                                                      |
| Iterator conversion clause | Convert a JDBC result set to a SQLJ iterator. | "[Converting from Result Sets to Named or Positional Iterators](advanced-language-features.md)" |

**Note:**

A SQLJ statement is referred to by the same name as the clause that makes up the body of that statement. For example, an executable statement consisting of `#sql` followed by a `SELECT INTO` clause is referred to as a `SELECT INTO` statement.

#### 5.2.3 Specifying Connection Context Instances and Execution Context Instances

If you have defined multiple database connections and want to specify a particular connection context instance for an executable statement, then use the following syntax:

    #sql [conn_context_instance] { SQL operation };

If you have defined one or more execution context instances of the `sqlj.runtime.ExecutionContext` class and want to specify one of them for use with an executable statement, then use the following syntax:

    #sql [exec_context_instance] { SQL operation };

You can use an execution context instance to provide status or control of the SQL operation of a SQLJ executable statement. For example, you can use execution context instances in multithreading situations where multiple operations are occurring on the same connection.

You can also specify both a connection context instance and an execution context instance:

    #sql [conn_context_instance, exec_context_instance] { SQL operation };

**Note:**

- Include the square brackets around connection context instances and execution context instances. They are part of the syntax.

- If you specify both a connection context instance and an execution context instance, then the connection context instance must come first.

#### 5.2.4 Executable Statement Examples

This section provides examples of elementary SQLJ executable statements.

##### Elementary INSERT

The following example demonstrates a basic `INSERT`. The statement clause does not require any syntax specific to SQLJ.

Consider an employee table `EMP` with the following rows:

    CREATE TABLE EMP (
       ENAME VARCHAR2(10),
       SAL NUMBER(7,2) );

Use the following SQLJ executable statement, which uses only standard SQL syntax, to insert Joe as a new employee into the `EMP` table, specifying his name and salary:

    #sql { INSERT INTO emp (ename, sal) VALUES ('Joe', 43000) };

##### Elementary INSERT with Connection Context or Execution Context Instances

The following examples use `ctx` as a connection context instance, which is an instance of either the default `sqlj.runtime.ref.DefaultContext` or a class that you have previously declared in a connection context declaration, and `execctx` as an execution context instance:

    #sql [ctx] { INSERT INTO emp (ename, sal) VALUES ('Joe', 43000) };

    #sql [execctx] { INSERT INTO emp (ename, sal) VALUES ('Joe', 43000) };

    #sql [ctx, execctx] { INSERT INTO emp (ename, sal) VALUES ('Joe', 43000) };

##### A Simple SQLJ Method

This example demonstrates a simple method using SQLJ code, demonstrating how SQLJ statements interrelate with and are interspersed with Java statements. The SQLJ statement uses standard `INSERT INTO ``table`` VALUES` syntax supported by the Oracle SQL implementation. The statement also uses Java host expressions, marked by colons (:), to define the values. Host expressions are used to pass data between the Java code and SQL instructions.

    public static void writeSalesData (int[] itemNums, String[] itemNames)
           throws SQLException
    {
      for (int i =0; i < itemNums.length; i++)
        #sql { INSERT INTO sales VALUES(:(itemNums[i]), :(itemNames[i]), SYSDATE) };
    }

**Note:**

- The `throws SQLException` is required.

- SQLJ function calls also use a `VALUES` token, but these situations are not related semantically.

#### 5.2.5 PL/SQL Blocks in Executable Statements

PL/SQL blocks can be used within the curly braces of a SQLJ executable statement just as SQL operations can, as in the following example:

    #sql {
       DECLARE
          n NUMBER;
       BEGIN
          n := 1;
          WHILE n <= 100 LOOP
             INSERT INTO emp (empno) VALUES(2000 + n);
             n := n + 1;
          END LOOP;
       END
    };

This example goes through a loop that inserts new employees in the `emp` table, creating employee numbers `2001` through `2100`. It presumes data other than the employee number will be filled in later.

Simple PL/SQL blocks can also be coded in a single line as follows:

    #sql { <DECLARE ...> BEGIN ... END; };

Using PL/SQL anonymous blocks within SQLJ statements is one way to use dynamic SQL in your application. You can also use dynamic SQL directly through SQLJ extensions provided by Oracle or through JDBC code within a SQLJ application.

**See Also:**

"[Support for Dynamic SQL](advanced-language-features.md)" and "[SQLJ and JDBC Interoperability](advanced-language-features.md)"

**Note:**

Remember that using PL/SQL in your SQLJ code would prevent portability to other platforms, because PL/SQL is Oracle-specific.

### 5.3 Java Host, Context, and Result Expressions

This section discusses three categories of Java expressions used in SQLJ code: host expressions, context expressions, and result expressions. Host expressions are the most frequently used Java expressions. Another category of expressions, called meta bind expressions, are used specifically for dynamic SQL operations and use syntax similar to that of host expressions.

**See Also:**

"[Support for Dynamic SQL](advanced-language-features.md)"

SQLJ uses Java host expressions to pass arguments between Java code and SQL operations. This is how you pass information between Java and SQL. Host expressions are interspersed within the embedded SQL operations in the SQLJ source code.

The most basic kind of host expression, consisting of only a Java identifier, is referred to as a host variable. A context expression specifies a connection context instance or execution context instance to be used for a SQLJ statement. A result expression specifies an output variable for query results or a function return.

This section covers the following topics:

- Overview of Host Expressions

- Basic Host Expression Syntax

- Examples of Host Expressions

- Overview of Result Expressions and Context Expressions

- Evaluation of Java Expressions at Run Time

- Examples of Evaluation of Java Expressions at Run Time (ISO Code Generation)

- Restrictions on Host Expressions

#### 5.3.1 Overview of Host Expressions

Any valid Java expression can be used as a host expression. In the simplest case, the expression consists of just a single Java variable. Other kinds of host expressions include the following:

- Arithmetic expressions

- Java method calls with return values

- Java class field values

- Array elements

- Conditional expressions (`a ? b : c`)

- Logical expressions

- Bitwise expressions

Java identifiers used as host variables or in host expressions can represent any of the following:

- Local variables

- Declared parameters

- Class fields

- Static or instance method calls

Local variables used in host expressions can be declared anywhere that other Java variables can be declared. Fields can be inherited from a superclass.

Java variables that are legal in the Java scope where the SQLJ executable statement appears can be used in a host expression in a SQL statement, presuming its type is convertible to or from a SQL data type. Host expressions can be input, output, or input-output.

**See Also:**

"[Supported Types for Host Expressions](type-support.md)"

#### 5.3.2 Basic Host Expression Syntax

A host expression is preceded by a colon (:). If the desired mode of the host expression is not the default, then the colon must be followed by `IN`, `OUT`, or `INOUT`, as appropriate, before the host expression itself. These are referred to as mode specifiers. The default is `OUT` if the host expression is part of an `INTO`-list or is the assignment expression in a `SET` statement. Otherwise, the default is `IN`. Any `OUT` or `INOUT` host expression must be assignable.

**Note:**

When using the default, you can still include the mode specifier if desired.

The SQL code that surrounds a host expression can use any vendor-specific SQL syntax. Therefore, no assumptions can be made about the syntax when parsing the SQL operations and determining the host expressions. To avoid any possible ambiguity, any host expression that is not a simple host variable (in other words, that is more complex than a nondotted Java identifier) must be enclosed in parentheses.

To summarize the basic syntax:

- For a simple host variable without a mode specifier, put the host variable after the colon, as in the following example:

      :hostvar

- For a simple host variable with a mode specifier, put the mode specifier after the colon and put white space (space, tab, newline, or comment) between the mode specifier and the host variable, as in the following example:

      :INOUT hostvar

  The white space is required to distinguish between the mode specifier and the variable name.

- For any other host expression, enclose the expression in parentheses and place it after the mode specifier or after the colon, if there is no mode specifier, as in the following examples:

      :IN(hostvar1+hostvar2)
      :(hostvar3*hostvar4)
      :(index--)

  White space is not required after the mode specifier in this example, because the parenthesis is a suitable separator. However, a white space after the mode specifier is allowed.

  An outer set of parentheses is needed even if the expression already starts with a begin-parenthesis, as in the following examples:

      :((x+y).z)
      :(((y)x).myOutput())

##### Syntax Notes

Keep the following in mind regarding the host expression syntax:

- White space is always allowed after the colon as well as after the mode specifier. Wherever white space is allowed, you can also have a comment.

  You can have any of the following in the SQL namespace:

  - SQL comments after the colon and before the mode specifier

  - SQL comments after the colon and before the host expression if there is no mode specifier

  - SQL comments after the mode specifier and before the host expression

  You can have the following in the Java namespace:

  - Java comments within the host expression (inside the parentheses)

- The `IN`, `OUT`, and `INOUT` syntax used for host variables and expressions are not case-sensitive. These tokens can be in uppercase, lowercase, or mixed.

- Do not confuse the `IN`, `OUT`, and `INOUT` syntax of SQLJ host expressions with similar `IN`, `OUT`, and `IN OUT` syntax used in PL/SQL declarations to specify the mode of parameters passed to PL/SQL stored functions and procedures.

##### Usage Notes

Keep the following in mind regarding the usage of host expressions:

- A simple host variable can appear multiple times in the same SQLJ statement, as follows:

  - If the host variable appears only as an input variable, then there are no restrictions or complications.

  - If at least one appearance of the host variable is as an output variable in a PL/SQL block, then you will receive a portability warning if the translator `-warn=portability` flag is set. SQLJ run-time behavior in this situation is vendor-specific. Oracle SQLJ run time uses value semantics, as opposed to reference semantics, for all occurrences of the host variable.

  - If at least one appearance of the host variable is as an output variable in a stored procedure call, stored function call, `SET` statement, or `INTO`-list, then you will not receive any warning. SQLJ run-time behavior in this situation is standardized, using value semantics.

  **Note:**

  The term output refers to `OUT` or `INOUT` variables, as applicable.

- If a host expression that is a simple host variable appears multiple times in a SQLJ statement, then by default each appearance is treated completely independently of the other appearances, using value semantics. However, if you use the SQLJ translator `-bind-by-identifier=true` setting, then this is not the case. With a `true` setting, multiple appearances of the same host variable in a given SQLJ statement or PL/SQL block are treated as a single bind occurrence.

- When binding a string host expression into a `WHERE` clause for comparison against `CHAR` data, be aware that there is a SQLJ option, `-fixedchar`, that accounts for blank padding in the `CHAR` column when the comparison is made.

#### 5.3.3 Examples of Host Expressions

The following examples will help clarify the preceding syntax discussion.

**Note:**

Some of these examples use `SELECT INTO` statements, which are described in "Single-Row Query Results: SELECT INTO Statements".

##### Example 1

In this example, two input host variables are used, one as a test value for a `WHERE` clause and one to contain new data to be sent to the database.

Presume you have a database employee table `emp` with an `ename` column for employee names and a `sal` column for employee salaries. The relevant Java code that defines the host variables is as follows:

    String empname = "SMITH";
    double salary = 25000.0;
    ...
    #sql { UPDATE emp SET sal = :salary WHERE ename = :empname };

`IN` is the default, but you can state it explicitly as well:

    #sql { UPDATE emp SET sal = :IN salary WHERE ename = :IN empname };

As you can see, the colon (:) can immediately precede the variable when not using the `IN` token, but `:IN` must be followed by white space before the host variable.

##### Example 2

This example uses an output host variable in a `SELECT INTO` statement, where you want to find out the name of the employee whose employee number 28959.

    String empname;
    ...
    #sql { SELECT ename INTO :empname FROM emp WHERE empno = 28959 };

`OUT` is the default for an `INTO`-list, but you can state it explicitly as well:

    #sql { SELECT ename INTO :OUT empname FROM emp WHERE empno = 28959 };

This statement looks in the `empno` column of the `emp` table for employee number 28959, selects the name in the `ename` column of that row, and outputs it to the `empname` output host variable, which is a Java `String`.

##### Example 3

This example uses an arithmetic expression as an input host expression. The Java variables `balance` and `minPmtRatio` are multiplied, and the result is used to update the `minPayment` column of the `creditacct` table for account number 537845.

    float balance = 12500.0;
    float minPmtRatio = 0.05;
    ...
    #sql { UPDATE creditacct SET minPayment = :(balance * minPmtRatio)
           WHERE acctnum = 537845 };

Alternatively, to use the `IN` token:

    #sql { UPDATE creditacct SET minPayment = :IN (balance * minPmtRatio)
           WHERE acctnum = 537845 };

##### Example 4

This example shows the use of the output of a method call as an input host expression and also uses an input host variable. This statement uses the value returned by `getNewSal()` to update the `sal` column in the `emp` table for the employee who is specified by the Java `empname` variable. Java code initializing the host variables is also shown.

    String empname = "SMITH";
    double raise = 0.1;
    ...
    #sql {UPDATE emp SET sal = :(getNewSal(raise, empname))
          WHERE ename = :empname};

#### 5.3.4 Overview of Result Expressions and Context Expressions

A context expression is an input expression that specifies the name of a connection context instance or an execution context instance to be used in a SQLJ executable statement. Any legal Java expression that yields such a name can be used.

A result expression is an output expression used for query results or a function return. It can be any legal Java expression that is assignable, meaning that it can logically appear on the left side of an equals sign. This is sometimes referred to as an l-value.

The following examples can be used for either result expressions or context expressions:

- Local variables

- Declared parameters

- Class fields

- Array elements

Result expressions and context expressions appear lexically in the SQLJ space, unlike host expressions, which appear lexically in the SQL space, that is, inside the curly brackets of a SQLJ executable statement. Therefore, a result expression or context expression must not be preceded by a colon.

#### 5.3.5 Evaluation of Java Expressions at Run Time

This section discusses the evaluation of Java host expressions, connection context expressions, execution context expressions, and result expressions when your application executes.

Following is a simplified representation of a SQLJ executable statement that uses all these kinds of expressions:

    #sql [connctxt_exp, execctxt_exp] result_exp = { SQL with host expression };

Java expressions can be used as any of the following, as appropriate:

- Connection context expression: Evaluated to specify the connection context instance to be used

- Execution context expression: Evaluated to specify the execution context instance to be used

- Result expression: To receive results, for example, from a stored function

- Host expression

For ISO standard code generation, the evaluation of Java expressions is well-defined, even for the use of any side effects that depend on the order in which expressions are evaluated.

For Oracle-specific code generation, evaluation of Java expressions follows the ISO standard when there are no side effects, except when the `-bind-by-identifier` option is enabled, but is implementation-specific and subject to change when there are side effects.

**Note:**

The following discussion and the related examples later do not apply to Oracle-specific code generation. If you use side effects as described here, then request ISO code generation during translation.

The following is a summary, for ISO code, of the overall order of evaluation, execution, and assignment of Java expressions for each statement that executes during run time.

1.  If there is a connection context expression, then it is evaluated immediately, before any other Java expressions are evaluated.

2.  If there is an execution context expression, then it is evaluated after any connection context expression, but before any result expression.

3.  If there is a result expression, then it is evaluated after any context expressions, but before any host expressions.

4.  After evaluation of any context or result expressions, host expressions are evaluated from left to right as they appear in the SQL operation. As each host expression is encountered and evaluated, its value is saved to be passed to SQL.

    Each host expression is evaluated once and only once.

5.  `IN` and `INOUT` parameters are passed to SQL, and the SQL operation is executed.

6.  After execution of the SQL operation, the output parameters, Java `OUT` and `INOUT` host expressions, are assigned output in order from left to right as they appear in the SQL operation.

    Each output host expression is assigned once and only once.

7.  The result expression, if there is one, is assigned output last.

**Note:**

Host expressions inside a PL/SQL block are all evaluated together before any statements within the block are executed. They are evaluated in the order in which they appear, regardless of the control flow within the block.

Once the expressions in a statement have been evaluated, input and input-output host expressions are passed to SQL, and then the SQL operation is executed. After execution of the SQL operation, assignments are made to Java output host expressions, input-output host expressions, and result expressions as follows:

1.  `OUT` and `INOUT` host expressions are assigned output in order from left to right.

2.  The result expression, if there is one, is assigned output last.

Note that during run time, all host expressions are treated as distinct values, even if they share the same name or reference the same object. The execution of each SQL operation is treated as if invoking a remote method, and each host expression is taken as a distinct parameter. Each input or input-output parameter is evaluated and passed as it is first encountered, before any output assignments are made for that statement, and each output parameter is also taken as distinct and is assigned exactly once.

It is also important to remember that each host expression is evaluated only once. An `INOUT` expression is evaluated when it is first encountered. When the output assignment is made, the expression itself is not reevaluated nor are any side-effects repeated.

#### 5.3.6 Examples of Evaluation of Java Expressions at Run Time (ISO Code Generation)

This section discusses, for ISO code generation, how Java expressions are evaluated when your application executes.

**Note:**

Do not count on these effects if you use Oracle-specific code generation. Request ISO code generation during translation if you depend on such effects.

##### Evaluation of Prefix and Postfix Operators

When a Java expression contains a Java postfix increment or decrement operator, the incrementing or decrementing occurs after the expression has been evaluated. Similarly, when a Java expression contains a Java prefix increment or decrement operator, the incrementing or decrementing occurs before the expression is evaluated. This is equivalent to how these operators are handled in standard Java code.

The following is an example of postfix operator:

    int indx = 1;
    ...
    #sql { ... :OUT (array[indx]) ... :IN (indx++) ... };

This example is evaluated as follows:

    #sql { ... :OUT (array[1]) ... :IN (1) ... };

The `indx` variable is incremented to 2 and will have that value the next time it is encountered, but not until after `:IN (indx++)` has been evaluated.

The following is the example of postfix operator:

    int indx = 1;
    ...
    #sql { ... :OUT (array[indx++]) ... :IN (indx++) ... };

This example is evaluated as follows:

    #sql { ... :OUT (array[1]) ... :IN (2) ... };

The variable `indx` is incremented to 2 after the first expression is evaluated, but before the second expression is evaluated. It is incremented to 3 after the second expression is evaluated and will have that value the next time it is encountered.

The following example consists of both prefix and postfix operators:

    int indx = 1;
    ...
    #sql { ... :OUT (array[++indx]) ... :IN (indx++) ... };

This example is evaluated as follows:

    #sql { ... :OUT (array[2]) ... :IN (2) ... };

The variable `indx` is incremented to 2 before the first expression is evaluated. It is incremented to 3 after the second expression is evaluated and will have that value the next time it is encountered.

##### Evaluation Order of IN, INOUT, and OUT Host Expressions

Host expressions are evaluated from left to right. Whether an expression is `IN`, `INOUT`, or `OUT` makes no difference when it is evaluated. All that matters is its position in the left-to-right order.

Consider the following example:

    int[5] arry;
    int n = 0;
    ...
    #sql { SET :OUT (arry[n]) = :(++n) };

This example is evaluated as follows:

    #sql { SET :OUT (arry[0]) = 1 };

One might expect input expressions to be evaluated before output expressions, but that is not the case. The expression `:OUT (arry[n])` is evaluated first because it is the left-most expression. Then `n` is incremented prior to evaluation of `++n`, because it is being operated on by a prefix operator. Then `++n` is evaluated as 1. The result will be assigned to `arry[0]`, not `arry[1]`, because `0` was the value of `n` when it was originally encountered.

##### Expressions in PL/SQL Blocks Are Evaluated Before Statements Are Executed

Host expressions in a PL/SQL block are all evaluated in one sequence, before any have been executed. Consider the following example:

    int x=3;
    int z=5;
    ...
    #sql { BEGIN :OUT x := 10; :OUT z := :x; END };
    System.out.println("x=" + x + ", z=" + z);

This example is evaluated as follows:

    #sql { BEGIN :OUT x := 10; :OUT z := 3; END };

Therefore, it would print `x=10, z=3`.

All expressions in a PL/SQL block are evaluated before any are executed. In this example, the host expressions in the second statement, `:OUT z `and` :x`, are evaluated before the first statement is executed. In particular, the second statement is evaluated while `x` still has its original value of `3`, before it has been assigned the value `10`.

Consider another example of how expressions are evaluated within a PL/SQL block:

    int x=1, y=4, z=3;
    ...
    #sql { BEGIN
             :OUT x := :(y++) + 1;
             :OUT z := :x;
           END };

This example is evaluated as follows:

    #sql { BEGIN
              :OUT x := 4 + 1;
              :OUT z := 1;
           END };

The postfix increment operator is executed after `:(y++)` is evaluated, so the expression is evaluated as `4`, which is the initial value of `y`. The second statement, `:OUT z := :x`, is evaluated before the first statement is executed. Therefore, `x` still has its initialized value of `1`. After execution of this block, `x` will have the value `5` and `z` will have the value `1`.

The following example demonstrates the difference between two statements appearing in a PL/SQL block in one SQLJ executable statement, and the same statements appearing in separate (consecutive) SQLJ executable statements.

First, consider the following, where two statements are in a PL/SQL block.

    int y=1;
    ...
    #sql { BEGIN :OUT y := :y + 1; :OUT x := :y + 1; END };

This example is evaluated as follows:

    #sql { BEGIN :OUT y := 1 + 1; :OUT x := 1 + 1; END };

The `:y` in the second statement is evaluated before either statement is executed. Therefore, `y` has not yet received its output from the first statement. After execution of this block, both `x` and `y` have the value `2`.

Now, consider the situation where the same two statements are in PL/SQL blocks in separate SQLJ executable statements.

    int y=1;
    #sql { BEGIN :OUT y := :y + 1; END };
    #sql { BEGIN :OUT x := :y + 1; END };

The first statement is evaluated as follows:

    #sql { BEGIN :OUT y := 1 + 1; END };

Then, it is executed and `y` is assigned the value `2`.

After execution of the first statement, the second statement is evaluated as follows:

    #sql { BEGIN :OUT x := 2 + 1; END };

This time, as opposed to the previous PL/SQL block example, `y` has already received the value `2` from execution of the previous statement. Therefore, x is assigned the value `3` after execution of the second statement.

##### Expressions in PL/SQL Blocks Are Always Evaluated Once Only

Each host expression is evaluated once, and only once, regardless of program flow and logic.

Consider the following example of evaluation of host expression in a loop:

    int count = 0;
    ...
    #sql {
       DECLARE
          n NUMBER
       BEGIN
          n := 1;
          WHILE n <= 100 LOOP
             :IN (count++);
             n := n + 1;
          END LOOP;
       END
    };

The Java `count` variable will have the value `0` when it is passed to SQL, because it is operated on by a postfix operator, as opposed to a prefix operator. It will then be incremented to `1` and will hold that value throughout execution of this PL/SQL block. It is evaluated only once as the SQLJ executable statement is parsed and then is replaced by the value `1` prior to SQL execution.

Consider the following example that illustrates the evaluation of host expressions in conditional blocks. This example demonstrates how each expression is always evaluated, regardless of the program flow. As the block is executed, only one branch of the `IF...THEN...ELSE` construct can be executed. However, before the block is executed, all expressions in the block are evaluated in the order that the statements appear.

    int x;
    ...
    (operations on x)
    ...
    #sql {
       DECLARE
          n NUMBER
       BEGIN
          n := :x;
          IF n < 10 THEN
             n := :(x++);
          ELSE
             n := :x * :x;
          END LOOP;
       END
    };

Say the operations performed on `x` resulted in `x` having a value of `15`. When the PL/SQL block is executed, the `ELSE` branch will be executed and the `IF` branch will not. However, all expressions in the PL/SQL block are evaluated before execution, regardless of program logic or flow. Therefore, `x++` is evaluated, then `x` is incremented, and then each `x` is evaluated in the `(x * x)` expression. The `IF...THEN...ELSE` block is evaluated as follows:

    IF n < 10 THEN
       n := 15;
    ELSE
       n := :16 * :16;
    END LOOP;

After execution of this block, given an initial value of `15` for `x`, `n` will have the value `256`.

##### Output Host Expressions Are Assigned Left to Right, Before Result Expression

Remember that `OUT` and `INOUT` host expressions are assigned in order from left to right, and then the result expression, if any, is assigned last. If the same variable is assigned more than once, then it will be overwritten according to this order, with the last assignment taking precedence.

The following example contains multiple output host expressions referencing the same variable:

    #sql { CALL foo(:OUT x, :OUT x) };

If `foo()` outputs the values `2` and `3`, respectively, then `x` will have the value `3` after the SQLJ executable statement has finished executing. The right-hand assignment will be performed last, thereby taking precedence.

The following example contains multiple output host expressions referencing the same object:

    MyClass x = new MyClass();
    MyClass y = x;
    ...
    #sql { ... :OUT (x.field):=1 ... :OUT (y.field):=2 ... };

After execution of the SQLJ executable statement, `x.field` will have a value of `2`, and not `1`, because `x` is the same object as `y`, and `field` was assigned the value of `2` after it was assigned the value of `1`.

The following example demonstrates the difference between having the output results of a function assigned to a result expression and having the results assigned to an `OUT` host expression. Consider the following function, with the `invar` input parameter, the `outvar` output parameter, and a return value:

    CREATE FUNCTION fn(invar NUMBER, outvar OUT NUMBER)
       RETURN NUMBER AS BEGIN
          outvar := invar + invar;
          return (invar * invar);
       END fn;

Now consider an example where the output of the function is assigned to a result expression:

    int x = 3;
    #sql x = { VALUES(fn(:x, :OUT x)) };

The function will take `3` as the input, will calculate `6` as the output, and will return `9`. After execution, the `:OUT x` will be assigned first, giving `x` a value of `6`. But finally the result expression is assigned, giving `x` the return value of `9` and overwriting the value of `6` previously assigned to `x`. So `x` will have the value `9` the next time it is encountered.

Now consider an example where the output of the function is assigned to an `OUT` host variable instead of a result expression:

    int x = 3;
    #sql { BEGIN :OUT x := fn(:x, :OUT x); END };

In this case, there is no result expression and the `OUT` variables are simply assigned left to right. After execution, the first `:OUT x`, on the left side of the equation, is assigned first, giving `x` the function return value of `9`. However, proceeding left to right, the second `:OUT x`, on the right side of the equation, is assigned last, giving `x` the output value of `6` and overwriting the value of `9` previously assigned to `x`. Therefore, `x` will have the value `6` the next time it is encountered.

**Note:**

Some unlikely cases have been used in these examples to explain the concepts of how host expressions are evaluated. In practice, it is not advisable to use the same variable in both an `OUT` or `INOUT` host expression or in an `IN` host expression inside a single statement or PL/SQL block. The behavior in such cases is well defined in the Oracle SQLJ implementation, but this practice is not covered in the SQLJ specification. Therefore, code written in this manner will not be portable. Such code will generate a warning from the SQLJ translator if the `portable` flag is set during semantics-checking.

#### 5.3.7 Restrictions on Host Expressions

Do not use `in`, `out`, and `inout` as identifiers in host expressions unless they are enclosed in parentheses. Otherwise, they might be mistaken for mode specifiers. This is not case-sensitive.

For example, you could use an input host variable called `in`, as follows:

    :(in)

or:

    :IN(in)

### 5.4 Single-Row Query Results: SELECT INTO Statements

When only a single row of data is being returned, SQLJ enables you to assign selected items directly to Java host expressions inside SQL syntax. This is done using the `SELECT INTO` statement. This section covers the following topics:

- SELECT INTO Syntax

- Examples of SELECT INTO Statements

- Examples with Host Expressions in SELECT-List

- SELECT INTO Error Conditions

#### 5.4.1 SELECT INTO Syntax

The syntax for a `SELECT INTO` statement is as follows:

    #sql { SELECT expression1,..., expressionN  INTO :host_exp1,..., :host_expN
           FROM table <optional_clauses> };

Keep in mind the following:

- The items `expression1` through `expressionN` are expressions specifying what is to be selected from the database. These can be any expressions valid for any `SELECT` statement. This list of expressions is referred to as the `SELECT`-list. In a simple case, these would be names of columns from a database table. It is also legal to include a host expression in the `SELECT`-list.

- The items `host_exp1` through `host_expN` are target host expressions, such as variables or array elements. This list of host expressions is referred to as the `INTO`-list.

- The item `table` is the name of the database table, view, or snapshot from which you are selecting the data.

- The item `optional_clauses` is for any additional clauses you want to include that are valid in a `SELECT` statement, such as a `WHERE` clause.

A `SELECT INTO` statement must return one, and only one, row of data, otherwise an error will be generated at run time.

The default is `OUT` for a host expression in an `INTO`-list, but you can optionally state this explicitly:

    #sql { SELECT column_name1, column_name2  INTO :OUT host_exp1, :OUT host_exp2
           FROM table WHERE condition };

Trying to use an `IN` or `INOUT` token in the `INTO`-list will result in an error at translation time.

**Note:**

- Permissible syntax for `expression1` through `expressionN`, the `table`, and the optional clauses is the same as for any SQL `SELECT` statement.

- There can be any number of `SELECT`-list and `INTO`-list items, as long as they match. That is, one INTO-list item per SELECT-list item, with compatible types.

#### 5.4.2 Examples of SELECT INTO Statements

The examples in this section use an employee table `EMP` with the following rows:

    CREATE TABLE EMP (
       EMPNO NUMBER(4),
       ENAME VARCHAR2(10),
       HIREDATE DATE );

The following is an example of a `SELECT INTO` statement with a single host expression in the `INTO`-list:

    String empname;
    #sql { SELECT ename INTO :enpname FROM emp WHERE empno=28959 };

The following is an example of a `SELECT INTO` statement with multiple host expressions in the `INTO`-list:

    String empname;
    Date hdate;
    #sql { SELECT ename, hiredate INTO :empname, :hdate FROM emp
           WHERE empno=28959 };

#### 5.4.3 Examples with Host Expressions in SELECT-List

It is legal to use Java host expressions in the `SELECT`-list as well as in the `INTO`-list. For example, you can select directly from one host expression into another, though this is of limited usefulness, as follows:

    ...
    #sql { SELECT :name1 INTO :name2 FROM emp WHERE empno=28959 };
    ...

More realistically, you may want to perform an operation or concatenation on the data selected, as in the following examples. Assume Java variables were previously declared and assigned, as necessary.

    ...
    #sql { SELECT sal + :raise INTO :newsal FROM emp WHERE empno=28959 };
    ...

    ...
    #sql { SELECT :(firstname + " ") || emp_last_name INTO :name FROM myemp
           WHERE empno=28959 };
    ...

In the second example, presume `myemp` is a table much like the `emp` table but with an `emp_last_name` column instead of an `ename` column. In the `SELECT` statement, `firstname` is prepended to a single space (" "), using a Java host expression and the Java string concatenation operator (`+`). This result is then passed to the SQL engine, which uses SQL string concatenation operator (`||`) to append the last name.

#### 5.4.4 SELECT INTO Error Conditions

Remember that `SELECT INTO` statements are intended for queries that return exactly one row of data only. A `SELECT INTO` query that finds zero rows or multiple rows will result in an exception, as follows:

- A `SELECT INTO` finding no rows will return an exception with a SQL state of `2000`, representing a "no data" condition.

- A `SELECT INTO` finding multiple rows will return an exception with a SQL state of `21000`, representing a cardinality violation.

You can retrieve the SQL state through the `getSQLState()` method of the `java.sql.SQLException` class.

This is vendor-independent behavior that is specified in the ISO SQLJ standard. There is no vendor-specific error code in these cases. The error code is always `0`.

### 5.5 Multirow Query Results: SQLJ Iterators

A large number of SQL operations are multirow queries. Processing multirow query results in SQLJ requires a SQLJ iterator. A SQLJ iterator is a strongly typed version of a JDBC result set and is associated with the underlying database cursor. SQLJ iterators are primarily used to take query results from a `SELECT` statement.

Additionally, Oracle offers SQLJ extensions that enable you to use SQLJ iterators and result sets in the following ways:

- As `OUT` host variables in executable SQL statements

- As `INTO`-list targets, such as in a `SELECT INTO` statement

- As a return type from a stored function call

- As column types in iterator declarations (essentially, nested iterators)

**Note:**

To use a SQLJ iterator in any of these ways, its class must be declared as `public`. If you declared it at the class level or nested-class level, then it might be advisable to declare it as `public static`.

This section covers the following topics:

- Iterator Concepts

- General Steps in Using an Iterator

- Named\_ Positional\_ and Result Set Iterators

- Using Named Iterators

- Using Positional Iterators

- Using Iterators and Result Sets as Host Variables

- Using Iterators and Result Sets as Iterator Columns

**See Also:**

"[Iterator Class Implementation and Advanced Functionality](advanced-language-features.md)"

#### 5.5.1 Iterator Concepts

Using a SQLJ iterator declaration results in a strongly typed iterator. This is the typical usage for iterators and takes particular advantage of SQLJ semantics-checking features during translation. It is also possible, and at times advantageous, to use weakly typed iterators. There are generic classes you can instantiate in order to use a weakly typed iterator.

This section covers the following topics:

- Overview of Strongly Typed Iterators

- Overview of Weakly Typed Iterators

##### 5.5.1.1 Overview of Strongly Typed Iterators

Before using a strongly typed iterator object, you must declare an iterator class. An iterator declaration specifies a Java class that SQLJ constructs for you, where the class attributes define the type and, optionally, the name of the columns of data in the iterator.

A SQLJ iterator object is an instance of such a specifically declared iterator class, with a fixed number of columns of predefined type. This is as opposed to a JDBC result set object, which is a standard `java.sql.ResultSet` instance and can, in principle, contain any number of columns of any type.

When you declare an iterator, you specify either just the data type of the selected columns, or both the data type and the name of the selected columns:

- Specifying the names and data types defines a named iterator class.

- Specifying just the data types defines a positional iterator class.

The data types and names, if applicable, that you declare determine how query results will be stored in iterator objects you instantiate from that class. SQL data retrieved into an iterator object are converted to the Java types specified in the iterator declaration.

When you query to populate a named iterator object, the name and data type of the columns in the `SELECT` statement must match the name and data type of the iterator columns. However, this is not case-sensitive. The order of the columns in the `SELECT` statement is irrelevant. All that matters is that each column name in the `SELECT` statement matches an iterator column name. In the simplest case, the database column names directly match the iterator column names.

For example, data from an `ENAME` column in a database table can be selected and put into an iterator `ename` column. Alternatively, you can use an alias to map a database column name to an iterator column name if the names differ. Also, in a more complicated query, you can perform an operation between two columns and alias the result to match the corresponding iterator column name.

Because SQLJ iterators are strongly typed, they offer the benefit of Java type-checking during the SQLJ semantics-checking phase.

As an example, consider the following table:

    CREATE TABLE EMPSAL (
       EMPNO NUMBER(4),
       ENAME VARCHAR2(10),
       OLDSAL NUMBER(10),
       RAISE NUMBER(10) );

Given this table, you can declare a named iterator as follows.

    #sql iterator SalNamedIter (int empno, String ename, float raise);

Once declared, you can use this named iterator as follows:

    class MyClass {
       void func() throws SQLException {
          ...
          SalNamedIter niter;
          #sql niter = { SELECT ename, empno, raise FROM empsal };

          ... process niter ...
       }
    }

This is a simple case where the iterator column names match the table column names. Note that the order of items in the `SELECT` statement does not matter when you use a named iterator. Data is matched by name, not position.

When you query to populate a positional iterator object, the data is retrieved according to the order in which you select the columns. Data from the first column selected from the database table is placed into the first column of the iterator, and so on. The data types of the table columns must be convertible to the types of the iterator columns, but the names of the database columns are irrelevant, as the iterator columns have no names.

Given the `EMPSAL` table, you can declare a positional iterator as follows:

    #sql iterator SalPosIter (int, String, float);

You can use this positional iterator as follows:

    class MyClass {
       void func() throws SQLException {
          ...
          SalPosIter piter;
          #sql piter = { SELECT empno, ename, raise FROM empsal };

          ... process piter ...
       }
    }

Note that the order of the data items in the `SELECT` statement must be the same as in the iterator. The processing differs between named iterators and positional iterators.

##### General Iterator Notes

In addition to the preceding concepts, be aware of the following general notes about iterators:

- The `SELECT *` syntax is allowed in populating an iterator, but is not recommended. In the case of a positional iterator, this requires that the number of columns in the table be equal to the number of columns in the iterator, and that the data types match in order. In the case of a named iterator, this requires that the number of columns in the table be greater than or equal to the number of columns in the iterator and that the name and data type of each iterator column match a database table column. However, if the number of columns in the table is greater, then a warning will be generated unless the translator `-warn=nostrict` flag is set.

- Positional and named iterators are distinct and incompatible kinds of Java classes. An iterator object of one kind cannot be cast to an iterator object of the other kind.

- Unlike a SQL cursor, an iterator instance is a first-class Java object. That is, it can be passed and returned as a method parameter, for example. Also, an iterator instance can be declared using Java class modifiers, such as `public` or `private`.

- SQLJ supports interoperability and conversion between SQLJ iterators and JDBC result sets.

- Generally speaking, the contents of an iterator is determined only by the state of the database at the time of execution of the `SELECT` statement that populated it. Subsequent `UPDATE`, `INSERT`, `DELETE`, `COMMIT`, or `ROLLBACK` operations have no effect on the iterator or its contents. The exception to this is if you declare an iterator to be scrollable and sensitive to changes in the data.

##### 5.5.1.2 Overview of Weakly Typed Iterators

In case you do not want to declare an iterator class, the Oracle SQLJ implementation enables you to use a weakly typed iterator. Such iterators are known as result set iterators. To use a plain, that is, nonscrollable result set iterator, instantiate the `sqlj.runtime.ResultSetIterator` class. To use a scrollable result set iterator, instantiate the `sqlj.runtime.ScrollableResultSetIterator` class.

The drawback to using result set iterators, compared to strongly typed iterators, is that SQLJ cannot perform as much semantics-checking for your queries.

#### 5.5.2 General Steps in Using an Iterator

You must follow the following general steps to use SQLJ named or positional iterator:

1.  Use a SQLJ declaration to define the iterator class (in other words, to define the iterator type).

2.  Declare a variable of the iterator class.

3.  Populate the iterator variable with the results from a SQL query, using a `SELECT` statement.

4.  Access the query columns in the iterator. How to accomplish this differs between named iterators and positional iterators.

5.  When you finish processing the results of the query, close the iterator to release its resources.

#### 5.5.3 Named, Positional, and Result Set Iterators

There are advantages and appropriate situations for each kind of SQLJ iterator.

Named iterators enable greater flexibility. Because data selection into a named iterator matches the columns in the `SELECT` statement to iterator columns by name, you need not be concerned about the order in your query. This is less prone to error, as it is not possible for data to be placed into the wrong column. If the names do not match, then the SQLJ translator will generate an error when it checks the SQL statements against the database.

Positional iterators offer a familiar paradigm and syntax to developers who have experience with other embedded-SQL languages. With named iterators you use a `next()` method to retrieve data, while with positional iterators you use `FETCH INTO` syntax similar to that of Pro\*C, for example. Each fetch implicitly advances to the next available row of the iterator before retrieving the next set of values.

However, positional iterators do offer less flexibility than named iterators, because you are selecting data into iterator columns by position, instead of by name. You must be certain of the order of items in your `SELECT` statement. Also, you must select data into all columns of the iterator. It is possible to have data written into the wrong iterator column, if the data type of that column happens to match the data type of the table column being selected.

Access to individual data elements is also less convenient with positional iterators. Named iterators, because they store data by name, are able to have convenient accessor methods for each column. For example, there would be an `ename()` method to retrieve data from an `ename` iterator column. With positional iterators, you must fetch data directly into Java host expressions with the `FETCH INTO` statement, and the host expressions must be in the correct order.

If you do not want to declare strongly typed iterator classes for your queries, then you can choose the alternative of using weakly typed result set iterators. Result set iterators are most convenient when converting JDBC code to SQLJ code. You must balance this consideration against the fact that result set iterators, either `ResultSetIterator` instances or `ScrollableResultSetIterator` instances, do not allow complete SQLJ semantics-checking during translation. With named or positional iterators, SQLJ verifies that the data types of columns in the `SELECT` statement match the Java types into which the data will be materialized. With result set iterators, this is not possible.

##### Comparative Iterator Notes

Be aware of the following notes regarding SQLJ iterators:

- In populating a positional iterator, the number of columns you select from the database must equal the number of columns in the iterator. In populating a named iterator, the number of columns you select from the database can never be less than the number of columns in the iterator, but can be greater than the number of columns in the iterator if you have the translator `-warn=nostrict` flag set. Unmatched columns are ignored in this case.

- Although the term "fetching" often refers to fetching data from a database, remember that a `FETCH INTO` statement for a positional iterator does not necessarily involve a round trip to the server. This depends on the row-prefetch value. This is because you are fetching data from the iterator, and not the database. However, if the row-prefetch value is `1`, then each fetch does involve a separate trip to the database. The row-prefetch value determines how many rows are retrieved with each trip to the database.

- Result set iterators use the same `FETCH INTO` syntax that is used with positional iterators and are subject to the same restriction at run time. That is, the number of data items in the `SELECT`-list must match the number of variables that are assigned data in the `FETCH` statement.

#### 5.5.4 Using Named Iterators

When you declare a named iterator class, you declare the name as well as the data type of each column of the iterator. When you select data into a named iterator, the columns in the `SELECT` statement must match the iterator columns in two ways:

- The name of each data item in the `SELECT` statement, either a table column name or an alias, must match an iterator column name. However, this is not case-sensitive. That is, `ename` or `Ename` would match `ENAME`).

- The data type of each iterator column must be compatible with the data type of the corresponding data item in the `SELECT` statement according to standard JDBC type mappings.

The order in which attributes are declared in the named iterator class declaration is irrelevant. Data is selected into the iterator based on name alone.

A named iterator has a `next()` method to retrieve data row by row and an accessor method for each column to retrieve the individual data items. The accessor method names are identical to the column names. Unlike most accessor method names in Java, accessor method names in named iterator classes do not start with `get`. For example, a named iterator object with a column `sal` would have a `sal()` accessor method.

**Note:**

The following restrictions apply in naming the columns of a named iterator:

- Column names cannot use Java reserved words.

- Column names cannot have the same name as utility methods provided in named iterator classes, such as the `next()`, `close()`, `getResultSet()`, and `isClosed()` methods. For scrollable named iterators, this includes additional methods such as `previous()`, `first()`, and `last()`.

##### Declaring Named Iterator Classes

Use the following syntax to declare a named iterator class:

    #sql <modifiers> iterator classname <implements clause> <with clause>
         ( type-name-list );

In this syntax, `modifiers` is an optional sequence of legal Java class modifiers, `classname` is the desired class name for the iterator, and `type-name-list` is a list of the Java types and names equivalent to or compatible with the column types and column names in a database table.

The `implements` clause and `with` clause are optional, specifying interfaces to implement and variables to define and initialize, respectively.

**See Also:**

"Declaration IMPLEMENTS Clause" and "Declaration WITH Clause"

Consider the following table:

    CREATE TABLE PROJECTS (
       ID NUMBER(4),
       PROJNAME VARCHAR(30),
       START_DATE DATE,
       DURATION NUMBER(3) );

You can declare the following named iterator to use with this table:

    #sql public iterator ProjIter (String projname, int id, Date deadline);

This will result in an iterator class with columns of data accessible, using the following provided accessor methods: `projname()`, `id()`, and `deadline()`.

**Note:**

As with standard Java, any public class should be declared in one of the following ways:

- Declare it in a separate source file. The base name of the file should be the same as the class name.

- Declare it at class-level scope or nested-class-level scope, with `public static` modifiers.

This is a requirement if you are using the standard `javac` compiler provided with the Sun Microsystems JDK.

##### Instantiating and Populating Named Iterators

Continuing to use the `PROJECTS` table and `ProjIter` iterator defined in the preceding section, note that there are columns in the table whose names and data types match the `id` and `projname` columns of the iterator. However, you must use an alias and perform an operation to populate the `deadline` column of the iterator. Following is an example:

    ProjIter projsIter;

    #sql projsIter = { SELECT start_date + duration AS deadline, projname, id
                       FROM projects WHERE start_date + duration >= sysdate };

This calculates a deadline for each project by adding its duration to its start date, then aliases the results as `deadline` to match the `deadline` iterator column. It also uses a `WHERE` clause so that only future deadlines are processed, that is, deadlines beyond the current system date in the database.

Similarly, you must create an alias if you want to use a function call. Suppose you have a `MAXIMUM()` function that takes a `DURATION` entry and an integer as input and returns the maximum of the two. For example, you could input the value `3` to ensure that each project has at least a three-month duration in your application.

Now, presume you are declaring your iterator as follows:

    #sql public iterator ProjIter2 (String projname, int id, float duration);

You could use the `MAXIMUM()` function in your query, with an alias for the result, as follows:

    ProjIter2 projsIter2;

    #sql projsIter2 = { SELECT id, projname, maximum(duration, 3) AS duration
                        FROM projects };

Generally, you must use an alias in your query for any data item in the `SELECT` statement whose name is not a legal Java identifier or does not match a column name in the iterator.

Remember that in populating a named iterator, the number of columns you select from the database can never be less than the number of columns in the iterator. The number of columns you select can be greater than the number of columns in the iterator, because unmatched columns are ignored. However, this will generate a warning, unless you have the SQLJ `-warn=nostrict` option set.

##### Accessing Named Iterators

Use the `next()` method of the named iterator object to step through the data that was selected into it. To access each column of each row, use the accessor methods generated by SQLJ, typically inside a `while` loop.

Whenever `next()` is called:

- If there is another row to retrieve from the iterator, then `next()` retrieves the row and returns `true`.

- If there are no more rows to retrieve, `next()` returns `false`.

The following is an example of how to access the data of a named iterator, repeating the declaration, instantiation, and population code illustrated in the preceding section.

**Note:**

Each iterator has a `close()` method that you must always call when you finish retrieving data from the iterator. This is necessary to close the iterator and free its resources.

Presume the following iterator class declaration:

    #sql public iterator ProjIter (String projname, int id, Date deadline);

Populate and then access an instance of this iterator class as follows:

    // Declare the iterator variable
    ProjIter projsIter;

    // Instantiate and populate iterator; order of SELECT doesn't matter
    #sql projsIter = { SELECT start_date + duration AS deadline, projname, id
                       FROM projects WHERE start_date + duration >= sysdate };

    // Process the results
    while (projsIter.next()) {
       System.out.println("Project name is " + projsIter.projname());
       System.out.println("Project ID is " + projsIter.id());
       System.out.println("Project deadline is " + projsIter.deadline());
    }

    // Close the iterator
    projsIter.close();
    ...

Note the convenient use of the `projname()`, `id()`, and `deadline()` accessor methods to retrieve the data. Note also that the order of the `SELECT` items does not matter, nor does the order in which the accessor methods are used.

However, remember that accessor method names are created with the case exactly as in your declaration of the iterator class. The following will generate compilation errors.

Consider the following declaration of the iterator:

    #sql iterator Cursor1 (String NAME);

The code for using the iterator is as follows:

    ...
    Cursor1 c1;
    #sql c1 = { SELECT NAME FROM TABLE };
    while (c1.next()) {
       System.out.println("The name is " + c1.name());
    }
    ...

The `Cursor1` class has a method called `NAME()`, and not `name()`. You will have to use `c1.NAME()` in the `System.out.println` statement.

#### 5.5.5 Using Positional Iterators

When you declare a positional iterator class, you declare the data type of each column but not the column name. The Java types into which the columns of the SQL query results are selected must be compatible with the data types of the SQL data. The names of the database columns or data items in the `SELECT` statement are irrelevant. Because names are not used, the order in which you declare your positional iterator Java types must exactly match the order in which the data is selected.

To retrieve data from a positional iterator once data has been selected into it, use a `FETCH INTO` statement followed by an `endFetch()` method call to determine if you have reached the end of the data.

##### Declaring Positional Iterator Classes

Use the following syntax to declare a positional iterator class:

    #sql <modifiers> iterator classname <implements clause> <with clause>
         ( position-list );

In this syntax, `modifiers` is an optional sequence of legal Java class modifiers and the` ``position-list` is a list of Java types compatible with the column types in a database table.

The `implements` clause and `with` clause are optional, specifying interfaces to implement and variables to define and initialize, respectively.

**See Also:**

"Declaration IMPLEMENTS Clause" and "Declaration WITH Clause"

Now consider an employee table `EMP` with the following rows:

    CREATE TABLE EMP (
       EMPNO NUMBER(4),
       ENAME VARCHAR2(10),
       SAL NUMBER(7,2) );

And consider the following positional iterator declaration:

    #sql public iterator EmpIter (String, int, float);

This example defines the `EmpIter` Java class with unnamed `String`, `int`, and `float` columns. Note that the table columns and iterator columns are in a different order, with the `String` corresponding to `ENAME` and the `int` corresponding to `EMPNO`. The order of the iterator columns determines the order in which you must select the data.

**Note:**

As with standard Java, any public class should be declared in one of the following ways:

- Declare it in a separate source file. The base name of the file should be the same as the class name.

- Declare it at class-level scope or nested-class-level scope, with `public static` modifiers.

This is a requirement if you are using the standard `javac` compiler provided with the Sun Microsystems JDK.

##### Instantiating and Populating Positional Iterators

Instantiating and populating a positional iterator is no different than doing so for a named iterator, except that you must be certain that the data items in the `SELECT` statement are in the proper order.

The three data types in the `EmpIter` iterator class are compatible with the types of the `EMP` table, but be careful how you select the data, because the order is different. The following will work, because the data items in the `SELECT` statement are in the same order as the iterator columns:

    EmpIter empsIter;

    #sql empsIter = { SELECT ename, empno, sal FROM emp };

Remember that in populating a positional iterator, the number of columns you select from the database must equal the number of columns in the iterator.

##### Accessing Positional Iterators

Access the columns defined by a positional iterator using SQL `FETCH INTO` syntax. The `INTO` part of the command specifies Java host variables that receive the results columns. The host variables must be in the same order as the corresponding iterator columns. Use the `endFetch()` method provided with all positional iterator classes to determine whether the last fetch reached the end of the data.

**Note:**

- The `endFetch()` method initially returns `true` before any rows have been fetched, then returns `false` once a row has been successfully retrieved, and then returns `true` again when a `FETCH` finds no more rows to retrieve. Therefore, you must perform the `endFetch()` test after the `FETCH INTO` statement. If your `endFetch()` test precedes the `FETCH INTO` statement, then you will never retrieve any rows, because `endFetch()` would be true before your first `FETCH` and you would immediately break out of the `while` loop.

- The `endFetch()` test must be before the results are processed, however, because the `FETCH` does not throw a SQL exception when it reaches the end of the data, it just triggers the next `endFetch()` call to return `true`. If there is no `endFetch()` test before results are processed, then your code will try to process `NULL` or invalid data from the first `FETCH` attempt after the end of the data had been reached.

- Each iterator has a `close()` method that you must always call once you finish retrieving data from it. This is necessary to close the iterator and free its resources.

The following is an example, repeating the declaration, instantiation, and population code illustrated in the preceding section. Note that the Java host variables in the `SELECT` statement are in the same order as the columns of the positional iterator, which is mandatory.

First, presume the following iterator class declaration:

    #sql public iterator EmpIter (String, int, float);

Populate and then access an instance of this iterator class as follows:

    // Declare and initialize host variables
    int empnum=0;
    String empname=null;
    float salary=0.0f;

    // Declare an iterator instance
    EmpIter empsIter;

    #sql empsIter = { SELECT first_name, employee_id, salary FROM employees };

    while (true) {
       #sql { FETCH :empsIter INTO :empnum, :empname, :salary };
       if (empsIter.endFetch()) break;  // This test must be AFTER fetch,
                                        // but before results are processed.
       System.out.println("Name is " + empname);
       System.out.println("Employee number is " + empnum);
       System.out.println("Salary is " + salary);
    }

    // Close the iterator
    empsIter.close();
    ...

The `empname`, `empnum`, and `salary` variables are Java host variables whose types must match the types of the iterator columns.

Do not use the `next()` method for a positional iterator. A `FETCH` operation calls it implicitly to move to the next row.

**Note:**

Host variables in a `FETCH INTO` statement must always be initialized because they are assigned in one branch of a conditional statement. Otherwise, you will get a compiler error indicating they may never be assigned. `FETCH` can assign the variables only if there was a row to be fetched.

##### Positional Iterator Navigation with the next() Method

The positional iterator `FETCH` clause discussed in the preceding section performs a movement, an implicit `next()` call, before it populates the host variables, if any. As an alternative, the Oracle SQLJ implementation supports a special `FETCH` syntax in conjunction with explicit `next()` calls in order to use the same movement logic as with JDBC result sets and SQLJ named iterators. Using this special `FETCH` syntax, the semantics differ. There is no implicit `next()` call before the `INTO`-list is populated.

#### 5.5.6 Using Iterators and Result Sets as Host Variables

SQLJ supports SQLJ iterators and JDBC result sets as host variables. Using iterators and result sets is fundamentally the same, with differences in declarations and in accessor methods to retrieve the data.

**Note:**

- Additionally, SQLJ supports iterators and result sets as return variables for stored functions.

- Oracle JDBC drivers currently do not support result sets as input host variables. There is a `setCursor()` method in the `OraclePreparedStatement` class, but it raises an exception at run time, if called.

For the examples in this section, consider the following department and employee tables:

    CREATE TABLE DEPT (
       DEPTNO NUMBER(2),
       DNAME VARCHAR2(14) );

    CREATE TABLE EMP (
       EMPNO NUMBER(4),
       ENAME VARCHAR2(10),
       SAL NUMBER(7,2),
       DEPTNO NUMBER(2) );

##### Example: Use of Result Set as OUT Host Variable

This example uses a JDBC result set as an output host variable.

    ...
    ResultSet rs;
    ...
    #sql { BEGIN
              OPEN :OUT rs FOR SELECT ename, empno FROM emp;
           END };

    while (rs.next())
    {
       String empname = rs.getString(1);
       int empnum = rs.getInt(2);
    }
    rs.close();
    ...

This example opens the result set `rs` in a PL/SQL block to receive data from a `SELECT` statement, selects data from the `ENAME` and `EMPNO` columns of the `EMP` table, and then loops through the result set to retrieve data into local variables.

##### Example: Use of Iterator as OUT Host Variable

This example uses a named iterator as an output host variable.

The iterator can be declared as follows:

    #sql public <static> iterator EmpIter (String ename, int empno);

The `public` modifier is required, and the `static` modifier may be advisable if your declaration is at class level or nested-class level.

This iterator can be used as follows:

    ...
    EmpIter iter;
    ...
    #sql { BEGIN
              OPEN :OUT iter FOR SELECT ename, empno FROM emp;
           END };

    while (iter.next())
    {
       String empname = iter.ename();
       int empnum = iter.empno();

       ...process/output empname and empnum...
    }
    iter.close();
    ...

This example opens the iterator `iter` in a PL/SQL block to receive data from a `SELECT` statement, selects data from the `ENAME` and `EMPNO` columns of the `EMP` table, and then loops through the iterator to retrieve data into local variables.

##### Example: Use of Iterator as OUT Host Variable for SELECT INTO

This example uses a named iterator as an output host variable, taking data through a `SELECT INTO` statement. `OUT` is the default for host variables in an `INTO`-list.

The iterator can be declared as follows:

    #sql public <static> iterator ENameIter (String ename);

The `public` modifier is required, and the `static` modifier may be advisable if your declaration is at class level or nested-class level.

This iterator can be used as follows:

    ...
    ENameIter enamesIter;
    String deptname;
    ...

    #sql { SELECT dname, cursor
          (SELECT ename FROM emp WHERE deptno = dept.deptno)
           INTO :deptname, :enamesIter FROM dept WHERE deptno = 20 };

    System.out.println(deptname);
    while (enamesIter.next())
    {
       System.out.println(enamesIter.ename());
    }
    enamesIter.close();
    ...

This example uses nested `SELECT` statements to accomplish the following:

- Select the name of department number 20 from the `DEPT` table, selecting it into the `deptname` output host variable.

- Query the `EMP` table to select all employees whose department number is 20, selecting the resulting cursor into the `enamesIter` output host variable, which is a named iterator.

- Print the department name.

- Loop through the named iterator printing employee names. This prints the names of all employees in the department.

In most cases, using `SELECT INTO` is more convenient than using nested iterators if you are retrieving a single row in the outer `SELECT`, although that option is also available. Also, with nested iterators, you would have to process the data to determine how many rows there are in the outer `SELECT`. With `SELECT INTO` you are assured of just one row.

#### 5.5.7 Using Iterators and Result Sets as Iterator Columns

The Oracle SQLJ implementation includes extensions that allow iterator declarations to specify columns of `ResultSet` type or columns of other iterator types declared within the current scope. In other words, iterators and result sets can exist within iterators. These column types are used to retrieve a column in the form of a cursor. This is useful for nested `SELECT` statements that return nested table information.

The following examples are functionally identical. Each uses a nested result set or iterator, that is, result sets or iterators in a column within an iterator, to print all the employees in each department in the `DEPT` table. The first example uses result sets within a named iterator, the second example uses named iterators within a named iterator, and the third example uses named iterators within a positional iterator.

Following are the steps:

1.  Select each department name (`DNAME`) from the `DEPT` table.
2.  Do a nested `SELECT` into a cursor to get all employees from the `EMP` table for each department.
3.  Put the department names and sets of employees into the outer iterator (`iter`), which has a name column and an iterator column. The cursor with the employee information for any given department goes into the iterator column of the row of the outer iterator corresponding to the department.
4.  Go through a nested loop that, for each department, prints the department name and then loops through the inner iterator to print all employee names for that department.

Example 5-1 Example: Result Set Column in a Named Iterator

This example uses a column of type `ResultSet` in a named iterator.

The iterator can be declared as follows:

    #sql iterator DeptIter (String dname, ResultSet emps);

The code that uses the iterator is as follows:

    ...
    DeptIter iter;
    ...
    #sql iter = { SELECT dname, cursor
                 (SELECT ename FROM emp WHERE deptno = dept.deptno)
                  AS emps FROM dept };

    while (iter.next())
    {
       System.out.println(iter.dname());
       ResultSet enamesRs = iter.emps();
       while (enamesRs.next())
       {
          String empname = enamesRs.getString(1);
          System.out.println(empname);
       }
       enamesRs.close();
    }
    iter.close();
    ...

Example 5-2 Example: Named Iterator Column in a Named Iterator

This example uses a named iterator that has a column whose type is that of a previously defined named iterator (nested iterators).

The iterator declaration is as follows:

    #sql iterator ENameIter (String ename);
    #sql iterator DeptIter (String dname, ENameIter emps);

The code that uses this iterator is as follows:

    ...
    DeptIter iter;
    ...
    #sql iter = { SELECT dname, cursor
                 (SELECT ename FROM emp WHERE deptno = dept.deptno)
                  AS emps FROM dept };

    while (iter.next())
    {
       System.out.println(iter.dname());
       ENameIter enamesIter = iter.emps();
       while (enamesIter.next())
       {
          System.out.println(enamesIter.ename());
       }
       enamesIter.close();
    }
    iter.close();
    ...

Example 5-3 Example: Named Iterator Column in a Positional Iterator

This example uses a positional iterator that has a column whose type is that of a previously defined named iterator (nested iterators). This uses the `FETCH INTO` syntax of positional iterators. This example is functionally equivalent to the previous two.

Note that because the outer iterator is a positional iterator, there does not have to be an alias to match a column name, as was required when the outer iterator was a named iterator in the previous example.

The iterator declaration is as follows:

    #sql iterator ENameIter (String ename);
    #sql iterator DeptIter (String, ENameIter);

The code that uses this iterator is as follows:

    ...
    DeptIter iter;
    ...
    #sql iter = { SELECT dname, cursor
                 (SELECT ename FROM emp WHERE deptno = dept.deptno)
                  FROM dept };

    while (true)
    {
       String dname = null;
       ENameIter enamesIter = null;
       #sql { FETCH :iter INTO :dname, :enamesIter };
       if (iter.endFetch()) break;
       System.out.println(dname);
       while (enamesIter.next())
       {
          System.out.println(enamesIter.ename());
       }
       enamesIter.close();
    }
    iter.close();
    ...

### 5.6 Assignment Statements (SET)

SQLJ enables you to assign a value to a Java host expression inside a SQL operation. This is known as an assignment statement and is accomplished using the following syntax:

    #sql { SET :host_exp = expression };

The `host_exp` is the target host expression, such as a variable or array index. The `expression` could be a number, host expression, arithmetic expression, function call, or other construct that yields a valid result into the target host expression.

The default is `OUT` for a target host expression in an assignment statement, but you can optionally state this explicitly:

    #sql { SET :OUT host_exp = expression };

Trying to use an `IN` or `INOUT` token in an assignment statement will result in an error at translation time.

The preceding statements are functionally equivalent to the following PL/SQL code:

    #sql { BEGIN :OUT host_exp := expression; END };

Here is a simple example of an assignment statement:

    #sql { SET :x = foo1() + foo2() };

This statement assigns to `x` the sum of the return values of `foo1()` and `foo2()` and assumes that the type of `x` is compatible with the type of the sum of the outputs of these functions.

Consider the following additional examples:

    int i2;
    java.sql.Date dat;
    ...
    #sql { SET :i2 = TO_NUMBER(substr('750 etc.', 1, 3)) +
            TO_NUMBER(substr('250 etc.', 1, 3)) };
    ...
    #sql { SET :dat = sysdate };
    ...

The first statement will assign to `i2` the value `1000`. The `substr()` calls takes the first three characters of the strings, that is, "750" and "250". The `TO_NUMBER()` calls convert the strings to the numbers 750 and 250.

The second statement will read the database system date and assign it to `dat`.

An assignment statement is especially useful when you are performing operations on return variables from functions stored in the database. You do not need an assignment statement to simply assign a function result to a variable, because you can accomplish this using standard function call syntax. You also do not need an assignment statement to manipulate output from Java functions, because you can accomplish that in a typical Java statement. So you can presume that `foo1()` and `foo2()` are stored functions in the database, not Java functions.

### 5.7 Stored Procedure and Function Calls

SQLJ provides convenient syntax for calling stored procedures and stored functions in the database. These procedures and functions could be written in Java, PL/SQL, or any other language supported by the database.

A stored function requires a result expression in your SQLJ executable statement to accept the return value and, optionally, can take input, output, or input-output parameters as well.

A stored procedure does not have a return value. Optionally, it can take input, output, or input-output parameters. A stored procedure can return output through any output or input-output parameter.

This section covers the following topics:

- Calling Stored Procedures

- Calling Stored Functions

- Using Iterators and Result Sets as Stored Function Returns

#### 5.7.1 Calling Stored Procedures

Stored procedures do not have a return value but can take a list with input, output, and input-output parameters. Stored procedure calls use the `CALL` token. The `CALL` token is followed by white space and then the procedure name. There must be a space after the `CALL` token to differentiate it from the procedure name. There cannot be a set of outer parentheses around the procedure call. This differs from the syntax for function calls. The syntax for the `CALL` token is as follows:

    #sql { CALL PROC(<PARAM_LIST>) };

`PROC` is the name of the stored procedure, which can optionally take a list of input, output, and input-output parameters. `PROC` can include a schema or package name as well, such as `HR.MYPROC()`.

Presume that you have defined the following PL/SQL stored procedure:

    CREATE OR REPLACE PROCEDURE MAX_DEADLINE (deadline OUT DATE) IS
       BEGIN
          SELECT MAX(start_date + duration) INTO deadline FROM projects;
       END;

This reads the `PROJECTS` table, looks at the `START_DATE` and `DURATION` columns, calculates `start_date + duration` in each row, then takes the maximum `START_DATE + DURATION` total, and assigns it to `DEADLINE`, which is an output parameter of type `DATE`.

In SQLJ, you can call this `MAX_DEADLINE` procedure as follows:

    java.sql.Date maxDeadline;
    ...
    #sql { CALL MAX_DEADLINE(:out maxDeadline) };

For any parameters, you must use the host expression tokens `IN`, `OUT`, and `INOUT` appropriately, to match the input, output, and input-output designations of the stored procedure. Additionally, the types of the host variables you use in the parameter list must be compatible with the parameter types of the stored procedure.

**Note:**

If you want your application to be compatible with Oracle7 Database, then do not include empty parentheses for the parameter list if the procedure takes no parameters. For example:

    #sql { CALL MAX_DEADLINE };

not:

    #sql { CALL MAX_DEADLINE() };

#### 5.7.2 Calling Stored Functions

Stored functions have a return value and can also take a list of input, output, and input-output parameters. Stored function calls use the `VALUES` token. The `VALUES` token is followed by the function call. In standard SQLJ, the function call must be enclosed in a set of outer parentheses. In the Oracle SQLJ implementation, the outer parentheses are optional. When using the outer parentheses, it does not matter if there is white space between the `VALUES` token and the begin-parenthesis. The syntax for the `VALUES` token is as follows:

    #sql result = { VALUES(FUNC(PARAM_LIST)) };

In this syntax, `result` is the result expression, which takes the function return value. `FUNC` is the name of the stored function, which can optionally take a list of input, output, and input-output parameters. `FUNC` can include a schema or package name, such as `HR.MYFUNC()`.

**Note:**

A `VALUES` token can also be used in `INSERT INTO ``table`` VALUES` syntax supported by the Oracle SQL implementation, but these situations are unrelated semantically and syntactically.

Referring back to the example in "Calling Stored Procedures", consider defining the stored procedure as a stored function instead, as follows:

    CREATE OR REPLACE FUNCTION GET_MAX_DEADLINE RETURN DATE IS
       deadline DATE;
       BEGIN
          SELECT MAX(start_date + duration) INTO deadline FROM projects;
          RETURN deadline;
       END;

In SQLJ, you can call this `GET_MAX_DEADLINE` function as follows:

    java.sql.Date maxDeadline;
    ...
    #sql maxDeadline = { VALUES(GET_MAX_DEADLINE) };

The result expression must have a type compatible with the return type of the function.

In the Oracle SQLJ implementation, the following syntax is also allowed:

    #sql maxDeadline = { VALUES GET_MAX_DEADLINE };

Note that the outer parentheses is omitted.

For stored function calls, as with stored procedures, you must use the host expression tokens `IN`, `OUT`, and `INOUT` appropriately, to match the input, output, and input-output parameters of the stored function. Additionally, the types of the host variables you use in the parameter list must be compatible with the parameter types of the stored function.

**Note:**

If you want your stored function to be portable to non-Oracle environments, then you should use only input parameters in the calling sequence, not output or input-output parameters.

#### 5.7.3 Using Iterators and Result Sets as Stored Function Returns

SQLJ supports assigning the return value of a stored function to an iterator or result set variable, if the function returns a REF CURSOR type.

The following example uses an iterator to take a stored function return. Using a result set is similar.

##### Example: Iterator as Stored Function Return

This example uses an iterator as a return type for a stored function, using a `REF CURSOR` type in the process.

Presume the following function definition:

    CREATE OR REPLACE PACKAGE sqlj_refcursor AS
       TYPE EMP_CURTYPE IS REF CURSOR;
       FUNCTION job_listing (j varchar2) RETURN EMP_CURTYPE;
    END sqlj_refcursor;

    CREATE OR REPLACE PACKAGE BODY sqlj_refcursor AS
       FUNCTION job_listing (j varchar) RETURN EMP_CURTYPE IS
       DECLARE
          rc EMP_CURTYPE;
       BEGIN
          OPEN rc FOR SELECT ename, empno FROM emp WHERE job = j;
          RETURN rc;
       END;
    END sqlj_refcursor;

Declare the iterator as follows:

    #sql public <static> iterator EmpIter (String ename, int empno);

The `public` modifier is required, and the `static` modifier may be advisable if your declaration is at class level or nested-class level.

The code that uses the iterator and the function is as follows:

    EmpIter iter;
    ...
    #sql iter = { VALUES(sqlj_refcursor.job_listing('SALES')) };

    while (iter.next())
    {
       String empname = iter.ename();
       int empnum = iter.empno();

       ... process empname and empnum ...
    }
    iter.close();
    ...

This example calls the `job_listing()` function to return an iterator that contains the name and employee number of each employee whose job title is SALES. It then retrieves this data from the iterator.
