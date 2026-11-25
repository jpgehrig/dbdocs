###

Oracle provides enterprise application developers an end-to-end Java solution for creating, deploying, and managing Java applications. The total solution consists of client-side and server-side programmatic interfaces, tools to support Java development, and a JVM integrated with Oracle Database. All these products are fully compatible with Java standards. This section covers the following topics:

- Java in Database Application Development

- Java Programming Environment Usage

- Java Stored Procedures

- PL/SQL Integration and Oracle RDBMS Functionality

- Development Tools

- Internet Protocol Version 6 Support

### 1.6.1 Java in Database Application Development

The most important features of Java in database application development are:

- Designing data-bound procedures and functions using Java SE APIs and JDBC.

- Extending the reach and capabilities of the database with standard and third-party Java libraries. For example, accessing third-party databases using their drivers in the database and accessing Hadoop/HDFS.

- Providing flexible partitioning of Java2 Platform, Standard Edition (J2SE) applications for symmetric data access at the JDBC level.

- Bridging SQL and the Java2 Platform, Enterprise Edition (J2EE) world by:

  - Calling out Web components, such as JSP and servlet

  - Bridging SQL and Web Services using Web Service Callouts

- Using an Oracle JVM as ERP Integration Hub.

- Invalidating cache.

### 1.6.2 Java Programming Environment Usage

In addition to the Oracle JVM, the Java programming environment provides:

- Java stored procedures as the Java equivalent and companion for PL/SQL. Java stored procedures are tightly integrated with PL/SQL. You can call Java stored procedures from PL/SQL packages and PL/SQL procedures from Java stored procedures.

- The JDBC and SQLJ programming interfaces for accessing SQL data.

- Tools and scripts that assist in developing, loading, and managing classes.

The following table helps you decide when to use which Java API:

| Type of functionality you need                                                                        | Java API to use        |
|:------------------------------------------------------------------------------------------------------|:-----------------------|
| To have a Java procedure called from SQL, such as a trigger.                                          | Java stored procedures |
| To call a static, simple SQL statement from a known table with known column names from a Java object. | SQLJ                   |
| To call dynamic, complex SQL statements from a Java object.                                           | JDBC                   |

### 1.6.3 Java Stored Procedures

Java stored procedures are Java programs written and deployed on a server and run from the server, exactly like a PL/SQL stored procedure. You invoke it directly with products like SQL\*Plus, or indirectly with a trigger. You can access it from any Oracle Net client, such as OCI and PRO\*, or JDBC or SQLJ.

In addition, you can use Java to develop powerful, server-side programs, which can be independent of PL/SQL. Oracle Database provides a complete implementation of the standard Java programming language and a fully compliant JVM.

**Related Topics**

- [Developing Java Stored Procedures](developing-Java-stored-procedures.md)

### 1.6.4 PL/SQL Integration and Oracle RDBMS Functionality

You can call existing PL/SQL programs from Java and Java programs from PL/SQL. This solution protects and leverages your PL/SQL and Java code and opens up the advantages and opportunities of Java-based Internet computing.

Oracle Database offers two different Java APIs for accessing SQL data, JDBC and SQLJ. Both these APIs are available on the client, and the JDBC API is also available on the server. As a result, you can deploy your applications on the client and server.

The following topics introduce the Java APIs provided by Oracle Database:

- JDBC Drivers

- SQLJ

#### 1.6.4.1 JDBC Drivers

JDBC is a database access protocol that enables you to connect to a database and run SQL statements and queries to the database. The core Java class libraries provide the following JDBC APIs: `java.sql` and `javax.sql`. However, JDBC is designed to enable vendors to supply drivers that offer the necessary specialization for a particular database. Oracle provides the following distinct JDBC drivers:

