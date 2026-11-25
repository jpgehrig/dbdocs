This chapter discusses key issues to consider before developing and running your SQLJ application, and also provides a summary and sample applications. The following topics are discussed:

- Selection of the JDBC Driver

- Connection Considerations

- NULL-Handling

- Exception-Handling Basics

- Basic Transaction Control

- Summary: First Steps in SQLJ Code

- Oracle-Specific Code Generation (No Profiles)

- ISO Standard Code Generation

- Requirements and Restrictions for Naming

- Considerations for SQLJ in the Middle Tier

### 4.1 Selection of the JDBC Driver

You must consider which Java Database Connectivity (JDBC) driver will be appropriate for your situation and whether it may be advantageous to use different drivers for translation and run time. You must choose or register the appropriate driver class for each and then specify the driver in your connection URL.

**Note:**

Your application will require an Oracle JDBC driver if you use Oracle-specific code generation or if you use ISO SQLJ standard code generation with Oracle customizer, even if your code does not actually use Oracle-specific features.

This section covers the following topics:

- Overview of Oracle JDBC Drivers

- Driver Selection for Translation

- Driver Selection and Registration for Run Time

#### 4.1.1 Overview of Oracle JDBC Drivers

Oracle provides the following JDBC drivers:

- Oracle Call Interface (OCI) driver: For client-side use with an Oracle client installation.

- Thin driver: A pure Java driver for client-side use, particularly with applets. It does not require an Oracle client installation.

- Server-side Thin driver: Is functionally the same as the client-side Thin driver, but is for code that runs inside Oracle Database instance and needs to access a remote server.

- Server-side internal driver: For code that runs inside the target server, that is, inside Oracle Database instance that it must access.

Oracle Database 12c Release 1 (12.1) provides client-side drivers compatible with JDK 6 and JDK 7.

**See Also:**

