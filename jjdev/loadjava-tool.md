The `loadjava` tool creates schema objects from files and loads them into a schema. Schema objects can be created from Java source, class, and data files. The `loadjava` tool can also create schema objects from SQLJ files.

You must have the following SQL database privileges to load classes:

- `CREATE PROCEDURE` and `CREATE TABLE` privileges to load into your schema.

- `CREATE ANY PROCEDURE` and `CREATE ANY TABLE` privileges to load into another schema.

- `oracle.aurora.security.JServerPermission.loadLibraryInClass.``classname`.

You can run the `loadjava` tool either from the command line or by using the `loadjava` method contained in the `DBMS_JAVA` class. To run the tool from within your Java application, do the following:

    call dbms_java.loadjava('... options...');

The options are the same as those that can be specified on the command line with the `loadjava` tool. Separate each option with a space. Do not separate the options with a comma. The only exception for this is the `-resolver` option, which contains spaces. For `-resolver`, specify all other options in the first input parameter and the `-resolver` options in the second parameter, as follows:

    call dbms_java.loadjava('..options...', 'resolver_options');

Do not specify the `-thin`, `-oci`, `-user`, and `-password` options, because they relate to the database connection for the `loadjava` command-line tool. The output is directed to `stderr`. Set `serveroutput` on, and call `dbms_java.set_output`, as appropriate.

**Note:**

The `loadjava` tool is located in the `bin` directory under `$ORACLE_HOME`.

Just before the `loadjava` tool exits, it checks whether the processing was successful. All failures are summarized preceded by the following header:

    The following operations failed

Some conditions, such as losing the connection to the database, cause the `loadjava` tool to terminate prematurely. These errors are displayed with the following syntax:

    exiting: error_reason

This section covers the following:

- loadjava Tool Syntax

- loadjava Tool Argument Summary

- loadjava Tool Argument Details

### 12.6.1 loadjava Tool Syntax

The syntax of the `loadjava` tool command is as follows:

**Note:**

- The `(* -)` option is the preferred option over the `-genmissing` and `-genmissingjar` options for resolving class references.

- The the `-genmissing` and `-genmissingjar` options cannot be used in an option file or an option table. These options are applicable to all the classes to be loaded and cannot be used only for specific classes.

<!-- -->

    loadjava {-user | -u} user [@database] [options]
    file.java | file.class | file.jar | file.zip |
    file.sqlj | resourcefile | URL...
      [-casesensitivepub]
      [-cleargrants]
      [-debug]
      [-d | -definer]
      [-dirprefix prefix]
      [-e | -encoding encoding_scheme]
      [-fileout file]
      [-f | -force]
      [-genmissing]
      [-genmissingjar jar_file]
      [-g | -grant user [, user]...]
      [-help]
      [-jarasresource]
      [-noaction]
      [-nosynonym]
      [-nousage]
      [-noverify]
      [-o | -oci | oci8]
      [-optionfile file]
      [-optiontable table_name]
      [-publish package]
      [-pubmain number]
      [-recursivejars]
      [-r | -resolve]
      [-R | -resolver "resolver_spec"]
      [-resolveonly]
      [-S | -schema schema]
      [-stdout]
      [-stoponerror]
      [-s | -synonym]
      [-tableschema schema]
      [-t | -thin]

      [-unresolvedok]
      [-v | -verbose]
      [-jarsasdbobjects]
      [-prependjarnames]
      [-nativecompile]

### 12.6.2 loadjava Tool Argument Summary

Table 12-2 summarizes the `loadjava` tool command arguments. If you run the `loadjava` tool multiple times specifying the same files and different options, then the options specified in the most recent invocation hold. However, there are two exceptions to this, as follows:

- If the `loadjava` tool does not load a file because it matches a digest table entry, then most options on the command line have no effect on the schema object. The exceptions are `-grant` and `-resolve`, which always take effect. You must use the `-force` option to direct the `loadjava` tool to skip the digest table lookup.

- The `-grant` option is cumulative. Every user specified in every invocation of the `loadjava` tool for a given class in a given schema has the `EXECUTE` privilege.

Table 12-2 loadjava Argument Summary

