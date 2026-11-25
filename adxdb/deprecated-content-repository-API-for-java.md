Oracle XML DB Content Connector implements Content Repository API for Java (also known as JCR), a Java API standard developed by the Java community as JSR-170. You can access Oracle XML DB Repository using Oracle XML DB Content Connector.

**Note:**

Oracle XML DB Content Connector is deprecated, starting with Oracle Database 12c Release 2 (12.2.0.1). Java standard JSR-170 has been replaced by JSR-283 Content Repository for Java Technology Version 2.0.

- About the Content Repository API for Java (JCR)
  JCR 1.0 defines a standard Java API for applications to interact with content repositories. A content repository is a tree of nodes, each of which can have one or more child nodes. Each node has exactly one parent node, except for the root node, which has no parent.
- About Oracle XML DB Content Connector
  Oracle XML DB Content Connector lets you access Oracle XML DB Repository using JCR 1.0 Java. Your applications can run either in a standalone Java Virtual Machine (JVM) or a J2EE container. Files and folders in the repository are represented as JCR nodes (and properties of those nodes).
- How Oracle XML DB Repository Is Exposed in JCR
  Oracle XML DB Content Connector represents data in Oracle XML DB Repository as JCR nodes and properties. Files and folders are represented as nodes of type `nt:file` and `nt:folder`, respectively. Their content and metadata is exposed as nodes of node type `nt:resource`.
- CLASSPATH for Oracle XML DB Content Connector
  Oracle XML DB Content Connector requires certain entries in environment variable `CLASSPATH`.
- Obtaining the JCR Repository Object
  In Oracle XML DB Content Connector, `oracle.jcr.OracleRepository` implements JCR interface `javax.jcr.Repository`, which provides the entry point for a JCR repository. You can use it to obtain a `Repository` object for Oracle XML DB Repository.
- Java Code to Upload a File to the Repository using Oracle XML DB Content Connector
  You can use Oracle XML DB Content Connector to upload a file from the local file system to Oracle XML DB Repository.
- Additional JCR Code Examples
  You can find additional sample JCR code at `$ORACLE_HOME/xdk/demo/java/jcr`. For each code sample, a `README` file describes its purpose and use.
- Oracle XML DB Content Connector Uses the Standard Java Logging API
  Oracle XML DB Content Connector uses the standard `java.util.logging` framework. You can use the logging API provided by that framework to control logging behavior.
- Supported JCR Compliance Levels
  The JSR-170 standard, which defines JCR version 1.0, defines two compliance levels and a set of optional features. Oracle XML DB Content Connector supports Level 1 (read functions) and Level 2 (write functions).
- Oracle XML DB Content Connector Restrictions
  Certain restrictions apply to Oracle XML DB Content Connector.
- XML Schemas and JCR
  Oracle XML DB Content Connector can create JCR node types from XML schemas.

**Parent topic:** [Appendixes](appendices.md)

### C.1 About the Content Repository API for Java (JCR)

JCR 1.0 defines a standard Java API for applications to interact with content repositories. A content repository is a tree of nodes, each of which can have one or more child nodes. Each node has exactly one parent node, except for the root node, which has no parent.

In addition to child nodes, a node may also have one or more properties. A property is a simple name/value pair. For example, a node representing a particular file in the content repository has a property named `jcr:created` whose value is the date the file was created.

Each property has a property type. For example, the `jcr:created` property has the `DATE` property type, requiring its value to be a valid date/time.

Similarly, each node has a node type. For example, a node representing a file has node type `nt:file`. The node type controls what child nodes and properties the node may have or must have. For example, all nodes of type `nt:file` must have a `jcr:created` property.

Because nodes and properties are named, they can be addressed by path. JCR supports both absolute and relative paths. For example, the absolute path

    /My Documents/pictures/puppy.jpg/jcr:created

resolves to the `jcr:created` property of file `puppy.jpg`. This property can also be addressed relative to the `My Documents` folder by the following relative path:

    pictures/puppy.jpg/jcr:created