[Oracle Database JDBC Developer's Guide](../jjdbc/introducing-JDBC.md)

**Note:**

Remember that your choices may differ between translation time and run time. For example, you may want to use Oracle JDBC OCI driver at translation time for semantics-checking, but Oracle JDBC Thin driver at run time.

##### Core JDBC Functionality

The core functionality of all Oracle JDBC drivers is the same. They support the same feature set, syntax, programming interfaces, and Oracle extensions.

All Oracle JDBC drivers are supported by the `oracle.jdbc.OracleDriver` class.

##### JDBC OCI Driver

Oracle JDBC OCI driver accesses the database by calling the OCI directly from Java, providing the highest compatibility with the different Oracle Database versions. These drivers support installed Oracle Net adapters, including interprocess communication (IPC), named pipes, TCP/IP, and IPX/SPX.

The use of native methods to call C entry points makes the OCI driver dependent on the Oracle platform, requiring an Oracle client installation that includes Oracle Net. Therefore it is not suitable for applets.

Connection strings for the OCI driver are of the following form, where `tns` is an optional TNS alias or full TNS specification:

    jdbc:oracle:oci:@<tns>

**Note:**

For backward compatibility, `oci8` is still acceptable instead of `oci`.

##### JDBC Thin Driver

Oracle JDBC Thin driver is a platform-independent, pure Java implementation that uses Java sockets to connect directly to Oracle Database from any Oracle or non-Oracle client. It can be downloaded into a browser simultaneously with the Java applet being run.

The JDBC Thin driver supports only TCP/IP protocol and requires a TNS listener to be listening on TCP/IP sockets from the database server. When the JDBC Thin driver is used with an applet, the client browser must have the capability to support Java sockets.

Connection strings for the JDBC Thin driver are typically of the following form:

    jdbc:oracle:thin:@host:port/servicename

**See Also:**

[Oracle Database JDBC Developer's Guide](../jjdbc/introducing-JDBC.md) for information about database service names

In Oracle Database 12c Release 2 (12.2), connection strings using SIDs are deprecated, but are still supported for backward compatibility:

    jdbc:oracle:thin:@host:port:sid

##### JDBC Server-Side Thin Driver

Oracle JDBC server-side Thin driver offers the same functionality as the client-side JDBC Thin driver, but runs inside the database and accesses a remote server. This is useful in accessing one Oracle Database instance from inside another, such as from a Java stored procedure.

Connection strings for the server-side Thin driver are the same as for the client-side Thin driver.

**Note:**

In order to leave the originating database when using the server-side Thin driver, the user account must have `SocketPermission` assigned. Refer to the[ Oracle Database JDBC Developer's Guide](../jjdbc/JDBC-getting-started.md) for more information. Also, refer to the[ Oracle Database Java Developer's Guide ](../jjdev/database-contents-Oracle-JVM-security.md)for general information about `SocketPermission` and other permissions.

##### JDBC Server-Side Internal Driver

Oracle JDBC server-side internal driver provides support for any Java code that runs inside the target Oracle Database instance where the SQL operations are to be performed. The server-side internal driver enables Oracle Java virtual machine (JVM) to communicate directly with the SQL engine. This driver is the default JDBC driver for SQLJ code running as a stored procedure, stored function, or trigger in Oracle Database 12c Release 2 (12.2).

Connection strings for the server-side internal driver are of the following form:

    jdbc:oracle:kprb:

If your SQLJ code uses the default connection context, then SQLJ automatically uses this driver for code running in Oracle JVM.

#### 4.1.2 Driver Selection for Translation

Use SQLJ option settings, either on the command line or in a properties file, to choose the driver manager class and specify a driver for translation.

Use the SQLJ `-driver` option to choose any driver manager class other than `OracleDriver`, which is the default.

Specify the particular JDBC driver to choose, such as JDBC Thin or JDBC OCI for Oracle Database, as part of the connection URL you specify in the SQLJ `-url` option.

**See Also:**

"[Connection Options](translator-command-line-and-options.md)"

You will typically, but not necessarily, use the same driver that you use in your source code for the run-time connection.

**Note:**

Remember that the `-driver` option does not choose a particular driver. It registers a driver class with the driver manager. One driver class might be used for multiple driver protocols, such as `OracleDriver`, which is used for all of Oracle JDBC protocols.

#### 4.1.3 Driver Selection and Registration for Run Time

To connect to the database at run time, you must register one or more drivers that will understand the URLs you specify for any of your connection instances, whether they are instances of the `sqlj.runtime.ref.DefaultContext` class or of any connection context classes that you declare.

If you are using an Oracle JDBC driver and create a default connection using the `Oracle.connect()` method, then SQLJ handles this automatically. The `Oracle.connect()` method registers the `oracle.jdbc.OracleDriver` class.

If you are using an Oracle JDBC driver, but do not use `Oracle.connect()`, then you must manually register the `OracleDriver` class, as follows:

    DriverManager.registerDriver(new oracle.jdbc.OracleDriver());

If you are not using an Oracle JDBC driver, then you must register some appropriate driver class, as follows:

    DriverManager.registerDriver(new mydriver.jdbc.driver.MyDriver());

In any case, you must also set your connection URL, user name, and password.

**See Also:**

"Single Connection or Multiple Connections Using DefaultContext"

**Note:**

As an alternative to using the JDBC driver manager in establishing JDBC connections, you can use data sources. You can specify a data source in a `with` clause, as described in "[Declaration WITH Clause](basic-language-features.md)". For general information about data sources, refer to the[ Oracle Database JDBC Developer's Guide](../jjdbc/data-sources-and-URLs.md).

### 4.2 Connection Considerations

When deciding what database connection or connections you will need for your SQLJ application, consider the following:

- Will you need just one database connection or multiple connections?

- If using multiple connections (possibly to multiple schemas), then will each connection use SQL entities of the same name: tables of the same name, columns of the same name and data types, stored procedures of the same name and signature, and so on?

- Will you need different connections for translation and run time or will the same suffice for both?

A SQLJ executable statement can specify a particular connection context instance, either of `DefaultContext` or of a declared connection context class, for its database connection. Alternatively, it can omit the connection context specification and use the default connection, which is an instance of `DefaultContext` that was previously set as the default.

**Note:**

If your operations will use different sets of SQL entities, then you will typically want to declare and use additional connection context classes.

This section covers the following topics:

- Single Connection or Multiple Connections Using DefaultContext

- Closing Connections

- Multiple Connections Using Declared Connection Context Classes

- More About the Oracle Class

- More About the DefaultContext Class

- Connection for Translation

- Connection for Customization

#### 4.2.1 Single Connection or Multiple Connections Using DefaultContext

This section discusses scenarios where you will use connection instances of only the `DefaultContext` class.

This is typical if you are using a single connection, or multiple connections that use SQL entities with the same names and data types.

##### Single Connection

For a single connection, use one instance of the `DefaultContext` class specifying the database URL, user name, and password, when you construct your `DefaultContext` object.

You can use the `connect()` method of the `oracle.sqlj.runtime.Oracle` class to accomplish this. Calling this method automatically initializes the default connection context instance. This method has several signatures, including ones that allow you to specify user name, password, and URL, either directly or using a properties file. In the following example, the properties file `connect.properties` is used:

    Oracle.connect(MyClass.class, "connect.properties");

**Note:**

The `connect.properties` file is searched for relative to the specified class. In the example, if `MyClass` is located in `my-package`, then `connect.properties` must be found in the same package location, `my-package`.

If you use `connect.properties`, then you must edit it appropriately and package it with your application. In this example, you must also import the `oracle.sqlj.runtime.Oracle` class.

Alternatively, you can specify user name, password, and URL directly:

    Oracle.connect("jdbc:oracle:thin:@localhost:5221/myservice", "HR", "hr");

In this example, the connection will use the JDBC Thin driver to connect the `HR` user with the password, `hr`, to a database on the computer, `localhost`, through port `5221`, where `myservice` is the name of the database service for the connection.

Either of these examples creates a special static instance of the `DefaultContext` class and installs it as your default connection. It is not necessary to do anything with this `DefaultContext` instance directly.

Once you have completed these steps, you do not need to specify the connection for any of the SQLJ executable statements in your application, if you want them all to use the default connection.

Note that in using a JDBC Thin driver, the URL must include the host name, port number, and service name (or SID, which is deprecated in Oracle Database 12c Release 2 (12.2)), as in the preceding example. Also, the database must have a listener running at the specified port. In using the JDBC OCI driver, no service name (or SID) is required if you intend to use the default account of the client, as will be the case in examples in this document. Alternatively, you can use name-value pairs.

**See Also:**

[Oracle Database JDBC Developer's Guide ](../jjdbc/index.md)for more information

The following URL will connect to the default account of the client:

    jdbc:oracle:oci:@

**Note:**

- `Oracle.connect()` will not set your default connection if one had already been set. In that case, it returns `null`. This enables you to use the same code on a client or in the server. If you do want to override your default connection, then use the static `setDefaultContext()` method of `DefaultContext`.

- The `Oracle.connect()` method defaults to a `false` setting of the auto-commit flag. However, it also has signatures to set it explicitly. In the Oracle JDBC implementation, the auto-commit flag defaults to `true`.

- You can optionally specify `getClass()` instead of `MyClass.class` in the `Oracle.connect()` call, as long as you are not calling `getClass()` from a static method. The `getClass()` method is used in some of the SQLJ demo applications.

- You can access the static `DefaultContext` instance, which corresponds to your default connection, as follows:

      DefaultContext.getDefaultContext();

##### Multiple Connections

For multiple connections, you can create and use additional instances of the `DefaultContext` class, while optionally still using the default connection.

You can use the `Oracle.getConnection()` method to instantiate `DefaultContext`, as in the following examples.

First, consider a case where you want most statements to use the default connection, but other statements to use a different connection. You must create one additional instance of `DefaultContext`:

    DefaultContext ctx = Oracle.getConnection (
       "jdbc:oracle:thin:@localhost2:5221/myservice2", "bill", "lion");

**Note:**

`ctx` could also use the `HR`/`hr` schema, if you want to perform multiple sets of operations on the same schema.

When you want to use the default connection, it is not necessary to specify a connection context:

    #sql { SQL operation };

This is actually a shortcut for the following:

    #sql [DefaultContext.getDefaultContext()] { SQL operation };

When you want to use the additional connection, specify `ctx` as the connection:

    #sql [ctx] { SQL operation };

Next, consider situations where you want to use multiple connections, where each of them is a named `DefaultContext` instance. This enables you to switch your connection back and forth.

The following statements establish multiple connections to the same schema (in case you want to use multiple Oracle Database sessions or transactions, for example). Instantiate the `DefaultContext` class for each connection you will need:

    DefaultContext ctx1 = Oracle.getConnection
       ("jdbc:oracle:thin:@localhost1:5221/myservice1", "HR", "hr");
    DefaultContext ctx2 = Oracle.getConnection
       ("jdbc:oracle:thin:@localhost1:5221/myservice1", "HR", "hr");

This creates two connection context instances that would use the same schema, connecting to `HR/hr` using service `myservice1` on the computer `localhost1`, using Oracle JDBC Thin driver.

Now, consider a case where you would want multiple connections to different schemas. Again, instantiate the `DefaultContext` class for each connection you will need:

    DefaultContext ctx1 = Oracle.getConnection
       ("jdbc:oracle:thin:@localhost1:5221/myservice1", "HR", "hr");
    DefaultContext ctx2 = Oracle.getConnection
       ("jdbc:oracle:thin:@localhost2:5221/myservice2", "bill", "lion");

This creates two connection context instances that use Oracle JDBC Thin driver but use different schemas. The `ctx1` object connects to `HR/hr` using service `myservice1` on the computer `localhost1`, while the `ctx2` object connects to `bill/lion` using service `myservice2` on the computer `localhost2`.

There are two ways to switch back and forth between these connections for the SQLJ executable statements in your application:

- If you switch back and forth frequently, then you can specify the connection for each statement in your application:

      #sql [ctx1] { SQL operation };
      ...
      #sql [ctx2] { SQL operation };

  **Note:**

  Include the square brackets around the connection context instance name; they are part of the syntax.

- If you use either of the connections several times in a row within your code flow, then you can periodically use the static `setDefaultContext()` method of the `DefaultContext` class to reset the default connection. This method initializes the default connection context instance. This way, you can avoid specifying connections in your SQLJ statements.

      DefaultContext.setDefaultContext(ctx1);
      #sql { SQL operation };   // These three statements all use ctx1
      #sql { SQL operation };
      #sql { SQL operation };
      ...
      DefaultContext.setDefaultContext(ctx2);
      #sql { SQL operation };   // These three statements all use ctx2
      #sql { SQL operation };
      #sql { SQL operation };

  **Note:**

  Because the preceding statements do not specify connection contexts, at translation time they will all be checked against the default connection context.

#### 4.2.2 Closing Connections

It is advisable to close your connection context instances when you are done, preferably in a `finally` clause of a `try` block (in case your application terminates with an exception).

The `DefaultContext` class, as well as any connection context classes that you declare, includes a `close()` method. Calling this method closes the SQLJ connection context instance and, by default, also closes the underlying JDBC connection instance and the physical connection.

In addition, the `oracle.sqlj.runtime.Oracle` class has a static `close()` method to close the default connection only. In the following example, presume `ctx` is an instance of any connection context class:

    ...
    finally
    {
       ctx.close();
    }
    ...

Alternatively, if the `finally` clause is not within a `try` block in case a SQL exception is encountered:

    ...
    finally
    {
       try { ctx.close(); } catch(SQLException ex) {...}
    }
    ...

Or, to close the default connection, the `Oracle` class also provides a `close()` method:

    ...
    finally
    {
       Oracle.close();
    }
    ...

Always commit or roll back any pending changes before closing the connection. Whether there would be an implicit `COMMIT` operation as the connection is closed is not specified in the JDBC standard and may vary from vendor to vendor. For Oracle, there is an implicit `COMMIT` when a connection is closed, and an implicit `ROLLBACK` when a connection is garbage-collected without being closed, but it is not advisable to rely on these mechanisms.

**Note:**

It is also possible to close a connection context instance without closing the underlying connection (in case the underlying connection is shared).

#### 4.2.3 Multiple Connections Using Declared Connection Context Classes

For multiple connections that use different sets of SQL entities, it is advantageous to use connection context declarations to define additional connection context classes. Having a separate connection context class for each set of SQL entities that you use enables SQLJ to do more rigorous semantics-checking of your code.

**See Also:**

"[Connection Contexts](advanced-language-features.md)"

#### 4.2.4 More About the Oracle Class

The Oracle SQLJ implementation provides the `oracle.sqlj.runtime.Oracle` class to simplify the process of creating and using instances of the `DefaultContext` class.

The static `connect()` method initializes the default connection context instance, instantiating a `DefaultContext` object and installing it as your default connection. You do not need to assign or use the `DefaultContext` instance returned by `connect()`. If you had already established a default connection, then `connect()` returns `null`.

The static `getConnection()` method simply instantiates a `DefaultContext` object and returns it. You can use the returned instance as desired.

Both methods register Oracle JDBC driver manager automatically if the `oracle.jdbc.OracleDriver` class is found in the `CLASSPATH`. The static `close()` method closes the default connection.

##### Signatures of the Oracle.connect() and Oracle.getConnection() Methods

Both the method have signatures that take the following parameter sets as input:

- URL (`String`), user name (`String`), password (`String`)

- URL (`String`), user name (`String`), password (`String`), auto-commit flag (`boolean`)

- URL (`String`), `java.util.Properties` object containing properties for the connection

- URL (`String`), `java.util.Properties` object, auto-commit flag (`boolean`)

- URL (`String`) fully specifying the connection, including user name and password

  The following is an example of the format of a URL string specifying user name (`HR`) and password (`hr`) when using Oracle JDBC drivers, in this case the JDBC Thin driver:

      "jdbc:oracle:thin:HR/hr@localhost:5221/myservice"

- URL (`String`), auto-commit flag (`boolean`)

- A `java.lang.Class` object for the class relative to which the properties file is loaded, name of properties file (`String`)

- A `java.lang.Class` object, name of properties file (`String`), auto-commit flag (`boolean`)

- A `java.lang.Class` object, name of properties file (`String`), user name (`String`), password (`String`)

- A `java.lang.Class` object, name of properties file (`String`), user name (`String`), password (`String`), auto-commit flag (`boolean`)

- JDBC connection object (`Connection`)

- SQLJ connection context object

These last two signatures inherit an existing database connection. When you inherit a connection, you will also inherit the auto-commit setting of that connection.

The auto-commit flag specifies whether SQL operations are automatically committed. For the `Oracle.connect()` and `Oracle.getConnection()` methods only, the default is `false`. If that is the setting you want, then you can use one of the signatures that does not take auto-commit as input. However, anytime you use a constructor to create an instance of a connection context class, including `DefaultContext`, you must specify the auto-commit setting. In the Oracle JDBC implementation, the default for the auto-commit flag is `true`.

**See Also:**

"Basic Transaction Control" and "Single Connection or Multiple Connections Using DefaultContext"

##### Optional Oracle.close() Method Parameters

In using the `Oracle.close()` method to close the default connection, you have the option of specifying whether or not to close the underlying physical database connection. By default it is closed. This is relevant if you are sharing this physical connection between multiple connection objects, either SQLJ connection context instances or JDBC connection instances.

You can keep the underlying physical connection open as follows:

    Oracle.close(ConnectionContext.KEEP_CONNECTION);

You can close the underlying physical connection (default behavior) as follows:

    Oracle.close(ConnectionContext.CLOSE_CONNECTION);

`KEEP_CONNECTION` and `CLOSE_CONNECTION` are static constants of the `ConnectionContext` interface.

**See Also:**

"[Closing Shared Connections](advanced-language-features.md)"

#### 4.2.5 More About the DefaultContext Class

The `sqlj.runtime.ref.DefaultContext` class provides a complete default implementation of a connection context class. As with classes created using a connection context declaration, the `DefaultContext` class implements the `sqlj.runtime.ConnectionContext` interface. The `DefaultContext` class has the same class definition that would have been generated by the SQLJ translator from the declaration:

    #sql public context DefaultContext;

##### DefaultContext Methods

The following are the key methods of the `DefaultContext` class:

- `getConnection()`

  Gets the underlying JDBC connection object. This is useful if you want to have JDBC code in your application, which is one way to use dynamic SQL operations. You can also use the `setAutoCommit()` method of the underlying JDBC connection object to set the auto-commit flag for the connection.

- `setDefaultContext()`

  Sets the default connection your application uses. This is a `static` method and takes a `DefaultContext` instance as input. SQLJ executable statements that do not specify a connection context instance will use the default connection that you define using this method or the `Oracle.connect()` method.

- `getDefaultContext()`

  Returns the `DefaultContext` instance currently defined as the default connection for your application. This is a `static` method.

- `close()`

  Closes the connection context instance.

The `getConnection()` and `close()` methods are specified in the `sqlj.runtime.ConnectionContext` interface.

**Note:**

On a client, `getDefaultContext()` returns `null` if `setDefaultContext()` was not previously called. However, if a data source object has been bound under "`jdbc/defaultDataSource`" in JNDI, then the client will use this data source object as its default connection.

In the server, `getDefaultContext()` returns the default connection, which is the connection to the server itself.

##### DefaultContext Constructors

It is typical to instantiate `DefaultContext` using the `Oracle.connect()` or `Oracle.getConnection()` method. However, if you want to create an instance directly, then there are five constructors for `DefaultContext`. The different input parameter sets for these constructors are:

- URL (`String`), user name (`String`), password (`String`), auto-commit (`boolean`)

- URL (`String`), `java.util.Properties` object, auto-commit (`boolean`)

- URL (`String` fully specifying connection and including user name and password), auto-commit setting (`boolean`)

  The following is an example of the format of a URL specifying user name and password when using Oracle JDBC drivers, in this case the JDBC Thin driver:

      "jdbc:oracle:thin:HR/hr@localhost:5221/myservice"

- JDBC connection object (`Connection`)

- SQLJ connection context object

The last two signatures inherit an existing database connection. When you inherit a connection, you will also inherit the auto-commit setting of that connection.

Following is an example of constructing a `DefaultContext` instance:

    DefaultContext defctx = new DefaultContext
       ("jdbc:oracle:thin:@localhost:5221/myservice", "HR", "hr", false);

##### Notes About Connection Context Constructors:

**Note:**

You must keep the following in mind when using connection context constructors:

- It is important to note that connection context class constructors, unlike the `Oracle.connect()` method, require an auto-commit setting.

- To use any of the first three constructors listed, you must first register your JDBC driver. This happens automatically if you are using an Oracle JDBC driver and call `Oracle.connect()`. Refer to "Driver Selection and Registration for Run Time".

- Connection context classes that you declare generally have the same constructor signatures as the `DefaultContext` class. However, if you declare a connection context class to be associated with a data source, a different set of constructors is provided. Refer to "[Standard Data Source Support](advanced-language-features.md)" for more information.

- When using the constructor that takes a JDBC connection object, do not initialize the connection context instance with a null JDBC connection.

- The auto-commit setting determines whether SQL operations are automatically committed. Refer to "Basic Transaction Control" for more information.

##### Optional DefaultContext close() Method Parameters

When you close a connection context instance, you have the option of specifying whether or not to close the underlying physical connection. By default it is closed. This is relevant if you are sharing the physical connection between multiple connection objects, either SQLJ connection context instances or JDBC connection instances. The following examples presume a `DefaultContext` instance `defctx`.

To keep the underlying physical connection open, use the following:

    defctx.close(ConnectionContext.KEEP_CONNECTION);

To close the underlying physical connection, which is the default behavior, use the following:

    defctx.close(ConnectionContext.CLOSE_CONNECTION);

`KEEP_CONNECTION` and `CLOSE_CONNECTION` are static constants of the `ConnectionContext` interface.

**See Also:**

"[Closing Shared Connections](advanced-language-features.md)" for more information about using these parameters and about shared connections

#### 4.2.6 Connection for Translation

If you want to use online semantics-checking during translation, then you must specify a database connection for SQLJ to use. These are referred to as exemplar schemas.

**See Also:**

"[Connection Context Concepts](advanced-language-features.md)"

You can use different connections for translation and run time. In fact, it is often necessary or preferable to do so. It might be necessary if you are not developing the application in the same kind of environment that it will run in. But even if the run-time connection is available during translation, it might be preferable to create an account with a narrower set of resources so that your online checking will be tighter. This would be true if your application uses only a small subset of the SQL entities available in the run-time connection. Your online checking would be tighter and more meaningful if you create an exemplar schema consisting only of SQL entities that your application actually uses.

Use the SQLJ translator connection options, either on the command line or in a properties file, to specify a connection for translation.

**See Also:**

"[Connection Options](translator-command-line-and-options.md)"

#### 4.2.7 Connection for Customization

Generally, Oracle customization does not require a database connection. However, the Oracle SQLJ implementation does support customizer connections. This is useful in two circumstances:

- If you are using Oracle customizer with the `optcols` option enabled, then a connection is required. This option allows iterator column type and size definitions for performance optimization.

- If you are using `SQLCheckerCustomizer`, a specialized customizer that performs semantics-checking on profiles, then a connection is required if you are using an online checker, which is true by default.

For Oracle-specific code generation, the SQLJ translator has an `-optcols` option with the same functionality. The `SQLCheckerCustomizer` is invoked through Oracle customizer harness `verify` option. Use the customizer harness `user`, `password`, `url`, and `driver` options to specify connection parameters for whatever customizer you are using, as appropriate.

**See Also:**

- "[Oracle Customizer Column Definition Option (optcols)](appendix.md)".

- "[SQLCheckerCustomizer for Profile Semantics-Checking](appendix.md)"

- "[Customizer Harness Options for Connections](appendix.md)"

### 4.3 NULL-Handling

Java primitive types, such as `int`, `double`, or `float`, cannot have null values. You must consider this in choosing your result expression and host expression types.

This section covers the following topics:

- Wrapper Classes for NULL-Handling

- Examples of NULL-Handling

#### 4.3.1 Wrapper Classes for NULL-Handling

SQLJ consistently enforces retrieving SQL `NULL` as Java `null`, in contrast to JDBC, which retrieves `NULL` as `0` or `false` for certain data types. Therefore, do not use Java primitive types in SQLJ for output variables in situations where a SQL `NULL` may be received, because Java primitive types cannot take `null` values.

This pertains to result expressions, output or input-output host expressions, and iterator column types. If the receiving Java type is primitive and an attempt is made to retrieve a SQL `NULL`, then a `sqlj.runtime.SQLNullException` is thrown and no assignment is made.

To avoid the possibility of `NULL` being assigned to Java primitives, use the following wrapper classes instead of primitive types:

- `java.lang.Boolean`

- `java.lang.Byte`

- `java.lang.Short`

- `java.lang.Integer`

- `java.lang.Long`

- `java.lang.Double`

- `java.lang.Float`

In case you must convert back to a primitive value, each of these wrapper classes has an `xxx``Value()` method. For example, `intValue()` returns an `int` value from an `Integer` object and `floatValue()` returns a `float` value from a `Float` object. For example, presuming `intobj` is an `Integer` object:

    int j = intobj.intValue();

**Note:**

- `SQLNullException` is a subclass of the standard `java.sql.SQLException` class.

- Because Java objects can have `null` values, there is no need for indicator variables in SQLJ, such as those used in other host languages like C, C++, and COBOL.

#### 4.3.2 Examples of NULL-Handling

The following examples show the use of the `java.lang` wrapper classes to handle `NULL`.

##### Example: Null Input Host Variable

In the following example, a `Float` object is used to pass a `null` value to the database:

    int empno = 7499;
    Float commission = null;

    #sql { UPDATE employees SET commission_pct = :commission WHERE employee_id = :empno };

You cannot use the Java primitive type `float` to accomplish this.

##### Example: Null Iterator Rows

In the following example, a `Double` column type is used in an iterator to allow for the possibility of `null` data.

For each employee in the `employee` table whose salary is at least \$50,000, the employee name (`FIRST_NAME`) and commission (`COMMISSION_PCT`) are selected into the iterator. Then each row is tested to determine if the `COMMISSION_PCT` field is, in fact, null. If so, then it is processed accordingly.

    #sql iterator EmployeeIter (String first_name, Double commission);

    EmployeeIter ei;
    #sql ei = { SELECT first_name, commission_pct FROM employees WHERE salary >= 50000 };

    while (ei.next())
    {
       if (ei.commission_pct() == null)
          System.out.println(ei.first_name() + " is not on commission.");
    }
    ei.close();
    ...

**Note:**

To execute a `WHERE` clause comparison against `NULL`, use the following SQL syntax:

    ...WHERE :x IS NULL

### 4.4 Exception-Handling Basics

This section covers the basics of handling exceptions in SQLJ application, including requirements for error-checking. This section covers the following topics:

- SQLJ and JDBC Exception-Handling Requirements

- Processing Exceptions

- Using SQLException Subclasses

#### 4.4.1 SQLJ and JDBC Exception-Handling Requirements

Because SQLJ executable statements result in JDBC calls through `sqlj.runtime`, and JDBC requires SQL exceptions to be caught or thrown, SQLJ also requires SQL exceptions to be caught or thrown in any block containing SQLJ executable statements. Your source code will generate errors during compilation if you do not include appropriate exception-handling.

Handling SQL exceptions requires the `SQLException` class, which is included in the standard JDBC `java.sql.*` package.

##### Example: Exception Handling

This example demonstrates the basic exception-handling required in SQLJ applications. The code declares a `main` method with a `try/catch` block and another method, which throws `SQLException` when an exception is encountered. The code is as follows:

        /* Import SQLExceptions class.  The SQLException comes from
           JDBC. Executable #sql clauses result in calls to JDBC, so methods
           containing executable #sql clauses must either catch or throw
           SQLException.
        */
    import java.sql.* ;
    import oracle.sqlj.runtime.Oracle;

        // iterator for the select

    #sql iterator MyIter (String ITEM_NAME);

    public class TestInstallSQLJ
    {
        //Main method
      public static void main (String args[])
      {
        try {

        // Set the default connection to the URL, user, and password
        // specified in your connect.properties file
          Oracle.connect(TestInstallSQLJ.class, "connect.properties");

          TestInstallSQLJ ti = new TestInstallSQLJ();

        // This method throws SQLException. Therefore, it ic called within a try block
          ti.runExample();

        } catch (SQLException e) {
          System.err.println("Error running the example: " + e);
        }

      } //End of method main

      //Method that runs the example
      void runExample() throws SQLException
      {
          //Issue SQL command to clear the SALES table
        #sql { DELETE FROM SALES };
        #sql { INSERT INTO SALES(ITEM_NAME) VALUES ('Hello, SQLJ!')};

        MyIter iter;
        #sql iter = { SELECT ITEM_NAME FROM SALES };

        while (iter.next()) {
          System.out.println(iter.ITEM_NAME());
        }
      }
    }

#### 4.4.2 Processing Exceptions

This section discusses ways to process and interpret exceptions in your SQLJ application. During run time, exceptions may be raised from any of the following:

- SQLJ run time

- JDBC driver

- RDBMS

##### Printing Error Text

The example in the previous section showed how to catch SQL exceptions and output the error messages. Part of that code is as follows:

    ...
    try {
    ...
    } catch (SQLException e) {
          System.err.println("Error running the example: " + e);
    }
    ...

This will print the error text from the `SQLException` object.

You can also retrieve error information using the `getMessage()`, `getErrorCode()`, and `getSQLState()` methods the `SQLException` class.

Printing the error text, as in this example, prints the error message with some additional text, such as `SQLException`.

##### Retrieving SQL States and Error Codes

The `java.sql.SQLException` class and subclasses include the `getMessage()`, `getErrorCode()`, and `getSQLState()` methods. Depending on where the exception or error originated and how they are implemented there, the following methods provide additional information:

- `String getMessage()`

  If the error originates in the SQLJ run time or JDBC driver, then this method returns the error message with no prefix. If the error originates in the RDBMS, then it returns the error message prefixed by the `ORA` number.

- `int getErrorCode()`

  If the error originates in the SQLJ run time, then this method returns no meaningful information. If the error originates in the JDBC driver or RDBMS, then it returns the five-digit `ORA` number as an integer.

- `String getSQLState()`

  If the error originates in the SQLJ run time, then this method returns a string with a five-digit code indicating the SQL state. If the error originates in the JDBC driver, then it returns no meaningful information. If the error originates in the RDBMS, then it returns the five-digit SQL state. Your application should have appropriate code to handle `null` values returned.

The following example prints the error message and also checks the SQL state:

    ...
    try {
    ...
    } catch (SQLException e) {
          System.err.println("Error running the example: " + e);
          String sqlState = e.getSQLState();
          System.err.println("SQL state = " + sqlState);
    }
    ...

#### 4.4.3 Using SQLException Subclasses

For more specific error-checking, use any available and appropriate subclasses of the `java.sql.SQLException` class.

SQLJ provides the `sqlj.runtime.NullException` class, which is a subclass of `java.sql.SQLException`. You can use this exception in situations where a `NULL` might be returned into a Java primitive variable.

For batch-enabled environments, there is also the standard `java.sql.BatchUpdateException` subclass. Refer to "[Error Conditions During Batch Execution](performance-and-debugging.md)" for further information.

When you use a subclass of `SQLException`, catch the subclass exception before catching `SQLException`, as in the following example:

    ...
    try {
    ...
    } catch (SQLNullException ne) {
         System.err.println("Null value encountered: " + ne); }
      catch (SQLException e) {
         System.err.println("Error running the example: " + e); }
    ...

This is because a subclass exception can also be caught as a `SQLException`. If you catch `SQLException` first, then execution will not proceed to the part where you have coded special processing for the subclass exception.

### 4.5 Basic Transaction Control

This section discusses how to manage data updates. It covers the following topics:

- Overview of Transactions

- Automatic Commits Versus Manual Commits

- Specifying Auto-Commit as You Define a Connection

- Modifying Auto-Commit in an Existing Connection

- Using Manual COMMIT and ROLLBACK

- Effect of Commits and Rollbacks on Iterators and Result Sets

- Using Savepoints

**See Also:**

"[Advanced Transaction Control](advanced-language-features.md)"

#### 4.5.1 Overview of Transactions

A transaction is a sequence of SQL operations that Oracle treats as a single unit. A transaction begins with the first executable SQL statement after any of the following:

- Connection to the database

- `COMMIT` (committing data updates, either automatically or manually)

- `ROLLBACK` (canceling data updates)

A transaction ends with a `COMMIT` or `ROLLBACK` operation.

**Note:**

In Oracle Database 12c Release 2 (12.2), all data definition language (DDL) statements, such as `CREATE` and `ALTER`, include an implicit `COMMIT`. This will commit not only the DDL statement, but all the preceding data manipulation language (DML) statements, such as `INSERT`, `DELETE`, and `UPDATE`, that have not yet been committed or rolled back.

#### 4.5.2 Automatic Commits Versus Manual Commits

In using SQLJ or JDBC, you can either have your data updates automatically committed or commit them manually. In either case, each `COMMIT` operation starts a new transaction. You can specify that changes be committed automatically by enabling the auto-commit flag. This can be done either when you define a SQLJ connection or by using the `setAutoCommit()` method of the underlying JDBC connection object of an existing connection. You can use manual control by disabling the auto-commit flag and using SQLJ `COMMIT` and `ROLLBACK` statements.

Enabling auto-commit may be more convenient, but gives you less control. For example, you have no option to roll back changes. In addition, some SQLJ or JDBC features are incompatible with auto-commit mode. For example, you must disable the auto-commit flag for update batching or `SELECT FOR UPDATE` syntax to work properly.

#### 4.5.3 Specifying Auto-Commit as You Define a Connection

When you use the `Oracle.connect()` or `Oracle.getConnection()` method to create a `DefaultContext` instance and define a connection, the auto-commit flag is set to `false` by default. However, there are signatures of these methods that enable you to set this flag explicitly. The auto-commit flag is always the last parameter.

The following is an example of instantiating `DefaultContext` and using the default `false` setting for auto-commit mode:

    Oracle.getConnection
       ("jdbc:oracle:thin:@localhost:5221/myservice", "HR", "hr");

Alternatively, you can specify a `true` setting as follows:

    Oracle.getConnection
       ("jdbc:oracle:thin:@localhost:5221/myservice", "HR", "hr", true);

**See Also:**

"More About the Oracle Class"

If you use a constructor to create a connection context instance, either of `DefaultContext` or of a declared connection context class, then you must specify the auto-commit setting. Again, it is the last parameter, as in the following example:

    DefaultContext ctx = new DefaultContext
       ("jdbc:oracle:thin:@localhost:5221/myservice", "HR", "hr", false);

**See Also:**

"More About the DefaultContext Class"

If you have reason to create a JDBC `Connection` instance directly, then the auto-commit flag is set to `true` by default if your program runs on a client, or `false` by default if it runs in the server. You cannot specify an auto-commit setting when you create a JDBC `Connection` instance directly, but you can use the `setAutoCommit()` method to alter the setting.

**Note:**

Auto-commit functionality is not supported by the JDBC server-side internal driver.

#### 4.5.4 Modifying Auto-Commit in an Existing Connection

There is typically no reason to change the auto-commit flag setting for an existing connection, but you can if you desire. You can do this by using the `setAutoCommit()` method of the underlying JDBC connection object.

You can retrieve the underlying JDBC connection object by using the `getConnection()` method of any SQLJ connection context instance, whether it is an instance of the `DefaultContext` class or of a connection context class that you declared.

You can accomplish these two steps at once, as follows:

    ctx.getConnection().setAutoCommit(false);

or:

    ctx.getConnection().setAutoCommit(true);

In these examples, `ctx` is a SQLJ connection context instance.

**Note:**

Do not alter the auto-commit setting in the middle of a transaction.

#### 4.5.5 Using Manual COMMIT and ROLLBACK

If you disable the auto-commit flag, then you must manually commit any data updates. To commit any changes that have been executed since the last `COMMIT` operation, use the SQLJ `COMMIT` statement, as follows:

    #sql { COMMIT };

To roll back any changes that have been executed since the last `COMMIT` operation, use the SQLJ `ROLLBACK` statement, as follows:

    #sql { ROLLBACK };

**Note:**

- Do not use the `COMMIT` and `ROLLBACK` commands when auto-commit is enabled. This will result in unspecified behavior, or even SQL exceptions could be raised.

- You can also roll back to a specified savepoint. Refer to "Using Savepoints".

- All DDL statements in Oracle SQL syntax include an implicit `COMMIT` operation. There is no special SQLJ functionality in this regard. Such statements follow standard Oracle SQL rules.

- If auto-commit mode is off and you close a connection context instance from a client application, then any changes since your last `COMMIT` will be committed, unless you close the connection context instance with `KEEP_CONNECTION`. Refer to "[Closing Shared Connections](advanced-language-features.md)" for more information.

#### 4.5.6 Effect of Commits and Rollbacks on Iterators and Result Sets

`COMMIT` and `ROLLBACK` operations do not affect open result sets and iterators. The result sets and iterators will still be open. Usually, all that is relevant to their content is the state of the database at the time of execution of the `SELECT` statements that populated them.

**Note:**

An exception to this is if you declared an iterator class with `sensitivity=SENSITIVE`. In this case, changes to the underlying result set may be seen whenever the iterator is scrolled outside of its window size. For more information about scrollable iterators, refer to "[Scrollable Iterators](advanced-language-features.md)". For more information about the underlying scrollable result sets, refer to the[ Oracle Database JDBC Developer's Guide](../jjdbc/resultset.md).

This also applies to `UPDATE`, `INSERT`, and `DELETE` statements that are executed after the `SELECT` statements. Execution of these statements does not affect the contents of open result sets and iterators.

Consider a situation where you `SELECT`, then `UPDATE`, and then `COMMIT`. A nonsensitive result set or iterator populated by the `SELECT` statement will be unaffected by the `UPDATE` and `COMMIT`.

As a further example, consider a situation where you `UPDATE`, then `SELECT`, and then `ROLLBACK`. A nonsensitive result set or iterator populated by the `SELECT` will still contain the updated data, regardless of the subsequent `ROLLBACK`.

#### 4.5.7 Using Savepoints

The JDBC 3.0 specification added support for savepoints. A savepoint is a defined point in a transaction that you can roll back to, if desired, instead of rolling back the entire transaction. The savepoint is the point in the transaction where the `SAVEPOINT` statement appears.

In Oracle9i Database Release 2 (9.2), SQLJ first included Oracle-specific syntax to support savepoints. In Oracle Database 12c Release 2 (12.2), SQLJ adds support for ISO SQLJ standard savepoint syntax.

##### Support for ISO SQLJ Standard Savepoint Syntax

In ISO SQLJ standard syntax, use a string literal in a `SAVEPOINT` statement to designate a name for a savepoint. This can be done as follows:

    #sql { SAVEPOINT savepoint1 };

If you want to roll back changes to that savepoint, then you can refer to the specified name later in a `ROLLBACK TO` statement, as follows:

    #sql { ROLLBACK TO savepoint1 };

Use a `RELEASE SAVEPOINT` statement if you no longer need the savepoint:

    #sql { RELEASE SAVEPOINT savepoint1 };

Savepoints are saved in the SQLJ execution context, which has methods that parallel the functionality of these three statements.

**See Also:**

"[Savepoint Methods](advanced-language-features.md)"

Because any `COMMIT` operation ends the transaction, this also releases all savepoints of the transaction.

##### Oracle SQLJ Savepoint Syntax

In addition to the ISO SQLJ standard syntax, the following Oracle-specific syntax for savepoints is supported. Note that the Oracle syntax uses string host expressions, rather than string literals.

You can set a savepoint as follows:

    #sql { SET SAVEPOINT :savepoint };

The host expression, `savepoint` in this example, is a variable that specifies the name of the savepoint as a Java `String`.

You can roll back to a savepoint as follows:

    #sql { ROLLBACK TO :savepoint };

To release a savepoint, use the following SQLJ statement:

    #sql { RELEASE :savepoint };

**Note:**

Oracle-specific syntax will continue to be supported for backward compatibility. Note the following differences between Oracle syntax and ISO SQLJ standard syntax:

- Oracle syntax takes string variables rather than string literals.

- Oracle syntax uses `SET SAVEPOINT` instead of `SAVEPOINT`.

- Oracle syntax uses `RELEASE` instead of `RELEASE SAVEPOINT`.

### 4.6 Summary: First Steps in SQLJ Code

The best way to summarize the SQLJ executable statement features and functionality discussed to this point is by examining short but complete programs. This section presents two such examples.

The first example, presented one step at a time and then again in its entirety, uses a `SELECT INTO` statement to perform a single-row query of two columns from a table of employees. If you want to run the example, ensure that you change the parameters in the `connect.properties` file to settings that will let you connect to an appropriate database.

The second example, slightly more complicated, will make use of a SQLJ iterator for a multi-row query.

#### Import Required Classes

Import any JDBC or SQLJ packages you will need. You will need at least some of the classes in the `java.sql` package:

    import java.sql.*;

You may not need all the `java.sql` package. Key classes are `java.sql.SQLException` and any classes that you refer to explicitly. For example, `java.sql.Date` and `java.sql.ResultSet`.

You will need the following package for the `Oracle` class, which you typically use to instantiate `DefaultContext` objects and establish your default connection:

    import oracle.sqlj.runtime.*;

If you will be using any SQLJ run-time classes directly in your code, then import the following packages:

    import sqlj.runtime.*;
    import sqlj.runtime.ref.*;

However, even if your code does not use any SQLJ run-time classes directly, it will be sufficient to have them in the `CLASSPATH`.

Key run-time classes include `ResultSetIterator` and `ExecutionContext` in the `sqlj.runtime` package and `DefaultContext` in the `sqlj.runtime.ref` package.

#### Register JDBC Drivers and Set Default Connection

Declare the `SimpleExample` class with a constructor that uses the static `Oracle.connect()` method to set the default connection. This also registers Oracle JDBC drivers.

This uses a signature of `connect()` that takes the URL, user name, and password from the `connect.properties` file. An example of this file is in the directory `ORACLE_HOME``/sqlj/demo` and also in "[Set Up the Run-Time Connection](getting-started.md)".

    public class SimpleExample {

      public SimpleExample() throws SQLException {
        // Set default connection (as defined in connect.properties).
        Oracle.connect(getClass(), "connect.properties");
      }

#### Set Up Exception Handling

Create a `main()` that calls the `SimpleExample` constructor and then sets up a `try/catch` block to handle any SQL exceptions thrown by the `runExample()` method, which performs the real work of this application:

    ...
    public static void main (String [] args) {

       try {
          SimpleExample o1 = new SimpleExample();
          o1.runExample();
       }
       catch (SQLException ex) {
          System.err.println("Error running the example: " + ex);
       }
    }
    ...

You can also use a `try/catch` block inside a `finally` clause when you close the connection, presuming the `finally` clause is not already inside a `try/catch` block in case of SQL exceptions:

    finally
    {
       try { Oracle.close(); } catch(SQLException ex) {...}
    }

#### Set Up Host Variables, Execute SQLJ Clause, Process Results

Create a `runExample()` method that performs the following:

1.  Throws any SQL exceptions to the `main()` method for processing.

2.  Declares Java host variables.

3.  Executes a SQLJ clause that binds the Java host variables into an embedded `SELECT` statement and selects the data into the host variables.

4.  Prints the results.

The code for this method is as follows:

    void runExample() throws SQLException {

         System.out.println( "Running the example--" );

         // Declare two Java host variables--
         Float salary;
         String empname;

         // Use SELECT INTO statement to execute query and retrieve values.
          #sql { SELECT first_name, salary INTO :empname, :salary FROM employees
                 WHERE employee_id = 7499 };

         // Print the results--
         System.out.println("Name is " + empname + ", and Salary is " + salary);
      }
    }    // Closing brace of SimpleExample class

This example declares `salary` and `empname` as Java host variables. The SQLJ clause then selects data from the `first_name` and `salary` columns of the `employees` table and places the data into the host variables. Finally, the values of `salary` and `empname` are printed.

Note that this `SELECT` statement could select only one row of the `employees` table, because the `employee_id` column in the `WHERE` clause is the primary key of the table.

#### Example of Single-Row Query using SELECT INTO

This section presents the entire `SimpleExample` class from the previous step-by-step sections. Because this is a single-row query, no iterator is required.

    // Import SQLJ classes:
    import sqlj.runtime.*;
    import sqlj.runtime.ref.*;
    import oracle.sqlj.runtime.*;

    // Import standard java.sql package:
    import java.sql.*;

    public class SimpleExample {

      public SimpleExample() throws SQLException {
        // Set default connection (as defined in connect.properties).
        Oracle.connect(getClass(), "connect.properties");
      }

      public static void main (String [] args) throws SQLException {

        try {
          SimpleExample o1 = new SimpleExample();
          o1.runExample();
        }
        catch (SQLException ex) {
          System.err.println("Error running the example: " + ex);
        }
      }

      finally
      {
         try { Oracle.close(); } catch(SQLException ex) {...}
      }

      void runExample() throws SQLException {

         System.out.println( "Running the example--" );

         // Declare two Java host variables--
         Float salary;
         String empname;

         // Use SELECT INTO statement to execute query and retrieve values.
            #sql { SELECT first_name, salary INTO :empname, :salary FROM employees
                  WHERE employee_id = 7499 };

         // Print the results--
         System.out.println("Name is " + empname + ", and Salary is " + salary);
      }
    }

#### Set Up a Named Iterator

This example builds on the previous example by adding a named iterator and using it for a multiple-row query.

First, declare the iterator class. Use object types `Integer` and `Float`, instead of primitive types `int` and `float`, wherever there is the possibility of `NULL` values.

    #sql iterator EmpRecs(
          int empno,       // This column cannot be null, so int is OK.
                           // (If null is possible, use Integer.)
          String ename,
          String job,
          Integer mgr,
          Date hiredate,
          Float sal,
          Float comm,
          int deptno);

Next, instantiate the `EmpRecs` class and populate it with query results.

    EmpRecs employees;

    #sql employees = { SELECT employee_id, first_name, job_id, manager_id, hire_date,
                       salary, commission_pct, department_tno FROM employees };

Then, use the `next()` method of the iterator to print the results.

        while (employees.next())  {
          System.out.println( "Name:       " + employees.first_name() );
          System.out.println( "EMPNO:      " + employees.employee_id() );
          System.out.println( "Job:        " + employees.job_id() );
          System.out.println( "Manager:    " + employees.manager_id) );
          System.out.println( "Date hired: " + employees.hire_date() );
          System.out.println( "Salary:     " + employees.salary() );
          System.out.println( "Commission: " + employees.commission_pct() );
          System.out.println( "Department: " + employees.department_no() );
          System.out.println();
        }

