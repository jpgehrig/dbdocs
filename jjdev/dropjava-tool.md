The `dropjava` tool is the converse of the `loadjava` tool. It transforms command-line file names and JAR or ZIP file contents to schema object names, drops the schema objects, and deletes their corresponding digest table rows. You can enter `.java`, `.class`, `.sqlj`, `.ser`, `.zip`, `.jar`, and resource file names on the command line and in any order.

Alternatively, you can specify a schema object name directly to the `dropjava` tool. A command-line argument that does not end in `.jar`, `.zip`, `.class`, `.java`, or `.sqlj` is presumed to be a schema object name. If you specify a schema object name that applies to multiple schema objects, then all will be removed.

Dropping a class invalidates classes that depend on it, recursively cascading upwards. Dropping a source drops classes derived from it.

**Note:**

You must remove Java schema objects in the same way that you first loaded them. If you load a `.sqlj` source file and translate it in the server, then you must run the `dropjava` tool on the same source file. If you translate on a client and load classes and resources directly, then run the `dropjava` tool on the same classes and resources.

You can run the `dropjava` tool either from the command line or by using the `dropjava` method in the `DBMS_JAVA` class. To run the `dropjava` tool from within your Java application, use the following command:

    call dbms_java.dropjava('... options...');

The options are the same as specified on the command line. Separate each option with a space. Do not separate the options using commas. The only exception to this is the `-resolver` option. The connection is always made to the current session. Therefore, you cannot specify another user name through the `-user` option.

For `-resolver`, you should specify all other options first, a comma (`,`), then the `-resolver` option with its definition. Do not specify the `-thin`, `-oci`, `-user`, and `-password` options, because they relate to the database connection for the `loadjava` tool. The output is directed to `stderr`. Set `serveroutput` on and call `dbms_java.set_output`, as appropriate.

This section covers the following topics:

- dropjava Tool Syntax

- dropjava Tool Argument Summary

- dropjava Tool Argument Details

- List Based Deletion

- About Dropping Resources Using dropjava Tool

### 12.7.1 dropjava Tool Syntax

The syntax of the `dropjava` tool command is:

    dropjava [options] {file.java | file.class | file.sqlj |
    file.jar | file.zip | resourcefile} ...
      -u | -user user/[password][@database]
      [-genmissingjar JARfile]
      [-jarasresource]

      [-o | -oci | -oci8]
      [-optionfile file]
      [-optiontable table_name]
      [-S | -schema schema]
      [-stdout]
      [-s | -synonym]
      [-t | -thin]

      [-v | -verbose]
     [-list]
    [-listfile]

### 12.7.2 dropjava Tool Argument Summary

Table 12-3 summarizes the `dropjava` tool arguments.

Table 12-3 dropjava Argument Summary

