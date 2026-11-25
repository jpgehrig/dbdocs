1\. Use Database Service on Cloud:

Use the Oracle Database Service on Cloud (DBCS) to create a database on cloud. DBCS comes with an in-built HR schema and tables that you can use when you build the HR web application.

**Note:**

Use Oracle Database Enterprise Edition 12.2.0.1 to use features and functionalities of the latest Oracle Database.

2\. JDBC Driver, UCP:

It is recommend that you use the latest 12.2.0.1 versions of JDBC drivers and UCP.

**Note:**

Download the latest JDBC drivers and UCP from [12.2.0.1 JDBC driver and UCP](http://www.oracle.com/technetwork/database/features/jdbc/jdbc-ucp-122-3110062.html)

3\. JDK 8

It is recommended that you use the latest version of Oracle JDBC driver 12.2.0.1, that is compliant with JDK 8.

4\. Auto-closeable statements

Starting JDK7, ‘Auto-closeable statements’ has been introduced, that close by default without an explicit `catch` statement.

5\. Use PreparedStatement instead of Statement objects:

Statement in JDBC must be localized to being used for `DDL` (`ALTER, CREATE, GRANT` etc) since these commands cannot accept bind variables.

Use `PreparedStatement` or `CallableStatement` for any other type of statement. These statements can accept bind variables.