Finally, close the iterator.

    employees.close();

#### Example of Multiple-Row Query Using Named Iterator

This example uses a named iterator for a multiple-row query that selects several columns of data from a table of employees.

Apart from use of the named iterator, this example is conceptually similar to the previous single-row query example.

    // Import SQLJ classes:
    import sqlj.runtime.*;
    import sqlj.runtime.ref.*;
    import oracle.sqlj.runtime.*;

    // Import standard java.sql package:
    import java.sql.*;

    // Declare a SQLJ iterator.
    // Use object types (Integer, Float) for mgr, sal, And comm rather
    // than primitive types to allow for possible null selection.

    #sql iterator EmpRecs(
          int empno,       // This column cannot be null, so int is OK.
                           // (If null is possible, Integer is required.)
          String ename,
          String job,
          Integer mgr,
          Date hiredate,
          Float sal,
          Float comm,
          int deptno);

    // This is the application class.
    public class EmpDemo1App {

       public EmpDemo1App() throws SQLException {
          // Set default connection (as defined in connect.properties).
          Oracle.connect(getClass(), "connect.properties");
       }

      public static void main(String[] args) {

        try {
          EmpDemo1App app = new EmpDemo1App();
          app.runExample();
        }
        catch( SQLException exception ) {
          System.err.println( "Error running the example: " + exception );
        }
      }

      finally
      {
         try { Oracle.close(); } catch(SQLException ex) {...}
      }

      void runExample() throws SQLException  {
        System.out.println("\nRunning the example.\n" );

        // The query creates a new instance of the iterator and stores it in
        // the variable 'employees' of type 'EmpRecs'.  SQLJ translator has
        // automatically declared the iterator so that it has methods for
        // accessing the rows and columns of the result set.

        EmpRecs employees;

        #sql employees = { SELECT employee_id, first_name, job_id, manager_id, hire_date,
                           salary, commission_pct, department_no FROM employees };

        // Print the result using the iterator.

        // Note how the next row is accessed using method 'next()', and how
        // the columns can be accessed with methods that are named after the
        // actual database column names.

        while (employees.next())  {
          System.out.println( "Name:       " + employees.first_name() );
          System.out.println( "EMPNO:      " + employees.employee_id() );
          System.out.println( "Job:        " + employees.job_id() );
          System.out.println( "Manager:    " + employees.manager_id() );
          System.out.println( "Date hired: " + employees.hire_date() );
          System.out.println( "Salary:     " + employees.salary() );
          System.out.println( "Commission: " + employees.commission_pct() );
          System.out.println( "Department: " + employees.department_no() );
          System.out.println();
        }

        // You must close the iterator when it's no longer needed.
        employees.close() ;
      }
    }