| Argument                    | Description                                                                                                                                                                                                                                                                          |
|:----------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-user`                     | Specifies a user name, password, and optional database connection string. The files will be dropped from this database instance.                                                                                                                                                     |
| `filenames`                 | Specifies any number and combination of `.java`, `.class`, `.sqlj`, `.ser`, `.jar`, `.zip`, and resource file names.                                                                                                                                                                 |
| `-genmissingjar ``JARfile`  | Treats the operand of this option as a file to be processed.                                                                                                                                                                                                                         |
| `-jarasresource`            | Drops the whole JAR file, which was previously loaded as a resource.                                                                                                                                                                                                                 |
| `-oci | -oci8`              | Directs the `dropjava` tool to connect with the database using the OCI JDBC driver. The `-oci` and the `-thin` options are mutually exclusive. If neither is specified, then the `-oci` option is used by default. Choosing the `-oci` option implies the form of the `-user` value. |
| `-optionfile ``file`        | Has the same usage as for the `loadjava` tool.                                                                                                                                                                                                                                       |
| `-optiontable ``table_name` | Has the same usage as for `loadjava`.                                                                                                                                                                                                                                                |
| `-schema ``schema`          | Designates the schema from which schema objects are dropped. If not specified, then the logon schema is used. To drop a schema object from a schema that is not your own, you need the `DROP ANY PROCEDURE` and `UPDATE ANY TABLE` privileges.                                       |
| `-stdout`                   | Causes the output to be directed to `stdout`, rather than to `stderr`.                                                                                                                                                                                                               |
| `-synonym`                  | Drops a `PUBLIC` synonym that was created with the `loadjava` tool.                                                                                                                                                                                                                  |
| `-thin`                     | Directs the `dropjava` tool to communicate with the database using the JDBC Thin driver. Choosing the `-thin` option implies the form of the `-user` value.                                                                                                                          |
| `-verbose`                  | Directs the `dropjava` tool to emit detailed status messages while running.                                                                                                                                                                                                          |
| `–list`                     | Drops the classes, Java source, or resources listed on the command line without them being present on the client machine or server machine.                                                                                                                                          |
| `-listfile`                 | Reads a file and drops the classes, Java source, or resources listed in the file without them being present on the client machine or server machine.The file contains the internal representation of the complete class, Java source, or resource name one per line.                 |

### 12.7.3 dropjava Tool Argument Details

This section describes a few of the `dropjava` tool arguments, which are complex.

#### File Names

The `dropjava` tool interprets most file names as the `loadjava` tool does:

- `.class` files

  Finds the class name in the file and drops the corresponding schema object.

- `.java` and `.sqlj` files

  Finds the first class name in the file and drops the corresponding schema object.

- `.jar` and `.zip` files

  Processes the archived file names as if they had been entered on the command line.

If a file name has another extension or no extension, then the `dropjava` tool interprets the file name as a schema object name and drops all source, class, and resource objects that match the name.

If the `dropjava` tool encounters a file name that does not match a schema object, then it displays a message and processes the remaining file names.

#### user

    {-user | -u} user/password[@database]

The permissible forms of `@``database` depend on whether you specify `-oci` or `-thin`:

- `-oci:@``database` is optional. If you do not specify, then the `dropjava` tool uses the user's default database. If specified, then `database` can be a TNS name or an Oracle Net Services name-value list.

- `-thin:@``database` is required. The format is `host``:``lport``:``SID`.

  where:

  - `host` is the name of the computer running the database.

  - `lport` is the listener port that has been configured to listen for Oracle Net Services connections. In a default installation, it is `5521`.

  - `SID` is the database instance identifier. In a default installation, it is `ORCL`.

The following are examples of the `dropjava` tool command:

- Drop all schema objects in the `TEST` schema in the default database that were loaded from `ServerObjects.jar`:

      dropjava -u HR -schema TEST ServerObjects.jar
      Password: password

- Connect with the JDBC Thin driver, then drop a class and a resource file from the user's schema:

      dropjava -thin -u HR@dbhost:5521:orcl alpha.class beta.props
      Password: password

#### List Based Deletion

Earlier versions of the `dropjava` tool required that the classes, JARs, source, and resources be present on the machine, where the client or server side utility is running. The current version of `dropjav`a has an option that enables you to drop classes, resources, or sources based on a list of classes, which may not exist on the client machine or the server machine. This list can be either on the command line or in a text file. For example:

    dropjava –list –u HR –v this.is.my.class this.is.your.class
    Password: password

The preceding command drops the classes `this.is.my.class` and `this.is.your.class` listed on the command line without them being present on the client machine or server machine.

    dropjava –listfile my.list –u HR –s –v
    Password: password

The preceding command drops classes, resources, or sources and their synonyms based on a list of classes listed in `my.list` and displays verbosely.

**Note:**

The `'-install'` flag ignores the loading and dropping of system owned schema objects that cannot be modified.

These schema objects are the runtime classes, and resources provided by the `CREATE JAVA COMMAND`.

### 12.7.4 About Dropping Resources Using dropjava Tool

Care must be taken if you are removing a resource that was loaded directly into the server. This includes profiles, if you translated them on the client without using the `-ser2class` option. When dropping source or class schema objects or resource schema objects that were generated by the server-side SQLJ translator, the schema objects will be found according to the package specification in the applicable `.sqlj `source file. However, the fully qualified schema object name of a resource that was generated on the client and loaded directly into the server depends on path information in the `.jar` file or that specified on the command line at the time you loaded it. If you use a `.jar` file to load resources and use the same `.jar` file to remove resources, then there will be no problem. However, if you use the command line to load resources, then you must be careful to specify the same path information when you run the `dropjava` tool to remove the resources.