| Argument                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|:----------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `filenames`                 | You can specify any number and combination of `.java`, `.class`, `.sqlj`, `.ser`, `.jar`, `.zip`, and resource file name arguments.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-proxy host:port`          | If you do not have physical access to the server host or the `loadjava` client for loading classes, resources, and Java source, then you can use an HTTP URL with the `loadjava` tool to specify the JAR, class file, or resource and load the class from a remote server. `host` is the host name or address and `port` is the port the proxy server is using. The URL implementation must be such that the `loadjava` tool can determine the type of file to load, that is, JAR, class, resource, or Java source. For example:<br>`loadjava –u HR –r –v –proxy proxy_server:1020 http://my.server.com/this/is /the/path/my.jar`<br>`Password: password`<br>When the URL support is used inside the server, you should have proper Java permissions to access to the remote source. The URL support also includes `ftp:` and `file:` URLs.                                                                                                                                                                       |
| `-casesensitivepub`         | Publishing will create case-sensitive names. Unless the names are already all uppercase, it will usually require quoting the names in PL/SQL.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-cleargrants`              | The `-grant` option causes the `loadjava` tool to grant `EXECUTE` privileges to classes, sources, and resources. However, it does not cause it to revoke any privileges. If `-cleargrants` is specified, then the `loadjava` tool will revoke any existing grants of execute privilege before it grants execute privilege to the users and roles specified by the `-grant` operand. For example, if the intent is to have execute privilege granted to only `HR`, then the proper options are:<br>`-grant HR -cleargrants`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-debug`                    | Turns on SQL logging.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-definer`                  | By default, class schema objects run with the privileges of their invoker. This option confers definer privileges upon classes instead. This option is conceptually similar to the UNIX `setuid` facility.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-dirprefix ``prefix`       | For any files or JAR entries that start with `prefix`, this `prefix` will be deleted from the name before the name of the schema object is determined. For classes and sources, the name of the schema object is determined by their contents. Therefore, this option will only have an effect for resources.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-encoding`                 | Identifies the source file encoding for the compiler, overriding the matching value, if any, in the `JAVA$OPTIONS` table. Values are the same as for the `javac -encoding` option. If you do not specify an encoding on the command line or in the `JAVA$OPTIONS` table, then the encoding is assumed to be the value returned by:<br>`System.getProperty("file.encoding");`<br>This option is relevant only when loading a source file.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-fileout ``file`           | Displays all message to the designated file.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-force`                    | Forces files to be loaded, even if they match digest table entries.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-genmissing`               | Determines what classes and methods are referred to by the classes that the `loadjava` tool is asked to process. Any classes not found in the database or file arguments are called missing classes. This option generates dummy definitions for missing classes containing all the referred methods. It then loads the generated classes into the database. This processing happens before the class resolution.<br>Because detecting references from source is more difficult than detecting references from class files, and because source is not generally used for distributing libraries, the `loadjava` tool will not attempt to do this processing for source files.<br>The schema in which the missing classes are loaded will be the one specified by the `-user` option, even when referring classes are created in some other schema. The created classes will be flagged so that tools can recognize them. In particular, this is needed, so that the verifier can recognize the generated classes. |
| `-genmissingjar ``jar_file` | This option performs the same actions as `-genmissing`. In addition, it creates a JAR file, `jar_file`, that contains the definitions of any generated classes.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-grant`                    | Grants the `EXECUTE` privilege on loaded classes to the listed users. Any number and combination of user names can be specified, separated by commas, but not spaces.<br>Granting the `EXECUTE` privilege on an object in another schema requires that the original `CREATE PROCEDURE` privilege was granted with the `WITH GRANT` options.<br>Note:<br>• `-grant` is a cumulative option. Users are added to the list of those with the `EXECUTE` privilege. To remove privileges, use the `-cleargrants` option.<br>• The schema name should be used in uppercase.                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-help`                     | Displays usage message on how to use the `loadjava` tool and its options.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-jarasresource`            | Instead of unpacking the JAR file and loading each class within it, loads the whole JAR file into the schema as a resource.<sup>Foot 1</sup>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-noaction`                 | Take no action on the files. Actions include creating the schema objects, granting execute permissions, and so on. The typical use is within an option file to suppress creation of specific classes in a JAR. When used on the command line, unless overridden in the option file, it will cause the `loadjava` tool to ignore all files. Except that JAR files will still be examined to determine if they contain a `META-INF/loadjava-options` entry. If so, then the option file is processed. The `-action` option in the option file will override the `-noaction` option specified on the command line.                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-norecursivejars`          | Treat JAR files contained in other JAR files as resources. This is the default behavior. This option is used to override the `-recursivejars` option.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-nosynonym`                | Do not create a public synonym for the classes. This is the default behavior. This overrides the `-synonym` option.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-nousage`                  | Suppresses the usage message that is given if either no option is specified or if the `-help` option is specified.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-noverify`                 | Causes the classes to be loaded without bytecode verification. `oracle.aurora.security.JServerPermission(Verifier) must be granted `to use this option. To be effective, this option must be used in conjunction with `-resolve`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-oci | -oci8`              | Directs the `loadjava` tool to communicate with the database using the JDBC Oracle Call Interface (OCI) driver. `-oci` and `-thin` are mutually exclusive. If neither is specified, then `-oci` is used by default. Choosing `-oci` implies the syntax of the `-user` value. You do not need to provide the URL.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-optionfile ``file`        | A file can be provided with `loadjava` options.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-optiontable ``tablename`  | This option works like `-optionfile`, except that the source for the patterns and options is a SQL table rather than a file.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-publish ``package`        | The `package` is created or replaced by the `loadjava` tool. Wrappers for the eligible methods will be defined in this package. Through the use of option files, a single invocation of the `loadjava` tool can be instructed to create more than one package. Each package will undergo the same name transformations as the methods.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-pubmain ``number`         | A special case applied to methods with a single argument, which is of type `java.lang.String[]`. Multiple variants of the SQL procedure or function will be created, each of which takes a different number of arguments of type `VARCHAR`. In particular, variants are created taking all arguments up to and including `number`. The default value is `3`. This option applies to `main`, as well as any method that has exactly one argument of type `java.lang.String[]`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-recursivejars`            | Usually, if the `loadjava` tool encounters an entry in a JAR with a `.jar` extension, it will load the entry as a resource. If this option is specified, then the `loadjava` tool will process contained JAR files as if they were top-level JAR files. That is, it will read their entries and load classes, sources, and resources.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-resolve`                  | Compiles, if necessary, and resolves external references in classes after all classes on the command line have been loaded. If you do not specify the `-resolve` option, the `loadjava` tool loads files, but does not compile or resolve them.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-resolver`                 | Specifies an explicit resolver specification, which is bound to the newly loaded classes. If `-resolver` is not specified, then the default resolver specification, which includes current user's schema and `PUBLIC`, is used.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-resolveonly`              | Causes the `loadjava` tool to skip the initial creation step. It will still perform grants, resolves, create synonyms, and so on.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-schema`                   | Designates the schema where schema objects are created. If not specified, then the `-user` schema is used. To create a schema object in a schema that is not your own, you must have the following privileges:<br>• `CREATE TABLE` or `CREATE ANY TABLE`<br>• `CREATE INDEX` or `CREATE ANY INDEX`<br>• `SELECT ANY TABLE`<br>• `UPDATE ANY TABLE`<br>• `INSERT ANY TABLE`<br>• `DELETE ANY TABLE`<br>• `CREATE PROCEDURE or CREATE ANY PROCEDURE`<br>• `ALTER ANY PROCEDURE`<br>Finally, you must have the `JServerPermission loadLibraryInClass` for the class.<br>Note: The above-mentioned privileges allow the grantee to create and manipulate tables in any schema except the SYS schema. For security reasons, Oracle recommends that you use these settings only with great caution.                                                                                                                                                                                                                     |
| `-stdout`                   | Causes the output to be directed to `stdout`, rather than to `stderr`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-stoponerror`              | Usually, if an error occurs while the `loadjava` tool is processing files, it will issue a message and continue to process other classes. This option stops when an error occurs. In addition, it reports all errors that apply to Java objects and are contained in the `USER_ERROR` table of the schema in which classes are being loaded. Except that is does not report `ORA-29524` errors. These are errors that are generated when a class cannot be resolved, because a referred class could not be resolved. Therefore, these errors are a secondary effect of whatever caused a referred class to be unresolved.                                                                                                                                                                                                                                                                                                                                                                                         |
| `-synonym`                  | Creates a `PUBLIC` synonym for loaded classes making them accessible outside the schema into which they are loaded. To specify this option, you must have the `CREATE PUBLIC SYNONYM` privilege. If `-synonym` is specified for source files, then the classes compiled from the source files are treated as if they had been loaded with `-synonym`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-tableschema ``schema`     | Creates the `loadjava` tool internal tables within the specified schema, rather than in the Java file destination schema.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-thin`                     | Directs the `loadjava` tool to communicate with the database using the JDBC Thin driver. Choosing `-thin` implies the syntax of the `-user` value. You do need to specify the appropriate URL through the `-user` option.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-unresolvedok`             | When combined with `-resolve`, will ignore unresolved errors.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-user`                     | Specifies a user name, password, and database connection string. The files will be loaded into this database instance.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-verbose`                  | Directs the `loadjava` tool to display detailed status messages while running. Use the `-verbose` option to learn when the `loadjava` tool does not load a file, because it matches a digest table entry.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-jarsasdbobjects`          | Indicates that JARs processed by the current `loadjava` tool command are to be stored in the database as database resident JARs.<sup>Foot 2</sup>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-prependjarnames`          | Is used with the `-jarsasdbobjects `option. This option enables classes with the same names coming from different JARs to coexist in the same schema. It does this by prefixing a version of the name of the JAR to the class name to produce a unique name for the database object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

