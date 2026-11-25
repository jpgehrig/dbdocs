You can run Java stored procedures in the same way as PL/SQL stored procedures. Usually, a call to a Java stored procedure is a result of database manipulation, because it is usually the result of a trigger or SQL DML call. To call a Java stored procedure, you must publish it through a call specification.

Before you can call Java stored procedures, you must load them into Oracle Database instance and publish them to SQL. Loading and publishing are separate tasks. Many Java classes, which are referenced only by other Java classes, are never published.

To load Java stored procedures automatically, you can use the `loadjava` tool. It loads Java source, class, and resource files into a system-generated database table, and then uses the SQL `CREATE JAVA {SOURCE | CLASS | RESOURCE}` statement to load the Java files into Oracle Database instance. You can upload Java files from file systems, popular Java IDEs, intranets, or the Internet.

You must perform the following steps for creating, loading, and calling Java stored procedures:

- Creating or Reusing the Java Classes

- Loading and Resolving the Java Classes

- Publishing the Java Classes

- Calling the Stored Procedures

**Note:**

To load Java stored procedures manually, you can use the `CREATE JAVA` statements. For example, in SQL\*Plus, you can use the `CREATE JAVA CLASS` statement to load Java class files from local `BFILE` and `LOB` columns into Oracle Database.

### 5.3.1 Creating or Reusing the Java Classes

Use a preferred Java IDE to create classes, or reuse existing classes that meet your requirements. Oracle Database supports many Java development tools and client-side programmatic interfaces. For example, Oracle JVM accepts programs developed in popular Java IDEs, such as Oracle JDeveloper, Symantec Visual Cafe, and Borland JBuilder.

In the following example, you create the `public` class `Oscar`. It has a single method named `quote()`, which returns a quotation from Oscar Wilde.

    public class Oscar
    {
      // return a quotation from Oscar Wilde
      public static String quote()
      {
        return "I can resist everything except temptation.";
      }
    }

Save the class as `Oscar.java`. Using a Java compiler, compile the `.java` file on your client system, as follows:

    javac Oscar.java

The compiler outputs a Java binary file, in this case, `Oscar.class`.

### 5.3.2  Loading and Resolving the Java Classes

Using the `loadjava` tool, you can load Java source, class, and resource files into Oracle Database instance, where they are stored as Java schema objects. You can run the `loadjava` tool from the command line or from an application, and you can specify several options including a resolver.

In the following example, the `loadjava` tool connects to the database using the default JDBC OCI driver. You must specify the user name and password. By default, the `Oscar` class is loaded into the schema of the user you log in as, in this case, `HR`.

    $ loadjava -user HR Oscar.class
    Password: password

When you call the `quote()` method, the server uses a resolver to search for supporting classes, such as `String`. In this case, the default resolver is used. The default resolver first searches the current schema and then the `SYS` schema, where all the core Java class libraries reside. If necessary, you can specify different resolvers.

### 5.3.3 Publishing the Java Classes

For each Java method that can be called from SQL or JDBC, you must write a call specification, which exposes the top-level entry point of the method to Oracle Database. Typically, only a few call specifications are needed. If preferred, you can generate these call specifications using Oracle JDeveloper.

In the following example, from SQL\*Plus, you connect to the database and then define a top-level call specification for the `quote()` method:

    SQL> connect HR
    Enter password: password

    SQL> CREATE FUNCTION oscar_quote RETURN VARCHAR2
    2 AS LANGUAGE JAVA
    3 NAME 'Oscar.quote() return java.lang.String';

**Related Topics**

- [Publishing Java Classes With Call Specifications](publishing-Java-classes.md)

### 5.3.4 Calling the Stored Procedures

You can call Java stored procedures from JDBC, SQLJ, and all third party languages that can access the call specification. Using the SQL `CALL` statement, you can also call the stored procedures from the top level, for example, from SQL\*Plus. Stored procedures can also be called from database triggers.

In the following example, you declare a SQL\*Plus host variable:

    SQL> VARIABLE theQuote VARCHAR2(50);

Then, you call the function `oscar_quote()`, as follows:

    SQL> CALL oscar_quote() INTO :theQuote;

    SQL> PRINT theQuote;

    THEQUOTE
    --------------------------------------------------
    I can resist everything except temptation.

You can also call the Java class using the `ojvmjava` tool.

**Related Topics**

- [Calling Stored Procedures](calling-stored-procedures.md)
- [The ojvmjava Tool](ojvmjava-tool.md)