### 4.7 Oracle-Specific Code Generation (No Profiles)

Throughout this manual there is general and standard discussion of the SQLJ run-time layer and SQLJ profiles. However, the Oracle SQLJ implementation, by default, generates Oracle-specific code with direct calls to Oracle JDBC driver instead of generating ISO SQLJ standard code that calls the SQLJ run time. With Oracle-specific code generation, there are no profile files, and the role of the SQLJ run-time layer is greatly reduced during program execution. Oracle-specific code supports all Oracle-specific extended features.

Code generation is determined through the SQLJ translator `-codegen` option. The default setting for Oracle-specific code generation is `-codegen=oracle`. Alternatively, you can set `-codegen=iso` for code generation according to the ISO SQLJ standard.

This section covers the following topics:

- Code Considerations and Limitations with Oracle-Specific Code Generation

- SQLJ Usage Changes with Oracle-Specific Code Generation

- Advantages and Disadvantages of Oracle-Specific Code Generation

#### 4.7.1 Environment Requirements for Oracle-Specific Code Generation

Be aware of the following requirements of your environment if you use Oracle-specific code generation:

- You must use an Oracle11g or later version of JDBC driver, because Oracle-specific code generation requires JDBC statement caching functionality.

- The generic SQLJ run time library, `runtime`, is not supported for Oracle-specific code generation. You must have one of the following Oracle SQLJ run time libraries in the `CLASSPATH`:

  - `runtime12.jar`

  - `runtime12ee.jar`

  **See Also:**

  "[Requirements for Using the Oracle SQLJ Implementation](getting-started.md)"

