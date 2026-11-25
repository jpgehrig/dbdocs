This chapter describes BS2000 specific topics of XML such as installation, features, and restrictions. It contains the following topics:

- About XDK Installation

- Features and Restrictions of XML Features on BS2000 Systems

**See Also:**

- [Oracle XML Developer's Kit Programmer's Guide](../adxdk/introduction-to-XDK.md)

- [Oracle XML DB Developer’s Guide](../adxdb/intro-to-XML-DB.md)

- [Oracle Database XML C API Reference](../caxml/datatypes.md)

- [Oracle Database XML C++ API Reference](../cpxml/package-Ctx-API.md)

- [Oracle Database XML Java API Reference](../jaxml/index.md)

### 12.1 About XDK Installation

The Jar files for the XML SQL utility, `xsu12.jar` and `xdb.jar`, and the XML Parser, `xmlparserv2.jar` are already loaded in the database when you create a database as explained in "[About Creating a Database](about-creating-a-database.md)."

### 12.2 Features and Restrictions of XML Features on BS2000 Systems

The following table provides an overview of the XML features that are available for the programming languages on BS2000:

An empty field means that the feature is not supported.

N/A means means that it is not applicable.

| XML Feature       | Availability for Java | Availability for C | Availability for C++ | Availability for PL/SQL |
|:------------------|:----------------------|:-------------------|:---------------------|:------------------------|
| Parser            | Yes                   |                    |                      | Yes                     |
| XSLT Processor    | Yes                   |                    |                      | Yes                     |
| Class Generator   |                       | N/A                |                      | N/A                     |
| XSQL              |                       | N/A                | N/A                  | N/A                     |
| Transviewer Beans |                       | N/A                | N/A                  | N/A                     |
| XML-SQL Utility   | Yes                   | N/A                | N/A                  | Yes                     |
| Schema Processor  | Yes                   |                    |                      | N/A                     |

When you use PL/SQL instead of Java, you must consider the following behavior:

- PL/SQL file input is only possible from POSIX and with ASCII data format.

- PL/SQL file output is written to POSIX with ASCII data format.

- For `INSERT`/`UPDATE`/`DELETE` operations the XML document must not contain `<?xml ... encoding=WE8BS2000 ...>`.

When using the JAVA-interfaces, you must ensure the right character set of the data.

If you have an ASCII platform with JDK, then you can also use XML components and operate on the BS2000 Oracle database using a JDBC connection.

**See Also:**

[Java in the Database](java-in-the-database.md) for more information about the encoding considerations