<sup>Footnote 1</sup>

If you load a JAR file in this manner, then you cannot use it for resolution or execution.

<sup>Footnote 2</sup>

If you load a JAR file in this manner, then you can use it for resolution or execution.

### 12.6.3 loadjava Tool Argument Details

This section describes the details of some of the `loadjava` tool arguments whose behavior is more complex than the summary descriptions contained in the loadjava Argument Summary table.

#### File Names

You can specify as many `.class`, `.java`, `.sqlj`, `.jar`, `.zip`, and resource files as you want and in any order. If you specify a JAR or ZIP file, then the `loadjava` tool processes the files in the JAR or ZIP. There is no JAR or ZIP schema object. If a JAR or ZIP contains another JAR or ZIP, the `loadjava` tool does not process them.

The best way to load files is to put them in a JAR or ZIP and then load the archive. Loading archives avoids the resource schema object naming complications. If you have a JAR or ZIP that works with the Java Development Kit (JDK), then you can be sure that loading it with the `loadjava` tool will also work, without having to learn anything about resource schema object naming.

Schema object names are different from file names, and the `loadjava` tool names different types of schema objects differently. Because class files are self-identifying, the mapping of class file names to schema object names done by the `loadjava` tool is invisible to developers. Source file name mapping is also invisible to developers. The `loadjava` tool gives the schema object the fully qualified name of the first class defined in the file. JAR and ZIP files also contain the names of their files.