#### 4.7.2 Code Considerations and Limitations with Oracle-Specific Code Generation

When coding a SQLJ application where Oracle-specific code generation will be used, be aware of the following programming considerations and restrictions:

- To use a nondefault statement cache size, you must include appropriate method calls in your code, because Oracle customizer `stmtcache` option is unavailable.

- Do not mix Oracle-specific generated code with ISO SQLJ standard generated code in the same application. However, if Oracle-specific code and ISO SQLJ standard code must share the same connection, do one of the following:

  - Ensure that the Oracle-specific code and ISO standard code use different SQLJ execution context instances. Refer to "[Execution Contexts](advanced-language-features.md)" for information about SQLJ execution contexts.

  - Place a transaction boundary, that is, as a manual `COMMIT` or `ROLLBACK` statement, between the two kinds of code.

  This limitation regarding mixing code is especially significant for server-side code, because all Java code running in a given session uses the same JDBC connection and SQLJ connection context.

- Do not rely on side effects in parameter expressions when values are returned from the database. Oracle-specific code generation does not create temporary variables for evaluation of `OUT` parameters, `IN OUT` parameters, `SELECT INTO` variables, or return arguments on SQL statements.

  For example, avoid statements such as the following:

      #sql { SELECT * FROM EMPLOYEES INTO :(x[i++]), :(f_with_sideffect()[i++]),
                                    :(a.b[i]) };

  or:

      #sql x[i++] = { VALUES f(:INOUT (x[i++]), :OUT (f_with_sideffect())) };

  Evaluation of arguments is performed in place in the generated code. This may result in different behavior than when evaluation is according to ISO SQLJ standards.

