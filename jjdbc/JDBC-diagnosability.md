The diagnosabilty features of Oracle Database 12c Release 1 (12.1) enable you to diagnose problems in the applications that use Oracle JDBC drivers and the problems in the drivers themselves. They also reduce the effort required to develop and maintain Java applications that access an Oracle Database instance using Oracle JDBC drivers.

Oracle JDBC drivers provide the following diagnosabilty features that enable users to identify and fix problems in their JDBC applications:

- Logging Feature of Oracle JDBC Drivers

- Diagnosability Management

**Note:**

The diagnosability features of the JDBC drivers are based on the standard `java.util.logging` framework and the `javax.management` MBean framework. Information about these standard frameworks is not covered in this document.

### 34.1 About Logging Feature of Oracle JDBC Drivers

This section describes the following concepts:

- Overview of Logging Feature of Oracle JDBC Drivers

- Enabling and Using JDBC Logging

- Enabling or Disabling Feature-Specific Logging at Runtime

- Using the Logging Configuration File for Feature-Specific Logging

- Performance, Scalability, and Security Issues

#### 34.1.1 Overview of Logging Feature of Oracle JDBC Drivers

This feature logs information about events that occur when JDBC driver code runs. Events can include user-visible events, such as SQL exceptions, running of SQL statements, and detailed JDBC internal events, such as entry to and exit from internal JDBC methods. Users can enable this feature to log specific events or all the events.

Prior to Oracle Database 11g, JDBC drivers supported J2SE 2.0 and 3.0. These versions of J2SE did not include `java.util.logging`. Therefore, the logging feature provided by JDBC driver releases prior to Oracle Database 11g, differs from the `java.util.logging` framework.

Starting from Oracle Database 11g, the JDBC drivers no longer support J2SE 2.0 and 3.0. Therefore, the logging feature of JDBC drivers makes full use of the standard `java.util.logging` package. The enhanced logging system makes effective use of log levels to enable users to restrict log output to things of interest. It logs specific classes of information more consistently, making it easier for the user to understand the log file.

This feature does not introduce new APIs or configuration files. Only new parameters are added to the existing standard `java.util.logging` configuration file. These parameters are identical in use to the existing parameters and are intrinsic to using `java.util.logging`.

**Note:**

Oracle does not guarantee the exact content of the generated logs. To a large extent the log content is dependent on the details of the implementation. The details of the implementation change with every release, and therefore, the exact content of the logs are likely to change from release to release.

#### 34.1.2 Enabling and Using JDBC Logging

Before you can start debugging your Java application, you must enable and configure JDBC logging. This section covers the steps you must perform to enable and use JDBC logging. It describes the following:

- About Configuring the CLASSPATH

- Enabling Logging

- Configuring Logging

- Using Loggers

- Logging Example

##### 34.1.2.1 About Configuring the CLASSPATH

Oracle ships several JAR files for each version of the JDBC drivers. The optimized JAR files do not contain any logging code and, therefore, do not generate any log output when used. To get log output, you must use the debug JAR files, which are indicated with a "\_g" in the file name, like `ojdbc6_g.jar` or `ojdbc7_g.jar`. The debug JAR file must be included in the `CLASSPATH`.

**Note:**

Ensure that the debug JAR file, say `ojdbc6_g.jar` or `ojdbc7_g.jar`, is the only Oracle JDBC JAR file in the `CLASSPATH`.

##### 34.1.2.2 Enabling Logging

You can enable logging in the following ways:

- Setting a Java system property

  You can enable logging by setting the `oracle.jdbc.Trace` system property.

      java -Doracle.jdbc.Trace=true ...

  Setting the system property enables global logging, which means that logging is enabled for the entire application. You can use global logging if you want to debug the entire application, or if you cannot or do not want to change the source code of the application.

