This chapter describes BS2000-specific features for Java in the database. This chapter includes:

- Installation of a Java Enabled Database

- Database character sets and Java Encodings

- Java Demonstration Files

**See Also:**

Oracle Java documentation set for more information

### 10.1 Installation of a Java Enabled Database

When you call `$ORACINST.INSTALL.P.SUPER` and set the `JAVA` parameter to `YES`, you get a database that meets the Java requirements.

When you enable Java in an existing Oracle database, you can use the Java related parts of this procedure as an example and modify it according to your needs. For example, you can increase `dbsize`, `shared_pool_size`, run `initjvm.sql`, and so on.

#### Where can files related to Java reside and how should they be encoded?

It is not absolutely straightforward where files used by Java must be stored and how they should be encoded. In general, files can reside either in the native BS2000 or in the POSIX file system. However, there are exceptions.

The following table gives an overview of the file types, location, default encoding, and encoding modifications for APIs or statements:

| Statement or API                   | File type      | Place                    | Default encoding                              | Encoding modification                                            |
|:-----------------------------------|:---------------|:-------------------------|:----------------------------------------------|:-----------------------------------------------------------------|
| `CREATE JAVA CLASS USING BFILE`    | .class         | BS2000 PAM file or POSIX | Binary                                        | Not applicable                                                   |
| `CREATE JAVA RESOURCE USING BFILE` | .properties    | BS2000 PAM file or POSIX | ascii                                         | None, that is, there is no means to change the default encoding. |
| `CREATE JAVA SOURCE USING BFILE`   | .java, .sqlj   | BS2000 PAM file or POSIX | DB charset                                    | None, that is, there is no means to change the default encoding. |
| `CREATE JAVA SOURCE AS`            | .sql           | Part of statement        | Session character set specified in `NLS_LANG` | `NLS_LANG`                                                       |
| `CALL DBMS_JAVA.LOADJAVA`          | \*, .jar, .zip | POSIX                    | DB charset                                    | Option encoding in loadjava call                                 |
| `java.io-package`                  | \*             | POSIX                    | DB charset                                    | Depends on the classes used                                      |

You can create BS2000 PAM files in ASCII by transferring files with the File Transfer Protocol (FTP) from an ASCII platform to BS2000 in binary mode.

**Related Topics**

- [Oracle Database Java Developer’s Guide](../jjdev/installation-and-configuration.md)

### 10.2 Database character sets and Java Encodings

As far as I/O is concerned, the Oracle JAVAVM uses the database character set as the system property `file.encoding`. Therefore, the following Oracle Database on Fujitsu BS2000 database character sets have been added to the list of supported Java encodings:

    WE8BS2000
    WE8BS2000E
    EE8BS2000
    CE8BS2000
    CL8BS2000
    WE8BS2000L5

These encodings are not known to any other Java implementation.

The system property `file.encoding`, however, does not apply to Java property files. Property files always use the encoding 8859_1. The system property `file.encoding` is used when compiling a source file. You can change this default by either setting the encoding option of the `dbms_java.loadjava` procedure or by using the following procedure:

    dbms_java.set_compiler_option('','encoding',...)

**See Also:**

[Oracle Database SQLJ Developer’s Guide](../jsqlj/advanced-language-features.md) for more details about property files

### 10.3 Java Demonstration Files

A simple Java demonstration program running in the server is shipped under:

    $ORACINST.JAVAVM.DEMO.HELLO.SQL

An example with database connection using the server-side internal driver is shipped under:

    $ORACINST.JAVAVM.DEMO.EMPLOYEE.JAVA
    $ORACINST.JAVAVM.DEMO.CREATE.SQL
    $ORACINST.JAVAVM.DEMO.RUN.SQL