- Type maps for Oracle object functionality assumes that the corresponding Java classes implement the `java.sql.SQLData` interface. If you use type maps for Oracle object functionality, then your iterator declarations and connection context declarations must specify the same type maps. Specify this through the `with` clause.

  For example, if you declare a connection context class as follows:

      #sql context TypeMapContext with (typeMap="MyTypeMap");

  and you populate an iterator instance from a SQLJ statement that uses an instance of this connection context class, as follows:

      TypeMapContext tmc = new TypeMapContext(...);
      ...
      MyIterator it;
      #sql [tmc] it = ( SELECT pers, addr FROM tab WHERE ...);

  then the iterator declaration is required to have specified the same type map, as follows:

      #sql iterator MyIterator with (typeMap="MyTypeMap")
                    (Person pers, Address addr);

  **See Also:**

  "[Custom Java Class Requirements](objects-collections-and-OPAQUE-types.md)" and "[Declaration WITH Clause](basic-language-features.md)"

  **Note:**

  The reason for this restriction is that with Oracle-specific code generation, all iterator getter methods are fully generated as Oracle JDBC calls during translation. To generate the proper calls, the SQLJ translator must know whether an iterator will be used with a particular type map.

#### 4.7.3 SQLJ Usage Changes with Oracle-Specific Code Generation

Some options that were previously available only as Oracle customizer options are useful with Oracle-specific code generation as well. Because profile customization is not applicable with Oracle-specific code generation, these options have been made available through other means.

To alter the statement cache size or disable statement caching when generating Oracle-specific code, use method calls in your code instead of using the customizer `stmtcache` option. The `sqlj.runtime.ref.DefaultContext` class, as well as any connection context class you declare, now has the following static methods:

- `setDefaultStmtCacheSize(int)`

- `int getDefaultStmtCacheSize()`

It also has the following instance methods:

- `setStmtCacheSize(int)`

- `int getStmtCacheSize()`

By default, statement caching is enabled.

**See Also:**

"[Statement Caching](performance-and-debugging.md)"

In addition, the following options are available as front-end Oracle SQLJ translator options as well as Oracle customizer options:

- `-optcols`: Enable iterator column type and size definitions to optimize performance.

- `-optparams`: Enable parameter size definitions to optimize JDBC resource allocation. This option is used in conjunction with `optparamdefaults`.

- `-optparamdefaults`: Set parameter size defaults for particular data types. This option is used in conjunction with `optparams`.

- `-fixedchar`: Enable `CHAR` comparisons with blank padding for `WHERE` clauses.

**See Also:**

"[Options for Code Generation\_ Optimizations\_ and CHAR Comparisons](translator-command-line-and-options.md)"

Be aware of the following:

- Use the `-optcols` option only if you are using online semantics-checking, where you have used the SQLJ translator `-user`, `-password`, and `-url` options appropriately to request a database connection during translation.

- The functionality of the `-optcols`, `-optparams`, and `-optparamdefaults` options, including default values, is the same as for the corresponding customizer options.

#### 4.7.4 Advantages and Disadvantages of Oracle-Specific Code Generation

Oracle-specific code generation offers following advantages over ISO standard code generation:

- Applications run more efficiently. The code calls JDBC application programming interfaces (APIs) directly, placing run-time performance directly at the JDBC level. The role of the intermediate SQLJ run-time layer is greatly reduced during program execution.

- Applications are smaller in size.

- No profile files (`.ser`) are produced. This is especially convenient if you are loading a translated application into the database or porting it to another system, because there are fewer components.

- Translation is faster, because there is no profile customization step.

- During execution, Oracle SQLJ run time and Oracle JDBC driver use the same statement cache resources, so partitioning resources between the two is unnecessary.

- Having the SQL-specific information appear in the Java class files instead of in separate profile files avoids potential security issues.

- You need not have to rewrite your code to take advantage of possible future Oracle JDBC performance enhancements, such as enhancements being considered for execution of static SQL code. Future releases of Oracle SQLJ translator will handle this automatically.

- The use of Java reflection at run time is eliminated, and thus, provides full portability to browser environments.

However. there are a few disadvantages:

- Oracle-specific generated code may not be portable to generic JDBC platforms.

- Profile-specific functionality is not available. For example, you cannot perform customizations at a later date to use Oracle customizer harness `-debug`, `-verify`, and `-print` options.

  **See Also:**

  "[Customizer Harness Options for Connections](appendix.md)" and "[AuditorInstaller Customizer for Debugging](appendix.md)"

### 4.8 ISO Standard Code Generation

This section covers the following topics:

- Environment Requirements for ISO Standard Code Generation

- SQLJ Translator and SQLJ Run Time

- SQLJ Profiles

- SQLJ Translation Steps

- Summary of Translator Input and Output

- SQLJ Run-Time Processing

- Deployment Scenarios

#### 4.8.1 Environment Requirements for ISO Standard Code Generation

The Oracle SQLJ implementation, by default, generates Oracle-specific code with direct calls to Oracle JDBC driver instead of generating ISO standard code that calls the SQLJ run time. The following is a typical environment setup for ISO standard code generation:

- SQLJ code generation: `-codegen=iso`

- SQLJ translation library: `translator.jar`

- SQLJ run-time library: `runtime12.jar` with JDK 6 or JDK 7, and Oracle Database 12c Release 2 (12.2)

- JDBC drivers: Oracle Database 12c Release 2 (12.2)`ojdbc6.jar` or `ojdbc7.jar`

- JDK version: JDK 6 or JDK 7

#### 4.8.2 SQLJ Translator and SQLJ Run Time