However, resource files are not self identifying. The `loadjava` tool generates Java resource schema object names from the literal names you supply as arguments. Because classes use resource schema objects and the correct specification of resources is not always intuitive, it is important that you specify resource file names correctly on the command line.

The perfect way to load individual resource files correctly is to run the `loadjava` tool from the top of the package tree and specify resource file names relative to that directory.

**Note:**

The top of the package tree is the directory you would name in a `CLASSPATH`.

If you do not want to follow this rule, then observe the details of resource file naming that follow. When you load a resource file, the `loadjava` tool generates the resource schema object name from the resource file name, as literally specified on the command line. For example, if you type:

    % cd /home/HR/javastuff
    % loadjava options alpha/beta/x.properties
    % loadjava options /home/HR/javastuff/alpha/beta/x.properties

Although you have specified the same file with a relative and an absolute path name, the `loadjava` tool creates two schema objects, `alpha/beta/x.properties` and `ROOT/home/HR/javastuff/alpha/beta/x.properties`. The name of the resource schema object is generated from the file name as entered.

Classes can refer to resource files relatively or absolutely. To ensure that the `loadjava` tool and the class loader use the same name for a schema object, enter the name on the command line, which the class passes to `getResource()` or `getResourceAsString()`.

Instead of remembering whether classes use relative or absolute resource names and changing directories so that you can enter the correct name on the command line, you can load resource files in a JAR, as follows:

    % cd /home/HR/javastuff
    % jar -cf alpharesources.jar alpha/*.properties
    % loadjava options alpharesources.jar

To simplify the process further, place both the class and resource files in a JAR, which makes the following invocations equivalent:

    % loadjava options alpha.jar
    % loadjava options /home/HR/javastuff/alpha.jar

The preceding `loadjava` tool commands imply that you can use any path name to load the contents of a JAR file. Even if you run the redundant commands, the `loadjava` tool would realize from the digest table that it need not load the files twice. This implies that reloading JAR files is not as time-consuming as it might seem, even when few files have changed between the different invocations of the `loadjava` tool.

#### definer

    {-definer | -d}

This option is identical to the definer rights in stored procedures and is conceptually similar to the UNIX `setuid` facility. However, you can apply the `-definer` option to individual classes, in contrast to `setuid`, which applies to a complete program. Moreover, different definers may have different privileges. Because an application can consist of many classes, you must apply `-definer` with care to achieve the desired results. That is, classes run with the privileges they need, but no more.

#### noverify

    [-noverify]

This option causes the classes to be loaded without bytecode verification. `oracle.aurora.security.JServerPermission(Verifier)` must be granted to run this option. Also, this option must be used in conjunction with `-resolve`.

The verifier ensures that incorrectly formed Java binaries cannot be loaded for running on the server. If you know that the JAR or classes you are loading are valid, then the use of this option will speed up the process associated with the `loadjava` tool. Some Oracle Database-specific optimizations for interpreted performance are put in place during the verification process. Therefore, the interpreted performance of your application may be adversely affected by using this option.

#### optionfile

    [-optionfile <file>]

This option enables you to specify a file with different options that you can specify with the `loadjava` tool. This file is read and processed by the `loadjava` tool before any other `loadjava` tool options are processed. The file can contain one or more lines, each of which contains a pattern and a sequence of options. Each line must be terminated by a newline character (`\n`).

For each file or JAR entry that is processed by the `loadjava` tool, the long name of the schema object that is going to be created is checked against the patterns. Patterns can end in a wildcard (`*`) to indicate an arbitrary sequence of characters, or they must match the name exactly.

Options to be applied to matching Java schema objects are supplied on the rest of the line. Options are appended to the command-line options, they do not replace them. In case more than one line matches a name, the matching rows are sorted by length of pattern, with the shortest first, and the options from each row are appended. In general, the `loadjava` tool options are not cumulative. Rather, later options override earlier ones. This means that an option specified on a line with a longer pattern will override a line with a shorter pattern.

This file is parsed by a `java.io.StreamTokenizer`.

You can use Java comments in this file. A line comment begins with a `#`. Empty lines are ignored. The quote character is a double quote (`"`). That is, options containing spaces should be surrounded by double quotes. Certain options, such as `-user` and `-verbose`, affect the overall processing of the `loadjava` tool and not the actions performed for individual Java schema objects. Such options are ignored if they appear in an option file.

To help package applications, the `loadjava` tool looks for the `META-INF/loadjava-options` entry in each JAR it processes. If it finds such an entry, then it treats it as an options file that is applied for all other entries in the JAR file. However, the `loadjava` tool does some processing on entries in the order in which they occur in the JAR.

If the `loadjava` tool has partially processed entities before it processes `META-INF/loadjava-options`, then it attempts to patch up the schema object to conform to the applicable options. For example, the `loadjava` tool alters classes that were created with invoker rights when they should have been created with definer rights. The fix for `-noaction` is to drop the created schema object. This yields the correct effect, except that if a schema object existed before the `loadjava` tool started, then it would have been dropped.

#### optiontable

    [-optiontable table_name]

This option enables you to specify the properties of classes persistently. No mechanism is provided for loading the table. The table name must contain three character columns, PATTERN, OPTION, and VALUE. The value of PATTERN is interpreted in the same way as a pattern in an option file. The other two columns are the same as the corresponding command-line options and take an operand. Suppose, you create a table FOO with the following command:

    create table foo (pattern varchar2(2000), option_name varchar2(2000), value varchar2(2000));

Then, you can use the `optiontable` option in the following way:

    loadjava -optiontable foo myjar.jar

For options that do not take an operand, the VALUE column should be NULL. The rows are processed in the same way as the lines of an option file are processed. To determine the options for a given schema object, the rows are examined and for any match the option is appended to the list of options. If two rows have the same pattern and contradictory options, such as -synonym and -nosynonym, then it is unspecified which will prevail. If two rows have the same pattern and option columns, then it is unspecified which VALUE will prevail.

#### publish

    [-publish <package>]
    [-pubmain <number>]

The publishing options cause the `loadjava` tool to create PL/SQL wrappers for methods contained in the processed classes. Typically, a user wants to publish wrappers for only a few classes in a JAR. These options are most useful when specified in an option file.

To be eligible for publication, the method must satisfy the following:

- It must be a member of a `public` class.

- It must be declared `public` and `static`.

- The method signature should satisfy the following rules so that it can be mapped:

  - Java arithmetic types for arguments and return values are mapped to `NUMBER`.

  - `char` as an argument and return type is mapped to `VARCHAR`.

  - `java.lang.String` as an argument and return type is mapped to `VARCHAR`.

  - If the only argument of the method has type `java.lang.String`, special rules apply, as listed in the `-pubmain` option description.

  - If the return type is `void`, then a procedure is created.

  - If the return type is an arithmetic, `char`, or `java.lang.String` type, then a function is created.

Methods that take arguments or return types that are not covered by the preceding rules are not eligible. No provision is made for `OUT` and `IN OUT` SQL arguments, `OBJECT` types, and many other SQL features.

#### resolve

    {-resolve | -r}

Use `-resolve` to force the `loadjava` tool to compile and resolve a class that has previously been loaded. It is not necessary to specify `-force`, because resolution is performed after, and independent of, loading.

#### resolver

    {-resolver | -R} resolver_specification

This option associates an explicit resolver specification with the class schema objects that the `loadjava` tool creates or replaces.

A resolver specification consists of one or more items, each of which consists of a name specification and a schema specification expressed in the following syntax:

    "((name_spec schema_spec) [(name_spec schema_spec)] ...)"

A name specification is similar to a name in an `import` statement. It can be a fully qualified Java class name or a package name whose final element is the wildcard character asterisk (`*`) or simply an asterisk (`*`). However, the elements of a name specification must be separated by slashes (`/`), not periods (`.`). For example, the name specification `a/b/*` matches all classes whose names begin with `a.b`. The special name `*` matches all class names.

A schema specification can be a schema name or the wildcard character dash (`-`). The wildcard does not identify a schema, but directs the resolve operation not to mark a class invalid, because a reference to a matching name cannot be resolved. Use dash (`-`) when you must test a class that refers to a class you cannot or do not want to load. For example, GUI classes that a class refers to but does not call, because when run in the server there is no GUI.

When looking for a schema object whose name matches the name specification, the resolution operation looks in the schema named by the partner schema specification.

The resolution operation searches schemas in the order in which the resolver specification lists them. For example,

    -resolver '((* HR) (* PUBLIC))'

This implies that search for any reference first in `HR` and then in `PUBLIC`. If a reference is not resolved, then mark the referring class invalid and display an error message.

Consider the following example:

    -resolver "((* HR) (* PUBLIC) (my/gui/* -))"

This implies that search for any reference first in `HR` and then in `PUBLIC`. If the reference is to a class in the package `my.gui` and is not found, then mark the referring class valid and do not display an error. If the reference is not to a class in `my.gui` and is not found, then mark the referring class invalid and produce an error message.

#### user

    {-user | -u} user/password[@database_url]

By default, the `loadjava` tool loads into the logged in schema specified by the `-user` option. You use the `-schema` option to specify a different schema to load into. This does not require you to log in to that schema, but does require that you have sufficient permissions to alter the schema.

The permissible forms of `@``database_url` depend on whether you specify `-oci` or `-thin`, as described:

- `-oci:@``database_url` is optional. If you do not specify, then the `loadjava` tool uses the user's default database. If specified, `database_url` can be a TNS name or an Oracle Net Services name-value list.

- `-thin:@``database_url` is required. The format is `host``:``lport``:``SID`.

  where:

  - `host` is the name of the computer running the database.

  - `lport` is the listener port that has been configured to listen for Oracle Net Services connections. In a default installation, it is `5521`.

  - `SID` is the database instance identifier. In a default installation, it is `ORCL`.

The following are examples of the `loadjava` tool commands:

- Connect to the default database with the default OCI driver, load the files in a JAR into the `TEST` schema, and then resolve them:

      loadjava -u joe -resolve -schema TEST ServerObjects.jar
      Password: password

- Connect with the JDBC Thin driver, load a class and a resource file, and resolve each class:

      loadjava -thin -u HR@dbhost:5521:orcl \
        -resolve alpha.class beta.props
      Password: password

- Add Betty and Bob to the users who can run `alpha.class`:

      loadjava -thin -schema test -u HR@localhost:5521:orcl \
        -grant BETTY,BOB alpha.class
      Password: password

#### jarsasdbobjects

This option indicates that JARs processed by the current `loadjava` tool are to be stored in the database along with the classes they contain, and knowledge of the association between the classes and the JAR is to be retained in the database. In other words, this argument indicates that the JARs processed by the current `loadjava` tool are to be stored in the database as database resident JARs.

#### prependjarnames

This option is used with the `-jarsasdbobjects` option. This option enables classes with the same names coming from different JARs to coexist in the same schema.

**Related Topics**

- [Overview of Controlling the Current User](preparing-Java-class-methods.md)