Node and property names can be namespace qualified. Like XML, JCR uses colon-delimited namespace prefixes to express namespace-qualified names, for example, `jcr:created`. Unlike XML, JCR records the namespace prefix-to-URI mappings in a repository-wide namespace registry, which, for example, maps the `jcr` prefix to the URI `http://www.jcp.org/jcr/1.0`.

**See Also:**

[JSR 170: Content Repository for Java technology API](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdb&id=jcp_org_jsr_170). Chapter 4 of this specification provides a concise introduction to JCR 1.0.

**Parent topic:** Deprecated Content Repository API for Java

### C.2 About Oracle XML DB Content Connector

Oracle XML DB Content Connector lets you access Oracle XML DB Repository using JCR 1.0 Java. Your applications can run either in a standalone Java Virtual Machine (JVM) or a J2EE container. Files and folders in the repository are represented as JCR nodes (and properties of those nodes).

You can create, retrieve, and update repository files and folders using the JCR APIs.

**Note:**

Using Oracle XML DB Content Connector in the database Oracle JVM (the Java Virtual Machine available within a database process) is not supported. To use the content connector in the database tier, you must use either a standalone Java Virtual Machine or a J2EE container.

**Parent topic:** Deprecated Content Repository API for Java

### C.3 How Oracle XML DB Repository Is Exposed in JCR

Oracle XML DB Content Connector represents data in Oracle XML DB Repository as JCR nodes and properties. Files and folders are represented as nodes of type `nt:file` and `nt:folder`, respectively. Their content and metadata is exposed as nodes of node type `nt:resource`.

**Parent topic:** Deprecated Content Repository API for Java

### C.4 CLASSPATH for Oracle XML DB Content Connector

Oracle XML DB Content Connector requires certain entries in environment variable `CLASSPATH`.

- `$ORACLE_HOME/lib/jcr-1.0.jar`

- `$ORACLE_HOME/lib/ojcr.jar`

- `$ORACLE_HOME/lib/xmlparserv2.jar`

- `$ORACLE_HOME/jlib/xquery.jar`

**Parent topic:** Deprecated Content Repository API for Java

### C.5 Obtaining the JCR Repository Object

In Oracle XML DB Content Connector, `oracle.jcr.OracleRepository` implements JCR interface `javax.jcr.Repository`, which provides the entry point for a JCR repository. You can use it to obtain a `Repository` object for Oracle XML DB Repository.

The code fragment in Example C-1 illustrates this.

`OracleRepository` implements both `java.io.Serializable` and `javax.naming.Referenceable`. This lets you create and configure an `OracleRepository` object upon application deployment, and store the ready-to-use `OracleRepository` object in a JNDI directory. At run-time, your application can retrieve the preconfigured `OracleRepository` object from the JNDI directory. This approach, recommended by the JCR specification, separates deployment and run-time concerns.

In Oracle XML DB Content Connector, the set of prefix-to-URI mappings forming the JCR namespace registry is stored as part of the `OracleRepository` configuration.

**See Also:**

[Oracle Database XML Java API Reference](../jaxml/index.md), package `oracle.jcr`

Example C-1 Code Fragment Showing How to Get a Repository Object

    import oracle.jcr.OracleRepository;
    import oracle.jcr.OracleRepositoryFactory;
    import oracle.jcr.xdb.XDBRepositoryConfiguration;
    import oracle.jdbc.pool.OracleDataSource;
    ...
    XDBRepositoryConfiguration configuration =
      new XDBRepositoryConfiguration();
    OracleDataSource ods =
      (OracleDataSource)configuration.getDataSource();
    // databaseURL is a JDBC database URL.
    ods.setURL(databaseURL);
    // OracleRepository implements javax.jcr.Repository.
    OracleRepository repository =
      OracleRepositoryFactory.createOracleRepository(configuration);

**Parent topic:** Deprecated Content Repository API for Java

### C.6 Java Code to Upload a File to the Repository using Oracle XML DB Content Connector