The following section describes the differences in Oracle SQLJ implementation in case of ISO standard code generation:

- SQLJ translator: Along with the `.java` file, the translator also produces one or more SQLJ profiles for ISO standard code generation. These profiles contain information about the embedded SQL operations. SQLJ then automatically invokes a Java compiler to produce `.class` files from the `.java` file.

  **See Also:**

  "[SQLJ Translator Functionality](intro-to-SQLJ.md)"

- SQLJ run time: For ISO standard code generation, the SQLJ run time implements the desired actions of the SQL operations by accessing the database using a JDBC driver. The generic ISO SQLJ standard does not require the SQLJ run time to use a JDBC driver to access the database.

  **See Also:**

  "[SQLJ Run Time](intro-to-SQLJ.md)"[SQLJ Run Time](translator-run-time-functionality.md)

In addition to the translator and run time, there is a component known as the customizer that plays a role. A customizer tailors SQLJ profiles for a particular database implementation and vendor-specific features and data types. By default, for ISO standard code, the SQLJ front end invokes an Oracle customizer to tailor your profiles for Oracle Database instance and Oracle-specific features and data types.

When you use Oracle customizer during translation, your application will require the SQLJ run time and an Oracle JDBC driver when it runs.

**Note:**

Since Oracle Database 10g Release 1, only Oracle JDBC drivers are supported with SQLJ.

#### 4.8.3 SQLJ Profiles

With ISO standard code generation, SQLJ profiles are serialized Java resources or classes generated by the SQLJ translator, which contain details about the embedded SQL statements. The translator creates these profiles. Then, depending on the translator option settings, it either serializes the profiles and puts them into binary resource files or puts them into `.class` files.

This section covers the following topics:

- Overview of Profiles

- Binary Portability

##### 4.8.3.1 Overview of Profiles

SQLJ profiles are used in ISO standard code for implementing the embedded SQL operations in SQLJ executable statements. Profiles contain information about the SQL operations and the types and modes of data being accessed. A profile consists of a collection of entries, where each entry maps to one SQL operation. Each entry fully specifies the corresponding SQL operation, describing each of the parameters used in processing this instruction.

SQLJ generates a profile for each connection context class in your application, where each connection context class corresponds to a particular set of SQL entities you use in your database operations. There is one default connection context class, and you can declare additional classes. The ISO SQLJ standard requires that the profiles be of standard format and content. Therefore, for your application to use vendor-specific extended features, your profiles must be customized. By default, this occurs automatically, with your profiles being customized to use Oracle-specific extended features.

Profile customization enables vendors to add value in the following ways:

- Vendors can support their own specific data types and SQL syntax. For example, Oracle customizer maps standard JDBC `PreparedStatement` method calls in translated SQLJ code to `OraclePreparedStatement` method calls, which provide support for Oracle type extensions.

- Vendors can improve performance through specific optimizations.

**Note:**

- By default, SQLJ profile file names have the `.ser` extension, but this does not mean that all `.ser` files are profiles. Other serialized objects can use this extension, and a SQLJ program unit can use serialized objects other than its profiles. Optionally, profiles can be converted to `.class` files instead of `.ser` files.

- A SQLJ profile is not produced if there are no SQLJ executable statements in the source code.

##### 4.8.3.2 Binary Portability

SQLJ-generated profile files support binary portability. That is, you can port them as is and use them with other kinds of databases or in other environments, if you have not used vendor-specific data types or features. This is true for generated `.class` files as well.

#### 4.8.4 SQLJ Translation Steps

For ISO standard code generation (`-codegen=iso`), the translator processes the SQLJ source code, converts SQL operations to SQLJ run-time calls, and generates Java output code and one or more SQLJ profiles. A separate profile is generated for each connection context class in the source code, where a different connection context class is typically used for each interrelated set of SQL entities that is used in the operations.

Generated Java code is put into a `.java` output file containing the following:

- Any class definitions and Java code from the `.sqlj` source file

- Class definitions created as a result of the SQLJ iterator and connection context declarations

  **See Also:**

  "[Overview of SQLJ Declarations](basic-language-features.md)"

- A class definition for a specialized class known as the profile-keys class that SQLJ generates and uses in conjunction with the profiles (for ISO standard SQLJ code generation only)

- Calls to the SQLJ run time to implement the actions of the embedded SQL operations

Generated profiles contain information about all the embedded SQL statements in the SQLJ source code, such as actions to take, data types being manipulated, and tables being accessed. When the application is run, the SQLJ run time accesses the profiles to retrieve the SQL operations and passes them to the JDBC driver.

By default, profiles are put into `.ser` serialized resource files, but SQLJ can optionally convert the `.ser` files to `.class` files as part of the translation.

The compiler compiles the generated Java source file and produces Java `.class` files as appropriate. This includes a `.class` file for each class that is defined, each of the SQLJ declarations, and the profile-keys class. The JVM then invokes Oracle customizer or other specified customizer to customize the profiles generated.

**See Also:**

"[Internal Translator Operations](translator-run-time-functionality.md)"

##### General SQLJ Notes

Consider the following when translating and running SQLJ applications for ISO specific code generation:

- Along with compiling existing `.java` files on the command line and making them available for type resolution, as for Oracle-specific code generation, you need to:

  - Customize the existing profiles

  - Customize the Java Archive (JAR) files containing profiles

  **See Also:**

  "[Translator Command Line and Properties Files](translator-command-line-and-options.md)"

- SQLJ generates profiles and the profile-keys class only if your source code includes SQLJ executable statements.

- If you use Oracle customizer during translation, then your application requires Oracle SQLJ run time and an Oracle JDBC driver when it runs, even if your code does not use Oracle-specific features. You can avoid this by specifying `-profile=false` when you translate, to bypass Oracle-specific customization.

#### 4.8.5 Summary of Translator Input and Output

We have seen what the SQLJ translator takes as input, what it produces as output, and where it places its output in case of Oracle-specific code generation. This section covers the same topics for ISO standard code generation:

- Translator Input

- Translator Output

- Output File Locations

**See Also:**

"[Summary of Translator Input and Output](intro-to-SQLJ.md)"

##### 4.8.5.1 Translator Input

Similar to Oracle -specific code generation, the SQLJ translator takes one or more `.sqlj` source files as input, which can be specified on the command line. The name of the main `.sqlj` file is based on the public class it defines, if any, else on the first class it defines.

**See Also:**

"[Translator Input](intro-to-SQLJ.md)"

##### 4.8.5.2 Translator Output

The translation step produces a Java source file for each `.sqlj` file in the application and at least one application profile for ISO standard code generation, presuming the source code uses SQLJ executable statements.

SQLJ generates Java source files and application profiles as follows:

**See Also:**

"[Translator Output](intro-to-SQLJ.md)"

- Similar to Oracle-specific code generation, Java source files are `.java` files with the same base names as the `.sqlj` files.

- The application profile files, if applicable, contain information about the SQL operations of the SQLJ application. There is one profile for each connection class that is used in the application. The profiles have names with the same base name as the main `.sqlj` file and the following extensions:

      _SJProfile0.ser
      _SJProfile1.ser
      _SJProfile2.ser
      ...

  For example, for `MyClass.sqlj` the translator produces:

      MyClass_SJProfile0.ser

  The `.ser` file extension indicates that the profiles are serialized. The `.ser` files are binary files.

  **Note:**

  The `-ser2class` translator option instructs the translator to generate profiles as `.class` files instead of `.ser` files. Other than the file name extension, the naming is the same.

Similar to the compilation step of Oracle-specific code generation, compiling the Java source file into multiple class files generates one `.class` file for each class defined in the `.sqlj` source file. But in case of ISO code generation, a `.class` file is also generated for a class known as the profile-keys class that the translator generates and uses with the profiles to implement the SQL operations. Additional `.class` files are produced if you declare any SQLJ iterators or connection contexts. Also, like Oracle-specific code generation, separate `.class` files are produced for any inner classes or anonymous classes in the code.

**See Also:**

"[Overview of SQLJ Declarations](basic-language-features.md)"

The `.class` files are named as follows:

- Like Oracle-specific code generation, the class file for each class defined consists of the name of the class with the `.class` extension.

- The profile-keys class that the translator generates is named according to the base name of the main `.sqlj` file, plus the following:

      _SJProfileKeys

  So, the class file has the following extension:

      _SJProfileKeys.class

  For example, for `MyClass.sqlj`, the translator together with the compiler produces:

      MyClass_SJProfileKeys.class

- Like Oracle-specific code generation, the translator names iterator classes and connection context classes according to how you declare them.

The customization step alters the profiles but produces no additional output.

**See Also:**

"[Profile Customization (ISO Code Generation)](translator-run-time-functionality.md)"

**Note:**

It is not necessary to reference SQLJ profiles or the profile-keys class directly. This is all handled automatically.

##### 4.8.5.3 Output File Locations

The output file locations are the same for both Oracle-specific code generation and ISO standard code generation.

**See Also:**

"[Output File Locations](intro-to-SQLJ.md)"

#### 4.8.6 SQLJ Run-Time Processing

This section discusses run-time processing for ISO standard code during program execution.

For ISO standard SQLJ applications, the SQLJ run time reads the profiles and creates connected profiles, which incorporate database connections. Then the following occurs each time the application must access the database:

1.  SQLJ-generated application code uses methods in a SQLJ-generated profile-keys class to access the connected profile and read the relevant SQL operations. There is a mapping between SQLJ executable statements in the application and SQL operations in the profile.

2.  The SQLJ-generated application code calls the SQLJ run time, which reads the SQL operations from the profile.

3.  The SQLJ run time calls the JDBC driver and passes the SQL operations to the driver.

4.  The SQLJ run time passes any input parameters to the JDBC driver.

5.  The JDBC driver executes the SQL operations.

6.  If any data is to be returned, then the database sends it to the JDBC driver, which sends it to the SQLJ run time for use by your application.

**Note:**

Passing input parameters can also be referred to as binding input parameters or binding host expressions. The terms host variables, host expressions, bind variables, and bind expressions are all used to describe Java variables or expressions that are used as input or output for SQL operations.