- Programmatically

  You can programmatically enable or disable logging in the following way:

  First, get the `ObjectName` of the Diagnosability MBean. The `ObjectName` is

      com.oracle.jdbc:type=diagnosability,name=<loader>

  Here, `loader` is a unique name based on the class loader instance that loaded the Oracle JDBC drivers.

  **Note:**

  The drivers can be loaded multiple times in a single VM. So, there can be multiple MBeans, each with a unique name.

  Now, write the following lines of code:

      ClassLoader l = oracle.jdbc.OracleDriver.getClassLoader();
      String loader = l.getName() + "@" + l.hashCode();
      // compute the ObjectName

      javax.management.ObjectName name = new javax.management.ObjectName("com.oracle.jdbc:type=diagnosability,
      name="+loader);

      // get the MBean server
      javax.management.MBeanServer mbs = java.lang.management.ManagementFactory.getPlatformMBeanServer();

      // find out if logging is enabled or not
      System.out.println("LoggingEnabled = " + mbs.getAttribute(name, "LoggingEnabled"));

      // enable logging
      mbs.setAttribute(name, new javax.management.Attribute("LoggingEnabled", true));

      // disable logging
      mbs.setAttribute(name, new javax.management.Attribute("LoggingEnabled", false));

  **Note:**

  - If the same class loader loads the JDBC drivers multiple times, then each subsequent MBean increments the value of the `l.hashCode()` method, so as to create a unique name. It may be problematic to identify which MBean is associated with which JDBC driver instance.

  - If there is only one instance of the JDBC drivers loaded, then set the name to "\*".

Programmatic enabling and disabling of logging helps you to control what parts of your application need to generate log output.

**Note:**

Enabling logging using either of the methods would only generate a minimal log of serious errors. Usually this is not of much use. To generate a more useful and detailed log, you must configure `java.util.logging`.

##### 34.1.2.3 Configuring Logging

To generate a useful and detailed log, you must configure `java.util.logging`. This can be done either through a configuration file or programmatically.

A sample configuration file, `OracleLog.properties`, is provided as part of the JDBC installation in the `demo` directory. It contains basic information about how to configure `java.util.logging` and provides some initial settings that you can start with. You may use this sample file as is, edit the file and use it, rename the file and edit it, or create an entirely new file of any name.

To use a configuration file, you must identify it to the Java run-time. This can be done by setting a system property. For example:

    java -Djava.util.logging.config.file=/jdbc/demo/OracleLog.properties.

It is read by the `java.util.logging` system. This file can reside anywhere.

You can use both `java.util.logging.config.file` and `oracle.jdbc.Trace` at the same time.

    java -Djava.util.logging.config.file=/jdbc/demo/OracleLog.properties -Doracle.jdbc.Trace=true

You can use the default `OracleLog.properties` file. It may or may not get you the desired output. You can also create and use your own configuration file by following these steps:

1.  Create a file named `myConfig.properties`. You can use any name you choose.
2.  Insert the following lines of text in the file:
        .level=SEVERE
        oracle.jdbc.level=INFO
        oracle.jdbc.handlers=java.util.logging.ConsoleHandler
        java.util.logging.ConsoleHandler.level=INFO
        java.util.logging.ConsoleHandler.formatter=java.util.logging.SimpleFormatter
3.  Save the file.
4.  Set the system property to use this configuration file.
        java -Djava.util.logging.config.file=<filepath>/myConfig.properties ...

    `filepath` is the path of the folder where you have saved the `myConfig.properties` file.

**Note:**

If you use the settings specified in Step 2, then a huge amount of log output will be generated. Also, the log output will be displayed on the console.

##### 34.1.2.4 Redirecting the Log Output to a File

You can also configure `java.util.logging` to redirect the log output into a file. To do so, modify the configuration file as follows:

    .level=SEVERE
    oracle.jdbc.level=INFO
    oracle.jdbc.handlers=java.util.logging.FileHandler
    java.util.logging.FileHandler.level=INFO
    java.util.logging.FileHandler.pattern=jdbc.log
    java.util.logging.FileHandler.count=1
    java.util.logging.FileHandler.formatter=java.util.logging.SimpleFormatter

This will generate exactly the same log output and save it in a file named `jdbc.log` in the current directory.

You can control the amount of detail by changing the level settings. The defined levels from the least detailed to the most detailed are the following:

- `OFF`

  Turns off logging.

- `SEVERE`

  Logs SQLExceptions and internal errors.

- `WARNING`

  Logs SQLWarnings and bad but not fatal internal conditions.

- `INFO`

  Logs infrequent but significant events and errors. It produces a relatively low volume of log messages.

- `CONFIG`

  Logs SQL strings that are executed.

- `FINE`

  Logs the entry and exit to every public method providing a detailed trace of JDBC operations. It produces a fairly high volume of log messages.

- `FINER`

  Logs calls to internal methods.

- `FINEST`

  Logs calls to high volume internal methods.

- `ALL`

  Logs all the details. This is the most detailed level of logging.

**Note:**

Levels more detailed than `FINE` generate huge log volumes.

In the example provided earlier, to reduce the amount of detail, change the `java.util.logging.FileHandler.level` setting from `ALL` to `INFO`:

    java.util.logging.FileHandler.level=INFO

**Note:**

`INFO` logs the SQL strings that are executed.

Although you can, it is not necessary to change the level of the `oracle.jdbc` logger. Setting the `FileHandler` level will control what log messages are dumped into the log file.

##### 34.1.2.5 Using Loggers

Setting the level reduces all the logging output from JDBC. However, sometimes you need a lot of output from one part of the code and very little from other parts. To do that you must understand more about loggers.

Loggers exist in a tree structure defined by their names. The root logger is named "", the empty string. If you look at the first line of the configuration file you see` .level=SEVERE`. This is setting the level of the root logger. The next line is `oracle.jdbc.level=INFO`. This sets the level of the logger named `oracle.jdbc`. The `oracle.jdbc` logger is a member of the logger tree. Its parent is named `oracle`. The parent of the `oracle` logger is the root logger (the empty string).

Logging messages are sent to a particular logger, for example, `oracle.jdbc`. If the message passes the level check at that level, then the message is passed to the handler at that level, if any, and to the parent logger. So a log message sent to `oracle.log` is compared against that logger's level, `INFO` if you are following along. If the level is the same or less (less detailed) then it is sent to the FileHandler and to the parent logger, 'oracle'. Again it is checked against the level. If as in this case, the level is not set then it uses the parent level, `SEVERE`. If the message level is the same or less it is passed to the handler, which there is not one, and sent to the parent. In this case the parent in the root logger.All this tree structure did not help you reduce the amount of output. What will help is that the JDBC drivers use several subloggers. If you restrict the log messages to one of the subloggers you will get substantially less output. The loggers used by Oracle JDBC drivers include the following:

- `oracle.jdbc`

- `oracle.jdbc.pool`

- `oracle.jdbc.rowset`

- `oracle.jdbc.xa`

- `oracle.sql`

**Note:**

The loggers used by the drivers may vary from release to release.

##### 34.1.2.6 Logging Example

Suppose you want to trace what is happening in the `oracle.sql` component and also want to capture some basic information about the rest of the driver. This is a more complex use of logging. The following are the entries in the `config` file:

         #
         # set levels
         #
    .level=SEVERE
    oracle.level=INFO
    oracle.jdbc.driver.level=INFO
    oracle.jdbc.pool.level=OFF
    oracle.jdbc.util.level=OFF
    oracle.sql.level=INFO
         #
         # configure handlers
         #
    oracle.handlers=java.util.logging.ConsoleHandler
    java.util.logging.ConsoleHandler.level=INFO
    java.util.logging.ConsoleHandler.formatter=java.util.logging.SimpleFormatter

Let us consider what each line in the configuration file is doing.

    .level=SEVERE

Sets the logging level of the root logger to `SEVERE`. We do not want to see any logging from other, non-Oracle components unless something fails badly. Therefore, we set the default level for all loggers to `SEVERE`. Each logger inherits its level from its parent unless set explicitly. By setting the level of the root logger to `SEVERE` we ensure that all other loggers inherit that level except for the ones we set otherwise.

    oracle.level=INFO

We want log output from both the `oracle.sql` and `oracle.jdbc.driver` loggers. Their common ancestor is `oracle`. Therefore, we set the level of the `oracle` logger to `INFO`. We will control the detail more explicitly at lower levels.

    oracle.jdbc.driver.level=INFO

We only want to see the SQL execution from `oracle.jdbc.driver`. Therefore, we set the level to `INFO`. This is a fairly low volume level, but will help us to keep track of what our test is doing.

    oracle.jdbc.pool.level=OFF

We are using a `DataSource` in our test and do not want to see all of that logging. Therefore, we turn it `OFF`.

    oracle.jdbc.util.level=OFF

We do not want to see the logging from the `oracle.jdbc.util` package. If we were using XA or row sets we would turn them off as well.

    oracle.sql.level=INFO

We want to see what is happening in `oracle.sql`. Therefore, we set the level to `INFO`. This provides a lot of information about the public method calls without overwhelming detail.

    oracle.handlers=java.util.logging.ConsoleHandler

We are going to dump everything to `stderr`. When we run the test we will redirect `stderr` to a file.

    java.util.logging.ConsoleHandler.level=INFO

We want to dump everything to the console which is `System.err`. In this case, we are doing the filtering with the loggers rather than the handler.

    java.util.logging.ConsoleHandler.formatter=java.util.logging.SimpleFormatter

We will use a simple, more or less human readable format.

When you run your test with this configuration file, you will get moderately detailed information from the `oracle.sql` package, a little bit of information from the core driver code, and nothing from any other code.

You can also use `XMLFormatter` for sending logs to Oracle Support.

You can implement and use a custom `java.util.logging.Filter` to obtain finer control of the data captured in the logs. This is a standard `java.util.logging` feature and is documented in the JSE JavaDoc. A custom Filter enables you to:

- Capture only one thread in multithreaded applications

- Capture intermittent errors in long running applications

#### 34.1.3 Enabling or Disabling Feature-Specific Logging at Run Time

Starting from Oracle Database 12c Release 2 (12.2.0.1), JDBC provides support for enabling and disabling feature-specific logging for selected features during runtime. For example, you can enable logging only for Load Balancing feature, while disabling logging for other features of JDBC. Again, during the same run, you can enable logging for Fast Connection Failover feature and disable logging for Load Balancing feature.

By default, logging for all features is enabled.

The logging switching knob of JDBC is a part of the `OracleDiagnosabilityMBean`. For using this bean, start JConsole and connect to the application.

Displaying Supported Features

For a list of supported features, use the following method:

    getTraceController().getSupportedFeatures()

Displaying Enabled Features

For a list of currently enabled features, use the following method:

    getTraceController().getEnabledFeatures()

Enabling Logging for a Feature

For enabling logging for a specific feature or for all features, use the `trace` method in the following ways:

    trace(boolean enable, String feature_name)
    trace(boolean enable, ALL)

Disabling Logging for a Feature

For disabling logging for a specific feature or for all features, use the `trace` method in the following ways:

    trace(boolean disable, String feature_name)
    trace(boolean disable, ALL)

Suspending and Resuming Logging

Use the following methods for suspending and resuming logging respectively:

    suspend()
    resume()

#### 34.1.4 Using the Logging Configuration File for Feature-Specific Logging

Starting from Oracle Database 12c Release 2 (12.2.0.1), you can enable or disable logging for specific features by adding a property in the logging configuration file. By default, logging is enabled for all features. Otherwise, you can enable logging for all features using the following syntax:

    clio.feature.all = on

For feature-specific enabling of logging, you can use the following properties:

    clio.feature.pool_statistics = on
    clio.feature.check_in = on
    clio.feature.check_out = on
    clio.feature.labeling = on
    clio.feature.conn_construction = on
    clio.feature.conn_destruction = on
    clio.feature.high_availability = on
    clio.feature.load_balancing = on
    clio.feature.transaction_affinity = on
    clio.feature.web_affinity = on
    clio.feature.data_affinity = on
    clio.feature.conn_harvesting = on
    clio.feature.ttl_conn_timeout = on
    clio.feature.abandoned_conn_timeout = on
    clio.feature.admin = on
    clio.feature.sharding = on

#### 34.1.5 Performance, Scalability, and Security Issues

Although the logging feature enables you to trace or debug your application and generate detail log output, it has certain performance, scalability, and security issues.

**Caution:**

Trace files are likely to contain sensitive information including user names, passwords, and user data. Oracle recommends that users do not use JDBC debug JAR files with production data or credentials, so as to protect that sensitive information. In addition, Oracle recommends that users must follow good security practices for creating trace files.

##### Security Concerns

Enabling full logging creates the risk that sensitive information will be exposed in the trace files. This is intrinsic to the logging feature. However, only certain JDBC JAR files include the JDBC logging feature. The following JAR files include full logging and should not be used in a production environment:

- `ojdbc8_g.jar`

- `ojdbc8dms_g.jar`

The `ojdbc8dms.jar` JAR file includes a limited logging capability.

**Note:**

Database user names and passwords do not appear in log files created by the `ojdbc8_g.jar` and the `ojdbc8dms_g.jar` JAR files. However, sensitive user data that is part of a SQL statement, a defined value, or a bind value can appear in a log created using one of these JAR files.

##### About Secure Handling of Trace Files

For secure handling of trace files, you must:

- Trace only as much of the execution as needed to minimize the amount of sensitive information in the trace file.

- Create the trace file in a directory owned by you. Do not create the file in common public directories, such as the `/tmp` directory.

- Set the `UMASK` for the directory where the trace file is created. This will restrict user access to the trace file.

- Not enable the `append` option in `java.util.logging.FileHandler`. This will provide better control over the owner and permissions on the trace file.

- Not grant `LoggingPermission` to the JDBC code base, when using the `ojdbc8.jar` file. The `ojdbc8dms.jar` file provides limited log output and requires `LoggingPermission`. The debug JAR files, `ojdbc8_g.jar` and `ojdbc8dms_g.jar` have extensive trace and require `LoggingPermission`.

##### Performance and Scalability Issues

Logging has substantial impact on performance. You must make sure that logging is not enabled in production systems. Also, you must not use the debug JAR files in a production environment. When logging is disabled, it has no impact on performance.

Logging involves protected access to a number of shared resources resulting in severely reduced scalability. This is intrinsic to the `java.util.logging` framework.

### 34.2 Diagnosability Management

The JDBC diagnosability management feature introduces an MBean, `oracle.jdbc.driver.OracleDiagnosabilityMBean`. This MBean provides means to enable and disable JDBC logging.

**See Also:**

For information about the `OracleDiagnosabilityMBean` API, refer to the JDBC Javadoc.

In future releases, the MBean will be enhanced to provide additional statistics about JDBC internals.

#### Security Concerns

This feature can enable JDBC logging. Enabling JDBC logging does not require any special permission. However, once logging is enabled, generating any log output requires the standard Java permission `LoggingPermission`. Without this permission, any JDBC operation that would generate log output will throw a security exception. This is a standard Java mechanism.