You can use Oracle XML DB Content Connector to upload a file from the local file system to Oracle XML DB Repository.

Example C-2 is a Java program that illustrates this. You can compile and run it from the command line. The program requires the following command-line arguments:

- JDBC database URL

- User ID

- User password

- Folder in Oracle XML DB Repository into which to upload the file

- File to be uploaded

- MIME type

Example C-3 illustrates this.

Example C-2 Uploading a File Using Oracle XML DB Content Connector

    import java.io.FileInputStream;

    import javax.jcr.Node;
    import javax.jcr.Session;
    import javax.jcr.SimpleCredentials;

    import oracle.jcr.OracleRepository;
    import oracle.jcr.OracleRepositoryFactory;

    import oracle.jcr.xdb.XDBRepositoryConfiguration;

    import oracle.jdbc.pool.OracleDataSource;

    public class UploadFile
    {
      public static void main(String[] args)
        throws Exception
      {
        String databaseURL = args[0];
        String userName = args[1];
        String password = args[2];
        String parentPath = args[3];
        String fileName = args[4];
        String mimeType = args[5];

        // Get the JCR Repository object.
        XDBRepositoryConfiguration configuration =
          new XDBRepositoryConfiguration();

        OracleDataSource ods =
          (OracleDataSource)configuration.getDataSource();

        ods.setURL(databaseURL);

        OracleRepository repository =
          OracleRepositoryFactory.createOracleRepository(configuration);

        // Create a JCR Session.
        SimpleCredentials sc =
          new SimpleCredentials(userName, password.toCharArray());

        Session session = repository.login(sc);

        // Get the parent node.
        Node parentNode = (Node)session.getItem(parentPath);

        // Get the child contents.
        FileInputStream inputStream = new FileInputStream(fileName);

        // Create child node.
        Node node = parentNode.addNode(fileName, "nt:file");
        Node contentNode = node.getNode("jcr:content");
        contentNode.setProperty("jcr:mimeType", mimeType);
        contentNode.setProperty("jcr:data", inputStream);

        // Save changes and logout.
        session.save();
        session.logout();
      }
    }

    // EOF

Example C-3 Uploading a File Using the Command Line

    export CLASSPATH=.:$ORACLE_HOME/lib/jcr-1.0.jar:$ORACLE_HOME/lib/ojcr.jar:Foot 1
    $ORACLE_HOME/lib/xmlparserv2.jar:$ORACLE_HOME/jlib/xquery.jar

    javac UploadFile.java
    java UploadFile jdbc:oracle:oci:@ quine password /public MyFile.txt text/plain

**Parent topic:** Deprecated Content Repository API for Java

### C.7 Additional JCR Code Examples

You can find additional sample JCR code at `$ORACLE_HOME/xdk/demo/java/jcr`. For each code sample, a `README` file describes its purpose and use.

**Parent topic:** Deprecated Content Repository API for Java

### C.8 Oracle XML DB Content Connector Uses the Standard Java Logging API

Oracle XML DB Content Connector uses the standard `java.util.logging` framework. You can use the logging API provided by that framework to control logging behavior.

For example, the following Java code fragment disables all logging.

    import java.util.logging.LogManager;
    ...
    LogManager.getLogManager().reset();

**Parent topic:** Deprecated Content Repository API for Java

### C.9 Supported JCR Compliance Levels

The JSR-170 standard, which defines JCR version 1.0, defines two compliance levels and a set of optional features. Oracle XML DB Content Connector supports Level 1 (read functions) and Level 2 (write functions).

**Parent topic:** Deprecated Content Repository API for Java

### C.10 Oracle XML DB Content Connector Restrictions

Certain restrictions apply to Oracle XML DB Content Connector.

**Parent topic:** Deprecated Content Repository API for Java

### C.11 XML Schemas and JCR

Oracle XML DB Content Connector can create JCR node types from XML schemas.

**Parent topic:** Deprecated Content Repository API for Java

------------------------------------------------------------------------



Footnote Legend

Footnote 1:

This statement is split across two lines for the purpose of documentation.