#### 4.8.7 Deployment Scenarios

We have discussed how to run Oracle-specific SQLJ code in the following scenarios:

- From an applet

- In the server (optionally running the SQLJ translator in the server as well)

There are a few considerations that you need to make while running your ISO standard code from an applet:

**See Also:**

"[Alternative Deployment Scenarios](intro-to-SQLJ.md)"

- You must package all the SQLJ run-time packages with your applet. The packages are:

      sqlj.runtime
      sqlj.runtime.ref
      sqlj.runtime.profile
      sqlj.runtime.profile.ref
      sqlj.runtime.error

  Also package the following if you used Oracle customization:

      oracle.sqlj.runtime
      oracle.sqlj.runtime.error

  These packages are included with your Oracle installation in one of several run-time libraries in the `ORACLE_HOME``/lib` directory.

  **See Also:**

  "[Requirements for Using the Oracle SQLJ Implementation](getting-started.md)"

- Some browsers, such as Netscape Navigator 4.x, do not support resource files with a `.ser` extension, which is the extension used by the SQLJ serialized object files that are used for profiles. However, the Sun Microsystems Java plug-in supports `.ser` files.

  Alternatively, if you do not want to use the plug-in, then the Oracle SQLJ implementation offers the `-ser2class` option to convert `.ser` files to `.class` files during translation.

  **Note:**

  This consideration does not apply to the default Oracle-specific code generation, where no profiles are produced.

- Applets using Oracle-specific features require Oracle SQLJ run time to work. Oracle SQLJ run time consists of the classes in the SQLJ run-time library file under `oracle.sqlj.*`. Oracle SQLJ `runtime.jar` library requires the Java Reflection API, `java.lang.reflect.*`. Most browsers do not support the Reflection API or impose security restrictions, but the Sun Microsystems Java plug-in provides support for the Reflection API.

  With ISO standard code generation, the following SQLJ language features always require the Java Reflection API, regardless of the version of the SQLJ run time you are using:

  - The `CAST` statement

  - `REF CURSOR` parameters or `REF CURSOR` columns being retrieved from the database as instances of a SQLJ iterator

  - Retrieval of `java.sql.Ref`, `Struct`, `Array`, `Blob`, or `Clob` objects

  - Retrieval of SQL objects as instances of Java classes implementing the `oracle.sql.ORAData` or `java.sql.SQLData` interfaces

    **Note:**

    - An exception to the preceding is if you use SQLJ in a mode that is fully compatible with ISO. That is, if you use SQLJ in an environment that complies with J2EE and you translate and run your program with the SQLJ `runtime12ee.jar` library, and you employ connection context type maps as specified by ISO. In this case, instances of `java.sql.Ref`, `Struct`, `Array`, `Blob`, `Clob`, and `SQLData` are being retrieved without the use of reflection.

    - If you use Oracle-specific code generation, then you will eliminate the use of reflection in all of the instances listed.

### 4.9 Oracle-Specific Code Generation Versus ISO Standard Code Generation

The Oracle SQLJ implementation provides the option of Oracle-specific code generation, where Oracle JDBC calls are generated directly in the code. This is the default behavior. In the case of Oracle-specific code generation, you must be aware of the following:

- There are no profile files, and therefore, there is no customization step during translation.

- At run time, SQL operations do not have to go through the SQLJ run-time layer, because JDBC calls, instead of the SQLJ run-time calls, are directly generated in the translated code.

### 4.10 Requirements and Restrictions for Naming

There are four areas to consider in discussing naming requirements, naming restrictions, and reserved words:

- The Java namespace, including additional restrictions imposed by SQLJ on the naming of local variables and classes

- The SQLJ namespace

- The SQL namespace

- Source file names

This section covers the following topics:

- Java Namespace: Local Variable and Class Naming Restrictions

- SQLJ Namespace

- SQL Namespace

- File Name Requirements and Restrictions

#### 4.10.1 Java Namespace: Local Variable and Class Naming Restrictions

The Java namespace applies to all standard Java statements and declarations, including the naming of Java classes and local variables. All standard Java naming restrictions apply, and you should avoid the use of Java reserved words.

In addition, SQLJ places minor restrictions on the naming of local variables and classes.

**Note:**

Naming restrictions particular to host variables are discussed in "[Restrictions on Host Expressions](basic-language-features.md)".

##### Local Variable Naming Restrictions

Some of the functionality of the SQLJ translator results in minor restrictions in naming local variables. The SQLJ translator replaces each SQLJ executable statement with a statement block, where the SQLJ executable statement is of the standard syntax:

    #sql { SQL operation };

SQLJ may use temporary variable declarations within a generated statement block. The name of any such temporary variables will include the following prefix:

     __sJT_

**Note:**

There are two underscores at the beginning and one at the end.

The following declarations are examples of those that might occur in a SQLJ-generated statement block:

    int __sJT_index;
    Object __sJT_key;
    java.sql.PreparedStatement __sJT_stmt;

The string `__sJT_` is a reserved prefix for SQLJ-generated variable names. SQLJ programmers must not use this string as a prefix for the following:

- Names of variables declared in blocks that include executable SQL statements

- Names of parameters to methods that contain executable SQL statements

- Names of fields in classes that contain executable SQL statements, or whose subclasses or enclosed classes contain executable SQL statements

##### Class Naming Restrictions

Be aware of the following minor restrictions in naming classes in SQLJ applications:

- You must not declare class names that may conflict with SQLJ internal classes. In particular, a top-level class cannot have a name of the following form, where `a` is the name of an existing class in the SQLJ application:

      a_SJb

  where, `a` and `b` are legal Java identifiers.

  For example, if your application class is `Foo` in file `Foo.sqlj`, then SQLJ generates a profile-keys class called `Foo_SJProfileKeys`. Do not declare a class name that conflicts with this.

- A class containing SQLJ executable statements must not have a name that is the same as the first component of the name of any package that includes a Java type used in the application. Examples of class names to avoid are `java`, `sqlj`, and `oracle` (case-sensitive). As another example, if your SQLJ statements use host variables whose type is `abc.def.MyClass`, then you cannot use `abc` as the name of the class that uses these host variables.

  To avoid this restriction, follow Java naming conventions recommending that package names start in lowercase and class names start in uppercase.

#### 4.10.2 SQLJ Namespace

The SQLJ namespace refers to `#sql` class declarations and the portion of `#sql` executable statements outside the curly braces.

**Note:**

Restrictions particular to the naming of iterator columns are discussed in "[Using Named Iterators](basic-language-features.md)".

Avoid using the following SQLJ reserved words as class names for declared connection context classes or iterator classes, in `with` or `implements` clauses, or in iterator column type declaration lists:

- `iterator`

- `context`

- `with`

For example, do not have an iterator class or instance called `iterator` or a connection context class or instance called `context`.

However, note that it is permissible to have a stored function return variable whose name is any of these words.

#### 4.10.3 SQL Namespace

The SQL namespace refers to the portion of a SQLJ executable statement inside the curly braces. Standard SQL naming restrictions apply here.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/Syntax-for-Schema-Objects-and-Parts-in-SQL-Statements.md)

However, note that host expressions follow rules of the Java namespace, not the SQL namespace. This applies to the name of a host variable and to everything between the outer parentheses of a host expression.

#### 4.10.4 File Name Requirements and Restrictions

SQLJ source files have the `.sqlj` file name extension. If the source file declares a public class (maximum of one), then the base name of the file must match the name of this class (case-sensitive). If the source file does not declare a public class, then the file name must still be a legal Java identifier, and it is recommended that the file name match the name of the first defined class.

For example, if you define the public class `MySource` in your source file, then your file name must be:

    MySource.sqlj

**Note:**

These file naming requirements follow the Java Language Specification (JLS) and are not SQLJ-specific. These requirements do not directly apply in Oracle Database 12c Release 2 (12.2), but it is still advisable to adhere to them.

### 4.11 Considerations for SQLJ in the Middle Tier

There are special considerations if you run SQLJ in the middle tier, such as in an Oracle9i Application Server Containers for J2EE (OC4J) environment.

Oracle JDBC drivers provide Oracle-specific interfaces in the `oracle.jdbc` package. The Oracle SQLJ libraries `runtime12.jar` and `runtime12ee.jar` make full use of these interfaces, but these libraries are not compatible with Oracle JDBC implementations prior to Oracle9i Application Server.

In Oracle9i Application Server, connections are established through data sources, which typically return instances of the `oracle.jdbc.OracleConnection` interface instead of the older `oracle.jdbc.driver.OracleConnection` class. This is necessary for certain connection functionality, such as distributed transactions (XA). To support such features, connection objects must implement the new interface.

This has the following consequences, relevant in an Oracle9i Application Server middle-tier environment, or any situation where data sources are used:

- For maximum portability and flexibility of your code, use `oracle.jdbc.OracleXXX` types instead of `oracle.jdbc.driver.OracleXXX` types.

- For custom Java types (typically for SQL objects and collections), implement `oracle.sql.ORAData`.

- Do not use the SQLJ `runtime` library. Use `runtime12` or `runtime12ee` instead (depending on your environment). The run time library is backward compatible with older JDBC drivers, such as those in Oracle8i Database release 8.1.7, so supports the `oracle.jdbc.driver.OracleXXX` types, not the `oracle.jdbc.OracleXXX` types.

  However, if you must use the `runtime` library for some reason, then set the option `-profile=false` during translation. In this case, your program will not use Oracle-specific customization and, therefore, will not fail if passed an `oracle.jdbc.OracleConnection` instance instead of an `oracle.jdbc.driver.OracleConnection` instance. In this circumstance, Oracle-specific features will not be supported.

To facilitate management of connections obtained through data sources and connection JavaBeans (for SQLJ JavaServer Pages), the Oracle SQLJ implementation provides a number of APIs in the `runtime12ee` library.

For general information about SQLJ support for data sources and connection JavaBeans, refer to the following sections:

- "[Standard Data Source Support](advanced-language-features.md)"

- "[SQLJ-Specific Data Sources](advanced-language-features.md)"

- "[SQLJ-Specific Connection JavaBeans for JavaServer Pages](advanced-language-features.md)"
