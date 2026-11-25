UCP leverages the JDK logging facility (`java.util.logging`). Logging is not enabled by default and must be configured in order to print log messages. Logging can be configured using a log configuration file as well as through API-level configuration.

**Note:**

The default log level is `null`. This ensures that a parent logger's log level is used by default.

### 12.4.1 Using a Logging Properties File

Logging can be configured using a properties file. The location of the properties file must be set as a Java property for the logging configuration file property. For example:

    java -Djava.util.logging.config.file=log.properties

The logging properties file defines the handler to use for writing logs, the formatter to use for formatting logs, a default log level, as well as log levels for specific packages or classes. For example:

    handlers = java.util.logging.ConsoleHandler
    java.util.logging.ConsoleHandler.level = ALL
    java.util.logging.ConsoleHandler.formatter = java.util.logging.SimpleFormatter

    oracle.ucp.level = FINEST
    oracle.ucp.jdbc.PoolDataSource = WARNING

A custom formatter is included with UCP and can be entered as the value for the formatter property. For example:

    java.util.logging.ConsoleHandler.formatter = oracle.ucp.util.logging.UCPFormatter

You can also download the `ucpdemos.jar` file, which is shipped with UCP, from Oracle Technology Network (OTN). This file contains a list of sample logging property files. For example, this file contains the logging property file that can be used for troubleshooting the Fast Connection Failover (FCF) feature.

### 12.4.2 Using UCP and JDK API

Logging can be dynamically configured though either the UCP API or the JDK API. When using the UCP API, logging is configured using a connection pool manager. When using the JDK, logging is configured using the `java.util.logging` implementation.

The following example demonstrates using the UCP API to configure logging:

    UniversalConnectionPoolManager mgr = UniversalConnectionPoolManagerImpl.
    getUniversalConnectionPoolManager();

    mgr.setLogLevel(Level.FINE);

The following example demonstrate using the JDK logging implementation directly:

    Logger.getLogger("oracle.ucp").setLevel(Level.FINEST);
    Logger.getLogger("oracle.ucp.jdbc.PoolDataSource").setLevel(Level.FINEST);

### 12.4.3 Enabling or Disabling Feature-Specific Logging at Runtime

Starting from Oracle Database 12c Release 2 (12.2.0.1), UCP provides support for enabling and disabling logging for selected features during runtime. For example, you can enable logging only for Load Balancing feature, while disabling logging for other features of UCP. Again, during the same run, you can enable logging for Fast Failover feature and disable logging for Load Balancing feature.

By default, logging for all features is enabled.

The logging switching feature of UCP is a part of the `OracleDiagnosabilityMBean`. For using this bean, start JConsole and connect to the application.

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

### 12.4.4 About Using the Logging Properties File for Feature-Specific Logging

Starting from Oracle Database 12c Release 2 (12.2.0.1), you can enable or disable logging for specific features by adding a property in the logging properties file. By default, logging is enabled for all features. Otherwise, you can enable logging for all features using the following syntax: `clio.feature.all = on`. For feature-specific enabling of logging, you can use the properties as mentioned in the following section:

#### Supported Features for feature-Based Granularity

    clio.feature.pool_statistics          = on
    clio.feature.check_in                 = on
    clio.feature.check_out                = on
    clio.feature.labeling                 = on
    clio.feature.conn_construction        = on
    clio.feature.conn_destruction         = on
    clio.feature.high_availability        = on
    clio.feature.load_balancing           = on
    clio.feature.transaction_affinity     = on
    clio.feature.web_affinity            = on
    clio.feature.data_affinity           = on
    clio.feature.conn_harvesting          = on
    clio.feature.ttl_conn_timeout         = on
    clio.feature.abandoned_conn_timeout   = on
    clio.feature.admin                    = on
    clio.feature.sharding                 = on

### 12.4.5 Supported Log Levels

The following list describes each of the log levels that are supported for JDBC. Levels lower than `FINE` produce output that may not be meaningful to users. Levels lower than `FINER` will produce very large volumes of output.

- `INTERNAL_ERROR` – Internal Errors

- `SEVERE` – SQL Exceptions

- `WARNING` – SQL Warnings and other invisible problems

- `INFO` – Public events such as connection attempts or Oracle RAC events

- `CONFIG` – SQL statements

- `FINE` – Public APIs

- `TRACE_10` – Internal events

- `FINER` – Internal APIs

- `TRACE_20` – Internal debug

- `TRACE_30` – High volume internal APIs

- `FINEST` – High volume internal debug
