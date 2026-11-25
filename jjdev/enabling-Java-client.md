To run Java between the client and server, your must perform the following activities:

1.  Installing Java SE on the Client
2.  Setting Up Environment Variables

### 4.4.1 Installing Java SE on the Client

The client requires Java Development Kit (JDK) 1.6 or later. To confirm the version of JDK you are using, run the following commands on the command line:

    $ which java
    /usr/local/jdk1.6.0_26/bin/java

    $ which javac
    /usr/local/jdk1.6.0_26/bin/javac

    $ java -version
    java version "1.6.0_26"

### 4.4.2 Setting Up Environment Variables

After installing JDK on your client, add the directory path to the following environment variables:

- `$JAVA_HOME`

  This variable must be set to the top directory of the installed JDK base.

- `$PATH`

  This variable must include `$JAVA_HOME/bin`.

- `$LD_LIBRARY_PATH`

  This variable must include `$JAVA_HOME/lib`.

#### JAR Files Necessary for Java Clients

To ensure that the Java client successfully communicates with the server, include the following files in the `CLASSPATH`:

**Note:**

Specifics of `CLASSPATH` requirements may vary for Oracle JVMs running on different platforms. You must ensure that all elements of `CLASSPATH`, as defined in the script for Oracle JVM utilities, are present.

- For JDK 8, include `$JAVA_HOME/lib/dt.jar`

- For JRE 8, include `$JAVA_HOME/lib/rt.jar`

- For any interaction with JDBC, include `$ORACLE_HOME/jdbc/lib/ojdbc8.jar`

- For any client that uses SSL, include `$ORACLE_HOME/jlib/jssl-1_2.jar` and `$ORACLE_HOME/jlib/javax-ssl-1_2.jar`

- For any client that uses the Java Transaction API (JTA) functionality, include `$ORACLE_HOME/jlib/jta.jar`

- For any client that uses the Java Naming and Directory Interface (JNDI) functionality, include `$ORACLE_HOME/jlib/jndi.jar`

#### Server Application Development on the Client

If you develop and compile your server applications on the client and want to use the same Java Archive (JAR) files that are loaded on the server, then include `$ORACLE_HOME/lib/aurora.zip` in `CLASSPATH`. This is not required for running Java clients.
