Before you install Oracle JVM as part of your standard Oracle Database installation, you must ensure that the configuration requirements for Oracle JVM are fulfilled. The main configuration for Java classes within Oracle Database includes configuring the:

- Java memory requirements

  You must have at least 50 MB of `JAVA_POOL_SIZE` and 96 MB of `SHARED_POOL_SIZE`.

  **Note:**

  Oracle recommends that you increase the `JAVA_POOL_SIZE` and `SHARED_POOL_SIZE` values when using large Java applications, or when a large number of users are running Java in the database.

- Database processes

  You must decide whether to use dedicated server processes or shared server processes for your database server.

  **Note:**

  Oracle recommends that you use dedicated servers. Shared server incurs extra Java states save in the database session, in SGA, at the end of the Java call.

**Related Topics**

- [About Java Memory Usage](about-Java-memory-usage.md)