| Driver                           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|:---------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| JDBC Thin driver                 | You can use the JDBC Thin driver to write pure Java applications and applets that access Oracle SQL data. The JDBC Thin driver is especially well-suited for Web-based applications and applets, because you can dynamically download it from a Web page, similar to any other Java applet.                                                                                                                                                                                                                                                                                                                       |
| JDBC OCI driver                  | The JDBC OCI driver accesses Oracle-specific native code, that is, non-Java code, and libraries on the client or middle tier, providing performance boost compared to the JDBC Thin driver, at the cost of significantly larger size and client-side installation.                                                                                                                                                                                                                                                                                                                                                |
| JDBC server-side internal driver | Oracle Database uses the server-side internal driver when the Java code runs on the server. It allows Java applications running in the Oracle JVM on the server to access locally defined data, that is, data on the same system and in the same process, with JDBC. It provides a performance boost, because of its ability to use the underlying Oracle RDBMS libraries directly, without the overhead of an intervening network connection between the Java code and SQL data. By supporting the same Java-SQL interface on the server, Oracle Database does not require you to rework code when deploying it. |

**Related Topics**

- [About Utilizing SQLJ and JDBC with Java in the Database](invoking-Java-methods.md)

**See Also:**

[Oracle Database JDBC Developer’s Guide](../jjdbc/introducing-JDBC.md)

#### 1.6.4.2 SQLJ

Oracle has worked with other vendors, including IBM, Tandem, and Sybase, to develop a standard way to embed SQL statements in Java programs called SQLJ. This work has resulted in a new standard, ANSI x.3.135.10-1998, for a simpler and more highly productive programming API than JDBC. A user writes applications to this higher-level API and then uses a preprocessor to translate the program to standard Java source with JDBC calls. At run time, the program can communicate with multi-vendor databases using standard JDBC drivers.

SQLJ provides a simple, but powerful, way to develop client-side applications that access databases from Java. You can use SQLJ in stored procedures and triggers. In addition, you can combine SQLJ programs with JDBC.

The SQLJ translator is a Java program that translates embedded SQL in Java source code to pure JDBC-based Java code.

**See Also:**

[Oracle Database SQLJ Developer’s Guide](../jsqlj/intro-to-SQLJ.md)

### 1.6.5 Development Tools

The introduction of Java in Oracle Database enables you to use several Java IDEs. The adherence of Oracle Database to the Java standards and specifications and the open Internet standards and protocols ensures that your Java programs work successfully, when you deploy them on Oracle Database. Oracle provides many tools or utilities that are written in Java making development and deployment of Java server applications easier. Oracle JDeveloper, a Java IDE provided by Oracle, has many features designed specifically to make deployment of Java stored procedures and EJBs easier. You can download JDeveloper from

[`http://www.oracle.com/technetwork/developer-tools/jdev/overview/index.html`](http://www.oracle.com/technetwork/developer-tools/jdev/overview/index.html)

### 1.6.6 Internet Protocol Version 6 Support

Starting from Oracle Database 11g Release 2, Oracle JVM supports Internet Protocol Version 6 (IPv6) addresses in the URL and machine names of the Java code in the database, which resolve to IPv6 addresses. IPv6 is a new Network layer protocol designed by the Internet Engineering Task Force (IETF) to replace the current version of Internet Protocol, Internet Protocol Version 4 (IPv4). The primary benefit of IPv6 is a large address space, derived from the use of 128-bit addresses. IPv6 also improves upon IPv4 in areas such as routing, network autoconfiguration, security, quality of service, and so on.

The following system properties enable you to configure IPv6 preferences:

#### java.net.preferIPv4Stack

If IPv6 is available on the operating system, then the underlying native socket will be an IPv6 socket. This enables Java applications to connect to, and accept connections from both IPv4 and IPv6 hosts. If you have an application that has a preference to use only IPv4 sockets, then you can set this property to `true`. If you set the property to `true`, then it implies that the application will not be able to communicate with IPv6 hosts.

#### java.net.preferIPv6Addresses

Even if IPv6 is available on the operating system, then for backward compatibility reasons, the addresses are mapped to IPv4. For example, applications that depend on access to only an IPv4 service, benefit from this type of mapping. If you want to change the preferences to use IPv6 addresses over IPv4 addresses, then you can set the `java.net.preferIPv6Addresses` property to `true`. This allows applications to be tested and deployed in environments, where the application is expected to connect to IPv6 services.

**Note:**

All the new System classes that are required for IPv6 support are loaded when Java is enabled during database initialization. So, if your application does not have any addresses that are included in the software code, then you do not need to change your code to use IPv6 functionality.
