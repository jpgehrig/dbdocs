This chapter discusses internal operations and functionality of Oracle SQLJ translator and run time.

The following topics are covered:

- Internal Translator Operations

- Functionality of Translator Errors\_ Messages\_ and Exit Codes

- SQLJ Run Time

- Globalization Support in the Translator and Run Time

### 10.1 Internal Translator Operations

The following topics summarize the operations executed by the SQLJ translator during a translation:

- Java and SQLJ Code-Parsing and Syntax-Checking

- SQL Semantics-Checking and Offline Parsing

- Code Generation

- Java Compilation

- Profile Customization (ISO Code Generation)

#### 10.1.1 Java and SQLJ Code-Parsing and Syntax-Checking

In this first phase of SQLJ translation, a SQLJ parser and a Java parser are used to process all the source code and check syntax. As the SQLJ translator parses the `.sqlj` file, it invokes a Java parser to check the syntax of Java statements and a SQLJ parser to check the syntax of SQLJ constructs (anything preceded by `#sql`). The SQLJ parser also invokes the Java parser to check the syntax of Java host variables and expressions within SQLJ executable statements.

The SQLJ parser checks the grammar of SQLJ constructs according to the SQLJ language specification. However, it does not check the grammar of the embedded SQL operations. SQL syntax is not checked until the semantics-checking or offline parsing step.

This syntax-check will look for errors like missing semi-colons, mismatched curly braces, and obvious type mismatches, such as multiplying a number by a string. If the parsers find any syntax errors or type mismatches during this phase, then the translation is aborted and the errors are reported to the user.

#### 10.1.2 SQL Semantics-Checking and Offline Parsing

Once the SQLJ and Java application source code is verified as syntactically correct, the translator enters into the semantics-checking phase and invokes a SQL semantics-checker or a SQL offline parser or both, according to SQLJ option settings.

Setting the `-user` option enables online checking, and setting the `-password` and `-url` options specifies the database connection, if the password and URL were not specified in the `-user` option. The `-offline` or `-online` option specifies which checker to use. The default, typically sufficient, is a checker front end called `OracleChecker` that chooses the most appropriate checker, according to whether you have enabled online checking and which Java Database Connectivity (JDBC) driver you are using.

The `-parse` option, `true` by default, is for enabling the offline parser, which offers a way to verify SQL and PL/SQL syntax (but not data types against database columns) without necessitating a database connection during translation. Note that some settings of the `-parse` option will override the `-user` option and disable online checking.

**See Also:**

"[Connection Options](translator-command-line-and-options.md)" and "[Semantics-Checking and Offline-Parsing Options](translator-command-line-and-options.md)"

**Note:**

For ISO code generation, semantics-checking can also be performed on a profile that was produced during a previous execution of the SQLJ translator. Refer to "[SQLCheckerCustomizer for Profile Semantics-Checking](appendix.md)".

The following tasks are always performed during semantics-checking, regardless of the status of online checking or offline parsing:

1.  SQLJ analyzes the types of Java expressions in your SQLJ executable statements.

    This includes examining the SQLJ source files being translated, any `.java` files entered on the command line, and any imported Java classes whose `.class` files or `.java` files can be found through the classpath. SQLJ examines whether and how stream types are used in `SELECT` or `CAST` statements, what Java types are used in iterator columns or `INTO`-lists, what Java types are used as input host variables, and what Java types are used as output host variables.

    SQLJ also processes `FETCH`, `CAST`, `CALL`, `SET TRANSACTION`, `VALUES`, and `SET` statements syntactically.

    Any Java expression in a SQLJ executable statement must have a Java type valid for the given situation and usage. For example, consider the following statement:

        #sql [myCtx] { UPDATE ... };

    The `myCtx` variable, which might be used to specify a connection context instance or execution context instance for this statement, must actually resolve to a SQLJ connection context type or execution context type.

    Now consider the following example:

        #sql { UPDATE employees SET salary = :newSal };

    If `newSal` is a variable, as opposed to a field, then an error is generated if `newSal` was not previously declared. In any case, an error is generated if it cannot be assigned to a valid Java type or its Java type cannot be used in a SQL statement (for example, `java.util.Vector`).

    **Note:**

    Semantics-checking of Java types is performed only for Java expressions within SQLJ executable statements. Such errors in your standard Java statements will not be detected until compilation by the Java compiler.

2.  SQLJ tries to categorize your embedded SQL operations. Each operation must have a recognizable keyword, such as `SELECT` or `INSERT`, so that SQLJ knows what kind of operation it is. For example, the following statement will generate an error:

        #sql { foo };

3.  If either online checking or offline parsing (or both) is enabled, then SQLJ analyzes and verifies the syntax of embedded SQL and PL/SQL operations.

4.  If either online checking or offline parsing (or both) is enabled, then SQLJ checks the types of Java expressions in SQLJ executable statements against SQL types of corresponding columns in the database and SQL types of corresponding arguments and return variables of stored procedures and functions.

    In the process of doing this, SQLJ verifies that the SQL entities used in your SQLJ executable statements, such as tables, views, and stored procedures, actually exist in the database. SQLJ also checks nullability of database columns whose data is being selected into iterator columns of Java primitive types, which cannot process null data. However, nullability is not checked for stored procedure and function output parameters and return values.

#### 10.1.3 Code Generation

For the `.sqlj` application source file, the SQLJ translator generates a `.java` file and, for ISO standard SQLJ code generation, at least one profile (either in `.ser` or `.class` files). The `.java` contains your translated application source code, class definitions for any private iterators and connection contexts you declared, and, for ISO code, a profile-keys class definition generated and used internally by SQLJ.

**Note:**

No profiles or profile-keys class are generated if you use the default Oracle-specific code generation mode.

With ISO code generation, there are no profiles or profile-keys class if you do not use any SQLJ executable statements in your code.

##### Generated Application Code in .java File

For the default Oracle-specific code generation, the generated `.java` file for your application contains direct calls to Oracle JDBC driver in place of the original SQLJ executable statements. There are also calls to an Oracle-specific SQLJ run time. For ISO standard SQLJ code generation, SQLJ executable statements are replaced by calls to the SQLJ run time, which in turn contains calls to the JDBC driver.

For convenience, generated `.java` files also include a comment for each of your `#sql` statements, repeating the statement in its entirety for reference. The generated `.java` file will have the same base name as the input `.sqlj` file, which would be the name of the public class defined in the `.sqlj` file or the first class defined if there are no public classes. For example, `Foo.sqlj` defines the `Foo` class. The `Foo.java` source file will be generated by the translator.

The location of the generated `.java` file depends on whether and how you set the SQLJ `-dir` option. By default, the `.java` file will be placed in the directory of the `.sqlj` input file.

**See Also:**

"[Output Directory for Generated .java Files (-dir)](translator-command-line-and-options.md)"

##### Generated Profile-Keys Class in .java File (ISO Code Generation)

If you use ISO standard SQLJ code generation, SQLJ generates a profile-keys class that it uses internally during run time to load and access the serialized profile. This class contains mapping information between the SQLJ run time calls in your translated application and the SQL operations placed in the serialized profile. It also contains methods to access the serialized profile.

**Note:**

If you use the default Oracle-specific code generation, no profiles or profile-keys classes are generated.

The profile-keys class is defined in the same `.java` output file that has your translated application source code, with a class name based on the base name of your `.sqlj` source file as follows:

    Basename_SJProfileKeys

For example, translating `Foo.sqlj` defines the following profile-keys class in the generated `.java` file:

    Foo_SJProfileKeys

If your application is in a package, this is reflected appropriately. For example, translating `Foo.sqlj` in the `a.b` package defines the following class:

    a.b.Foo_SJProfileKeys

##### Generated Profiles in .ser or .class Files (ISO Code Generation)

If you use ISO standard SQLJ code generation, SQLJ generates profiles that it uses to store information about the SQL operations found in the input file. A profile is generated for each connection context class that you use in your application. It describes the operations to be performed using instances of the associated connection context class, such as SQL operations to execute, tables to access, and stored procedures and functions to call.

**Note:**

If you use the default Oracle-specific code generation, then information about the SQL operations is embedded in the generated code, which calls Oracle JDBC driver directly. In this case, SQLJ does not generate profiles.

Profiles are generated in `.ser` serialized resource files. However, if you enable the SQLJ `-ser2class` option, then the profiles are automatically converted to `.class` files as part of the translation. In this case, no further customization of the profile is possible. You would have to delete the `.class` file and rerun the SQLJ translator to regenerate the profile.

Profile base names are generated similarly to the profile-keys class name. They are fully qualified with the package name, followed by the `.sqlj` file base name, followed by the string:

    _SJProfilen

Where `n` is a unique number, starting with 0, for each profile generated for a particular `.sqlj` input file.

Again using the example of the `Foo.sqlj` input file, if two profiles are generated, then they will have the following base names (presuming no package):

    Foo_SJProfile0
    Foo_SJProfile1

If `Foo.sqlj` is in the `a.b` package, then the profile base names will be:

    a.b.Foo_SJProfile0
    a.b.Foo_SJProfile1

Physically, a profile exists as a Java serialized object contained within a resource file. Resource files containing profiles use the `.ser` extension and are named according to the base name of the profile (excluding package names). Resource files for the two previously mentioned profiles will be named as follows:

    Foo_SJProfile0.ser
    Foo_SJProfile1.ser

Or, they will be named `Foo_SJProfile0.class` and `Foo_SJProfile1.class` if you enable the `-ser2class` option. If you choose this option, then the conversion to `.class` takes place after the customization step.

**See Also:**

"[Conversion of .ser File to .class File (-ser2class)](translator-command-line-and-options.md)"

The location of these files depends on how the SQLJ `-d` option is set, which determines where all generated `.ser` and `.class` files are placed.

**See Also:**

"[Output Directory for Generated .ser and .class Files (-d)](translator-command-line-and-options.md)"

##### More About Generated Calls to SQLJ Run Time

When `#sql` statements are replaced by calls to the JDBC driver (for Oracle-specific code generation) or to the SQLJ run time (for ISO standard SQLJ code generation), these calls implement the steps in Table 10-1.

Table 10-1 Steps for Generated Calls, ISO Standard Versus Oracle-Specific

| Steps for ISO Standard Code Generation                                                                 | Steps for Oracle Code Generation                                                               |
|:-------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------|
| Get a SQLJ statement object, using information stored in the associated profile entry.                 | Get an Oracle JDBC statement object.                                                           |
| Bind inputs into the statement, using `set``XXX``()` methods of the statement object.                  | Bind inputs using Oracle JDBC statement methods and, if necessary, register output parameters. |
| Execute the statement, using the `executeUpdate()` or `executeQuery()` method of the statement object. | Execute the Oracle statement.                                                                  |
| Create iterator instances, if applicable.                                                              | Create iterator instances, if applicable.                                                      |
| Retrieve outputs from the statement, using `get``XXX``()` methods of the statement object.             | Retrieve outputs from the statement using appropriate JDBC getter methods.                     |
| Close the SQLJ statement object (by default, recycling it through the SQLJ statement cache).           | Close the JDBC statement object (by default, recycling it through the JDBC statement cache).   |

A SQLJ run time uses SQLJ statement objects that are similar to JDBC statement objects, although a particular implementation of SQLJ might or might not use JDBC statement classes directly. SQLJ statement classes add functionality particular to SQLJ. For example:

- Standard SQLJ statement objects raise a SQL exception if a null value from the database is to be output to a primitive Java type, such as `int` or `float`, which cannot take null values.

- Oracle SQLJ statement objects allow user-defined object and collection types to be passed to or retrieved from Oracle Database.

#### 10.1.4 Java Compilation

After code generation, SQLJ invokes the Java compiler to compile the generated `.java` file. This produces a `.class` file for each class you defined in your application, including iterator and connection context declarations, as well as a `.class` file for the generated profile-keys class if you use ISO code generation (and presuming your application uses SQLJ executable statements). Any `.java` files you specified directly on the SQLJ command line (for type-resolution, for example) are compiled at this time as well.

In the example used in "Code Generation", the following `.class` files would be produced in the appropriate directory (given package information in the source code):

- `Foo.class`

- `Foo_SJProfileKeys.class` (ISO code generation only)

- A `.class` file for each additional class you defined in `Foo.sqlj`

- A `.class` file for each iterator and connection context class you declared in `Foo.sqlj` (whether public or private)

To ensure that `.class` files and profiles (if any, whether `.ser` or `.class`) will be located in the same directory, SQLJ passes its `-d` option to the Java compiler. If the `-d` option is not set, then `.class` files and profiles are placed in the same directory as the generated `.java` file, which is placed according to the `-dir` option setting.

In addition, so that SQLJ and the Java compiler will use the same encoding, SQLJ passes its `-encoding` option to the Java compiler unless the SQLJ `-compiler-encoding-flag` is turned off. If the `-encoding` option is not set, then SQLJ and the compiler will use the setting in the Java virtual machine (JVM) `file.encoding` property.

By default, SQLJ invokes the standard `javac` compiler of the Sun Microsystems Java Development Kit (JDK), but other compilers can be used instead. You can request that an alternative Java compiler be used by setting the SQLJ `-compiler-executable` option.

**Note:**

If you are using the SQLJ `-encoding` option but using a compiler that does not have an `-encoding` option, then turn off the SQLJ `-compiler-encoding-flag`. Otherwise, SQLJ will attempt to pass the `-encoding` option to the compiler.

#### 10.1.5 Profile Customization (ISO Code Generation)

After Java compilation, if you are using ISO standard code generation, then the generated profiles containing information about your embedded SQL instructions are customized, so that your application can work efficiently with your database and use vendor-specific extensions.

**Note:**

If you use the default Oracle-specific code generation, then SQLJ produces no profiles and skips the customization step. Your code will support Oracle-specific features through direct calls to Oracle JDBC application programming interfaces (APIs).

If you want to check for the options already set on the customizer, then you can make use of the following command:

    % sqlj -P-print *.ser

For more information about profile print option, refer to "[Specialized Customizer: Profile Print Option (print)](appendix.md)".

To accomplish customization, SQLJ invokes a front end called the customizer harness, which is a Java class that functions as a command-line utility. The harness, in turn, invokes a particular customizer, either the default Oracle customizer or a customizer that you specify through SQLJ option settings.

During customization, profiles are updated in the following ways:

- To enable your application to use any vendor-specific database types or features, if applicable

- To tailor the profiles so that your application is as efficient as possible in using features of the relevant database environment

Without customization, you can access and use only standard JDBC types.

For example, Oracle customizer can update a profile to support a SQL `PERSON` type that you had defined. You could then use `PERSON` as you would any other supported data type.

You must also customize with Oracle customizer to use any of the `oracle.sql` type extensions.

**Note:**

Be aware of the following regarding profile customization:

- Oracle SQLJ run time and an Oracle JDBC driver will be required by your application whenever you use Oracle customizer during translation, even if you do not use Oracle extensions in your code.

- The generic SQLJ run time will be used if your application has no customizations, or none suitable for the connection.

- You can customize previously created profiles by specifying `.ser` files, or `.jar` files containing `.ser` files, on the command line. But you cannot do this in the same running of SQLJ where translations are taking place. You can specify `.ser`/`.jar` files to be customized or `.sqlj`/`.java` files to be translated, compiled, and customized, but not both categories. For more information about how `.jar` files are used, refer to "[JAR Files for Profiles](appendix.md)".

### 10.2 Functionality of Translator Errors, Messages, and Exit Codes

This section provides an overview of SQLJ translator messages and exit codes. It covers the following topics:

- Translator Error\_ Warning\_ and Information Messages

- Translator Status Messages

- Translator Exit Codes

#### 10.2.1 Translator Error, Warning, and Information Messages

There are three major levels of SQLJ messages that you may encounter during the translation phase: error, warning, and information. Warning messages can be further broken down into two levels: nonsuppressible and suppressible. Therefore, there are four message categories (in order of seriousness):

1.  Errors

2.  Nonsuppressible warnings

3.  Suppressible warnings

4.  Information

You can control suppressible warnings and information by using the SQLJ `-warn` option.

Error messages, prefixed by `Error:`, indicate that one of the following has been encountered:

- A condition that would prevent compilation (for example, the source file contains a public class whose name does not match the base file name)

- A condition that would result in a run-time error if the code were executed (for example, the code attempts to fetch a `VARCHAR` into a `java.util.Vector`, using an Oracle JDBC driver)

If errors are encountered during SQLJ translation, then no output is produced and compilation and customization are not executed.

Nonsuppressible warning messages, prefixed by `Warning:`, indicate that one of the following has been encountered:

- A condition that would probably, but not necessarily, result in a run-time error if the code were executed (for example, a `SELECT` statement whose output is not assigned to anything)

- A condition that compromises the ability of SQLJ to verify run-time aspects of your source code (for example, not being able to connect to the database you specify for online checking)

- A condition that presumably resulted from a coding error or oversight

SQLJ translation will complete if a nonsuppressible warning is encountered, but you should analyze the problem and determine if it should be fixed before running the application. If online checking is specified but cannot be completed, then offline checking is performed instead.

**Note:**

For logistical reasons, the parser that the SQLJ translator uses to analyze SQL operations is not the same top-level SQL parser that will be used at run time. Therefore, errors might occasionally be detected during translation that will not actually cause problems when your application runs. Accordingly, such errors are reported as nonsuppressible warnings, rather than fatal errors.

Suppressible warning messages, also prefixed by `Warning:`, indicate that there is a problem with a particular aspect of your application, such as portability. An example of this is using an Oracle-specific type, such as `oracle.sql.NUMBER`, to read from or write to Oracle Database 12c Release 1 (12.1).

Informational or status messages prefixed by `Info:` do not indicate an error condition. They merely provide additional information about what occurred during the translation phase.

Suppressible warning and status messages can be suppressed by using the various `-warn` option flags:

- `cast/nocast`: The `nocast` setting suppresses warnings about possible run-time errors when trying to cast an object type instance to an instance of a subtype.

- `precision/noprecision`: The `noprecision` setting suppresses warnings regarding possible loss of data precision during conversion.

- `nulls/nonulls`: The `nonulls` setting suppresses warnings about possible run-time errors due to nullable columns or types.

- `portable/noportable`: The `noportable` setting suppresses warnings regarding SQLJ code that uses Oracle-specific features or might otherwise be nonstandard and, therefore, not portable to other environments.

- `strict/nostrict`: The `nostrict` setting suppresses warnings issued if there are fewer columns in a named iterator than in the selected data that is to populate the iterator.

- `verbose/noverbose`: The `noverbose` setting suppresses status messages that are merely informational and do not indicate error or warning conditions.

If you receive warnings during your SQLJ translation, then you can try running the translator again with `-warn=none` to see if any of the warnings are of the more serious (nonsuppressible) variety.

The following table summarizes the categories of error and status messages generated by the SQLJ translator.

Table 10-2 SQLJ Translator Error Message Categories

| Message Category             | Prefix     | Indicates                                                                                          | Suppressed By                                                          |
|:-----------------------------|:-----------|:---------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------|
| Error                        | `Error:`   | Fatal error that will cause compilation failure or run-time failure (translation aborted)          | NA                                                                     |
| Nonsuppressible warning      | `Warning`: | Condition that prevents proper translation or might cause run-time failure (translation completed) | NA                                                                     |
| Suppressible warning         | `Warning`: | Problem regarding a particular aspect of your application (translation completed)                  | `-warn` option flags: `nocast noprecision nonulls noportable nostrict` |
| Informational/status message | `Info`:    | Information regarding the translation process                                                      | `-warn` option flag: `noverbose`                                       |

#### 10.2.2 Translator Status Messages

In addition to the error, warning, and information messages, SQLJ can produce status messages throughout all phases of SQLJ operation: translation, compilation, and customization. Status messages are produced as each file is processed and at each phase of SQLJ operation.

You can control status messages by using the SQLJ` -status` option.

**See Also:**

"[Real-Time Status Messages (-status)](translator-command-line-and-options.md)"

#### 10.2.3 Translator Exit Codes

The following exit codes are returned by the SQLJ translator to the operating system upon completion:

- `0`: No error in execution

- `1`: Error in SQLJ execution

- `2`: Error in Java compilation

- `3`: Error in profile customization

- `4`: Error in class instrumentation, the optional mapping of line numbers from your `.sqlj` source file to the resulting `.class` file

- `5`: Error in `ser2class` conversion, the optional conversion of profile files from `.ser` files to `.class` files

**Note:**

- If you issue the `-help` or `-version` option, then the SQLJ exit code is `0`.

- If you run SQLJ without specifying any files to process, then SQLJ issues help output and returns exit code `1`.

### 10.3 SQLJ Run Time

This section presents information about Oracle SQLJ run time, which is a thin layer of pure Java code that runs above the JDBC driver.

If you use the default Oracle-specific code generation, then the SQLJ run-time layer becomes even thinner, with a run time subset being used in conjunction with an Oracle JDBC driver. Most of the run-time functionality is compiled directly into Oracle JDBC calls. You cannot use a non-Oracle JDBC driver.

**See Also:**

"[Oracle-Specific Code Generation (No Profiles)](key-programming-considerations.md)"

When SQLJ translates SQLJ source code using ISO standard code generation, embedded SQL commands in your Java application are replaced by calls to the SQLJ run time. Run-time classes act as wrappers for equivalent JDBC classes, providing special SQLJ functionality. When the end user runs the application, the SQLJ run time acts as an intermediary, reading information about your SQL operations from your profile and passing instructions along to the JDBC driver.

Generally speaking, however, a SQLJ run time can be implemented to use any JDBC driver or vendor-proprietary means of accessing the database. Oracle SQLJ run time requires a JDBC driver, but can use any standard JDBC driver. To use Oracle-specific data types and features, however, you must use an Oracle JDBC driver. For the purposes of this document, it is generally assumed that you are using Oracle Database and one of Oracle JDBC drivers.

**Note:**

For ISO standard SQLJ code generation, Oracle SQLJ run time and an Oracle JDBC driver will be required by your application whenever you use Oracle customizer during translation, even if you do not use Oracle extensions in your code. The generic SQLJ run time will be used if your application has no customizations, or none suitable for the connection.

#### 10.3.1 SQLJ Run Time Packages

Oracle SQLJ run time includes packages you will likely import and use directly, and others that are used only indirectly.

**Note:**

These packages are included in the run-time libraries `runtime12`, `runtime12ee`, and `runtime`.

##### Packages Used Directly

The packages containing classes that you can import and use directly in your application are:

- `sqlj.runtime`

  This package includes the `ExecutionContext` class, `ConnectionContext` interface, `ConnectionContextFactory` interface, `ResultSetIterator` interface, `ScrollableResultSetIterator` interface, and wrapper classes for streams (`BinaryStream` and `CharacterStream`, as well as the deprecated `AsciiStream` and `UnicodeStream`).

  Interfaces and abstract classes in this package are implemented by classes in the `sqlj.runtime.ref` or `oracle.sqlj.runtime` package or by classes generated by the SQLJ translator.

- `sqlj.runtime.ref`

  The classes in this package implement interfaces and abstract classes in the `sqlj.runtime` package. You will likely use the `sqlj.runtime.ref.DefaultContext` class, which is used to specify your default connection and create default connection context instances. The other classes in this package are used internally by SQLJ in defining classes during code generation, such as iterator classes and connection context classes that you declare in your SQLJ code.

- `oracle.sqlj.runtime`

  This package contains the `Oracle` class that you can use to instantiate the `DefaultContext` class and establish your default connection. It also contains Oracle-specific run-time classes used by the Oracle implementation of SQLJ, including functionality to convert to and from Oracle type extensions.

**Note:**

Packages whose names begin with `oracle` are for Oracle-specific SQLJ features.

##### Packages Used Indirectly

The packages containing classes that are for internal use by SQLJ are:

- `sqlj.runtime.profile`

  This package contains interfaces and abstract classes that define what SQLJ profiles look like (applicable only for ISO standard code generation). This includes the `EntryInfo` and `TypeInfo` classes. Each entry in a profile is described by an `EntryInfo` object, where a profile entry corresponds to a SQL operation in your application. Each parameter in a profile entry is described by a `TypeInfo` object.

  The interfaces and classes in this package are implemented by classes in the `sqlj.runtime.profile.ref` package.

- `sqlj.runtime.profile.ref`

  This package contains classes that implement the interfaces and abstract classes of the `sqlj.runtime.profile` package and are used internally by the SQLJ translator in defining profiles (for ISO standard code generation only). It also provides the default JDBC-based run-time implementation.

- `sqlj.runtime.error`

  This package, used internally by SQLJ, contains resource files for all generic (not Oracle-specific) error messages that can be generated by the SQLJ translator.

- `oracle.sqlj.runtime.error`

  This package, used internally by SQLJ, contains resource files for all Oracle-specific error messages that can be generated by the SQLJ translator.

#### 10.3.2 Categories of Run-Time Errors

Run-time errors can be generated by any of the following:

- SQLJ run time

- JDBC driver

- RDBMS

In any of these cases, a SQL exception is generated as an instance of the `java.sql.SQLException` class, or as a subclass, such as `sqlj.runtime.SQLNullException`.

Depending on where the error came from, there might be meaningful information you can retrieve from an exception using the `getSQLState()`, `getErrorCode()`, and `getMessage()` methods. SQLJ errors, for example, include meaningful SQL states and messages.

If errors are generated by Oracle JDBC driver or RDBMS at run time, look at the prefix and consult the appropriate documentation:

- [Oracle Database JDBC Developer's Guide ](../jjdbc/JDBC-error-messages.md)for JDBC errors

- Oracle error message documentation for RDBMS errors (see "[Related Documents](preface.md)")

### 10.4 Globalization Support in the Translator and Run Time

The Oracle SQLJ implementation uses the Java built-in capabilities for globalization support. This section discusses the following:

- Basics of SQLJ support for globalization and native character encoding, starting with background information covering some of the implementation details of character encoding and language support in the Oracle implementation

- Options available through the SQLJ command line that enable you to adjust your Oracle Globalization Support configuration

- Extended Oracle globalization support

- Relevant manipulation outside of SQLJ for globalization support

**Note:**

Some prior knowledge of Oracle Globalization Support is assumed, particularly regarding character encoding and locales. For information, refer to:

[Oracle Database Globalization Support Guide](../nlspg/choosing-character-set.md)

This section covers the following topics:

- Character Encoding and Language Support

- SQLJ and Java Settings for Character Encoding and Language Support

- SQLJ Extended Globalization Support

- Manipulation Outside of SQLJ for Globalization Support

#### 10.4.1 Character Encoding and Language Support

There are two main areas of SQLJ globalization support:

- Character encoding

  There are three parts to this:

  - Character encoding for reading and generating source files during SQLJ translation

  - Character encoding for generating error and status messages during SQLJ translation

  - Character encoding for generating error and status messages when the application runs

- Language support

  This determines which translations of error and status message lists are used when SQLJ outputs messages to the user, either during SQLJ translation or at SQLJ run time.

Globalization support at run time is transparent to the user, presuming your SQLJ source code and SQL character data use only characters that are within the database character set. SQL character data is transparently mapped into and out of Unicode.

Note that for multi-language applications, it is advisable to use one of the following options:

- Use a database whose character set supports Unicode.

- Even if your database character set does not support Unicode, specify that the national language character set supports Unicode. (Refer to the [Oracle Database Globalization Support Guide](../nlspg/overview-of-globalization-support.md).) In this case, you will typically use the SQLJ Unicode character types described in "SQLJ Extended Globalization Support".

**Note:**

- The SQLJ translator fully supports Unicode 2.0 and Java Unicode escape sequences. However, the SQLJ command-line utility does not support Unicode escape sequences. You can use only native characters supported by the operating system. Command-line options requiring Unicode escape sequences can be entered in a SQLJ properties file instead, because properties files do support Unicode escape sequences.

- Encoding and conversion of characters in your embedded SQL operations and characters read or written to the database, are handled by JDBC directly. SQLJ does not play a role in this. If online semantics-checking is enabled during translation, however, then you will be warned if there are characters within the text of your SQL data manipulation language (DML) operations that might not be convertible to the database character set.

- For information about JDBC globalization support functionality, refer to the[ Oracle Database JDBC Developer's GuideOracle Database JDBC Developer’s Guide](../jjdbc/globalization-support.md).

##### Overview of Character Encoding

The character encoding setting for source files tells SQLJ two things:

- How source code is represented in `.sqlj` and `.java` input files that the SQLJ translator must read

- How SQLJ should represent source code in `.java` output files that it generates

By default, SQLJ uses the encoding indicated by the JVM `file.encoding` property. If your source files use other encodings, then you must indicate this to SQLJ so that appropriate conversion can be performed.

Use the SQLJ `-encoding` option to accomplish this. SQLJ also passes the `-encoding` setting to the compiler for it to use in reading `.java` files, unless the SQLJ `-compiler-encoding-flag` is off.

**Note:**

Do not alter the `file.encoding` system property to specify encodings for source files. This might impact other aspects of your Java operation and might offer only a limited number of encodings, depending on platform or operating system considerations.

The system character-encoding setting also determines how SQLJ error and status messages are represented when output to the user, either during translation or during run time when the end user is running the application. This is set according to the `file.encoding` property and is unaffected by the SQLJ `-encoding` option.

For source file encoding, you can use the `-encoding` option to specify any character encoding supported by your Java environment. If you are using the Sun Microsystems JDK, then these are listed in the `native2ascii` documentation, which you can find at the following Web site:

https://docs.oracle.com/javase/8/docs/technotes/tools/windows/native2ascii.html

Dozens of encodings are supported by the Sun Microsystems JDK. These include `8859_1` through `8859_9` (ISO Latin-1 through ISO Latin-9), `JIS` (Japanese), `SJIS` (shift-JIS, Japanese), and `UTF8`.

##### Character Encoding Notes

Be aware of the following:

- A character that is not representable in the encoding used, for either messages or source files, can always be represented as a Java Unicode escape sequence. This is of the form `\uHHHH`, where each H is a hexadecimal digit.

- As a `.sqlj` source file is read and processed during translation, error messages quote source locations based on character position (not byte position) in the input encoding.

- Encoding settings, either set through the SQLJ `-encoding` option or the Java `file.encoding` setting, do not apply to Java properties files, such as `sqlj.properties` and `connect.properties`. Properties files always use the encoding `8859_1`. This is a feature of Java in general, not SQLJ in particular. However, you can use Unicode escape sequences in a properties file. You can use the `native2ascii` utility to determine escape sequences.

##### Overview of Language Support

SQLJ error and status reporting, either during translation or during run time, uses the Java locale setting in the JVM `user.language` property. Users typically do not have to alter this setting.

Language support is implemented through message resources that use key/value pairs. For example, where an English-language resource has a key/value pair of `"OkKey", "Okay"`, a German-language resource has a key/value pair of `"OkKey", "Gut"`. The locale setting determines the message resources used.

SQLJ supports locale settings of `en` (English), `de` (German), `fr` (French), and `ja` (Japanese).

**Note:**

Java locale settings can support country and variant extensions in addition to language extensions. For example, consider `ErrorMessages_de_CH_var1`, where `CH` is the Swiss country extension of German and `var1` is an additional variant. SQLJ, however, currently supports only language extensions (`de` in this example), ignoring country and variant extensions.

#### 10.4.2 SQLJ and Java Settings for Character Encoding and Language Support

The Oracle SQLJ implementation provides syntax that enables you to set the following:

- The character encoding used by the SQLJ translator and Java compiler in representing source code

  Use the SQLJ `-encoding` option.

- The character encoding used by the SQLJ translator and run time in representing error and status messages

  Use the SQLJ `-J` prefix to set the Java `file.encoding` property.

- The locale used by the SQLJ translator and run time for error and status messages

  Use the SQLJ `-J` prefix to set the Java `user.language` property.

##### Setting Character Encoding for Source Code

Use the SQLJ `-encoding` option to determine the character encoding used in representing `.sqlj` files read by the translator, `.java` files generated by the translator, and `.java` files read by the compiler. The option setting is passed by SQLJ to the compiler, unless the SQLJ `-compiler-encoding-flag` is off.

This option can be set on the command line or `SQLJ_OPTIONS` environment variable, as in the following example:

    -encoding=SJIS

Alternatively, you can set it in a SQLJ properties file, as follows:

    sqlj.encoding=SJIS

If the encoding option is not set, then both the translator and compiler will use the encoding specified in the JVM `file.encoding` property. This can also be set through the SQLJ command line.

**See Also:**

"[Encoding for Input and Output Source Files (-encoding)](translator-command-line-and-options.md)" and "[Compiler Encoding Support (-compiler-encoding-flag)](translator-command-line-and-options.md)"[Encoding for Input and Output Source Files (-encoding)](translator-command-line-and-options.md)

**Note:**

If your `-encoding` is to be set routinely to the same value, then it is most convenient to specify it in a properties file, as in the second example.

##### Setting Character Encoding and Locale for SQLJ Messages

Character encoding and locale for SQLJ error and status messages produced, during both translation and run time, are determined by the Java `file.encoding` and `user.language` properties. Although it is typically not necessary, you can set these and other JVM properties in the SQLJ command line by using the SQLJ `-J` prefix. Options marked by this prefix are passed to the JVM.

Set the character encoding as in the following example, which specifies shift-JIS Japanese character encoding:

    -J-Dfile.encoding=SJIS

**Note:**

Only a limited number of encodings might be available, depending on platform or operating system considerations.

Set the locale as in the following example (which specifies Japanese locale):

    -J-Duser.language=ja

The `-J` prefix can be used on the command line or `SQLJ_OPTIONS` environment variable only. It cannot be used in a properties file, because properties files are read after the JVM is invoked.

**Note:**

- If your `file.encoding`, `user.language`, or any other Java property is to be set routinely to the same value, it is most convenient to specify `-J` settings in the `SQLJ_OPTIONS` environment variable. This way, you do not have to repeatedly specify them on the command line. The syntax is essentially the same as on the command line. For more information, refer to "[SQLJ_OPTIONS Environment Variable for Option Settings](translator-command-line-and-options.md)".

- Remember that if you do not set the SQLJ `-encoding` option, then setting `file.encoding` will affect encoding for source files as well as error and status messages.

- Be aware that altering the `file.encoding` property might have unforeseen consequences on other aspects of your Java operations. Also, any new setting must be compatible with your operating system.

**See Also:**

"[Command-Line Syntax and Operations](translator-command-line-and-options.md)" and "[Options to Pass to the Java Virtual Machine](translator-command-line-and-options.md)"

##### SQLJ Command-Line Example: Setting Encoding and Locale

Following is a complete SQLJ command line, including JVM `file.encoding` and `user.language` settings:

    % sqlj -encoding=8859_1 -J-Dfile.encoding=SJIS -J-Duser.language=ja Foo.sqlj

This example uses the SQLJ `-encoding` option to specify `8859_1` (Latin-1) for source code representation during SQLJ translation. This encoding is used by the translator in reading the `.sqlj` input file and in generating the `.java` output file. The encoding is then passed to the Java compiler to be used in reading the generated `.java` file. The `-encoding` option, when specified, is always passed to the Java compiler unless the SQLJ `-compiler-encoding-flag` is disabled.

For error and status messages output during translation of `Foo.sqlj`, the SQLJ translator uses the `SJIS` encoding and the `ja` locale.

#### 10.4.3 SQLJ Extended Globalization Support

The Oracle SQLJ implementation includes support for Java types (Unicode character types) derived from existing character and stream types that convey expected usage for globalization. In SQLJ it is not possible to use JDBC statement or result set methods directly that otherwise serve the purpose of globalization support. If you are interested in information about those methods, refer to the[ Oracle Database JDBC Developer's Guide](../jjdbc/globalization-support.md)

If the database natively supports Unicode, then the types described in the following section are unnecessary. In this case, globalization support will be handled transparently. It is when the database does not natively support Unicode, but has a national language character set that does support Unicode, that you will typically use these types (for columns that use the national language character set).

##### Java Types for Globalization Support

The Oracle SQLJ implementation provides a number of Java types for globalization support. The following table notes the correspondence between these globalization support types and general-use JDBC and SQLJ character and stream types. Each globalization support type, except for `NString`, is a subclass of its corresponding JDBC or SQLJ type.

Table 10-3 JDBC and SQLJ Types and Corresponding Globalization Types

| JDBC and SQLJ Types                                                  | Globalization Support Types                                                           |
|:---------------------------------------------------------------------|:--------------------------------------------------------------------------------------|
| JDBC types:                                                          |                                                                                       |
| `oracle.sql.CHAR`                                                    | `oracle.sql.NCHAR`                                                                    |
| `java.lang.String`                                                   | `oracle.sql.NString`                                                                  |
| `oracle.sql.CLOB`                                                    | `oracle.sql.NCLOB`                                                                    |
| SQLJ types:                                                          |                                                                                       |
| `sqlj.runtime.CharacterStream`                                       | `oracle.sqlj.runtime.NcharCharacterStream`                                            |
| `sqlj.runtime.AsciiStream`<br>(Deprecated; use `CharacterStream`.)   | `oracle.sqlj.runtime.NcharAsciiStream`<br>(Deprecated; use `NcharCharacterStream`.)   |
| `sqlj.runtime.UnicodeStream`<br>(Deprecated; use `CharacterStream`.) | `oracle.sqlj.runtime.NcharUnicodeStream`<br>(Deprecated; use `NcharCharacterStream`.) |

In situations where your application must handle national language character strings, either inserting them into or selecting them from national language character set columns, use the globalization support types instead of the corresponding general-use types.

**Note:**

- All globalization support types add automatic registration of intended usage for `IN` and `OUT` parameters, but are otherwise identical in usage to the corresponding JDBC or SQLJ type (including constructors).

- Use of globalization support types is unnecessary in iterator columns, because the underlying network protocol supports national language characters implicitly for the underlying result sets.

##### NString Class Usage and Notes

The `oracle.sql.CHAR` class, and therefore its `NCHAR` subclass, provides only constructors that require explicit knowledge of the database character set. Therefore, the `oracle.sql.NString` class, a wrapper for `java.lang.String`, is preferable in most circumstances. The `NString` class provides simpler constructors and ensures that the national language character form of use is registered with the JDBC driver.

Following are the key `NString` methods:

- `NString(String)`: This constructor creates an `NString` instance from an existing `String` instance.

- `String toString()`: This method returns the underlying `String` instance.

- `String getString()`: This method also returns the underlying `String` instance.

The `toString()` method enables you to use the `NString` instance in string concatenation expressions (such as `"a"+b`, where `b` is a string). The `getString()` method, provided in the `CHAR` superclass, is supported as well for uniformity. In addition, the member methods of the `String` class are carried over to the `NString` wrapper class to enable you to write more concise code.

In SQLJ applications, for versions prior to Oracle Database 11g, you must use host variables of the `NString` type to bind columns of the `NCHAR` type. For example, consider the following table:

    CREATE TABLE Tbl1 (
           ColA  CHAR
           NColB NCHAR
    )

To insert a row in this table through a SQLJ application, use a code similar to the following:

    ...
    String v_a = "\uFF5E";
    NString v_nb = "\uFF5E";
    #sql {INSERT INTO Tbl1 (ColA, NColB) VALUES (:v_a, :v_nb)};
    ...

Since Oracle Database 11g Release 1, SQLJ applications can use `String` variables to bind `NCHAR` columns. Therefore, the preceding example can be rewritten as follows:

    ...
    String v_a = "\uFF5E";
    String v_nb = "\uFF5E";
    #sql {INSERT INTO Tbl1 (ColA, NColB) VALUES (:v_a, :v_nb)};
    ...

However, if you want to use `String` host variable to bind to `NCHAR` columns, then you must translate the SQLJ file with the `-ncharconv` SQLJ translator option, as follows:

    sqlj -ncharconv [-options] app.sqlj

In the preceding command, `options` can be other SQLJ options and `app.sqlj` is the SQLJ file that contains the code.

When this option is used, the `setFormOfUse` method will be generated for all binds to character columns, that is, `CHAR` or `NCHAR` columns.

**Note:**

When the SQLJ file is compiled with the `-ncharconv` option, the `setFormOfUse` method is used in the generated code for `codegen=oracle`. For `codegen=iso`, this option information is passed to Oracle SQLJ run time, which internally uses `SetFormOfUse` for bind at run time.

The SQLJ application can use `String` host variable to retrieve data from the server without using the `-ncharconv` option, because the information about the column type is fetched at the client-side and JDBC internally sets the form for the appropriate columns.

**Note:**

There may be a small difference in the performance when using the `-ncharconv` option, depending on the database character set and national charster set and the number of character columns in the table.

##### Globalization Support Examples

The following examples show use of the `NString` class:

- `NString` as `IN` argument

  This example uses an `NString` instance as an input parameter to the database.

      import oracle.sql.NString;
      ...
      NString nc_name = new NString("Name with strange characters");
      #sql { update PEOPLE
             set city = :(new NString("\ufff2")), name = :nc_name
             where num= :n };
      ...

- `NString` as `OUT` argument

  This example uses an `NString` instance as an output parameter from the database.

      import oracle.sql.NString;
      ...
      NString nstr;
      #sql { call foo(:out nstr) };
      System.out.println("Result is: "+nstr);
      // or, explicitly: System.out.println("Result is: "+nstr.toString());
      ...

- `NString` as `Result Set` column

  This example uses the `NString` type for an iterator column. Such usage is superfluous, given that the underlying network protocol supports national language characters implicitly, but harmless. This example also shows use of one of the `String` methods, `substring()`, that is carried over to `NString`.

      import oracle.sql.NString;
      import oracle.sql.NCLOB;
      ...
      #sql iterator NIter(NString title, NCLOB article);

      NIter nit;
      #sql nit = { SELECT article, title FROM page_table };
      while (nit.next())
      {
        System.out.println("<TITLE>"+nit.title()+"</TITLE>");
        ...
        nit.article().substring(0, 1000); ...
      }

**Note:**

Using the `NCHAR` type instead of the `NString` type for the preceding examples requires the following changes:

- Use the appropriate `NCHAR` constructor. `NCHAR` constructors mirror `CHAR` constructors, such as the following:

      NCHAR(String str, oracle.sql.CharacterSet charset)

- Although you have the option of using either `toString()` or `getString()` to retrieve the underlying `String` instance from an `NString` instance, for an `NCHAR` instance you must use the `getString()` method. When using the `NString` type, the `toString()` method is used automatically for string concatenation.

#### 10.4.4 Manipulation Outside of SQLJ for Globalization Support

This section discusses ways to manipulate your Oracle Globalization Support configuration outside of SQLJ.

##### Setting Encoding and Locale at Application Run Time

As with any end user running any Java application, those running your SQLJ application can specify JVM properties, such as `file.encoding` and `user.language` directly, as they invoke the JVM to run your application. This determines the encoding and locale used for message output as your application executes.

They can accomplish this as in the following example:

    % java -Dfile.encoding=SJIS -Duser.language=ja Foo

This will use `SJIS` encoding and Japanese locale.

##### Using API to Determine Java Properties

In Java code, you can determine values of Java properties by using the `java.lang.System.getProperty()` method, specifying the appropriate property. For example:

    public class Settings
    {
       public static void main (String[] args)
       {
          System.out.println("Encoding: " + System.getProperty("file.encoding")
                           + ", Language: " + System.getProperty("user.language"));
       }
    }

You can compile this and run it as a standalone utility.

There is also a `getProperties()` method that returns the values of all properties, but this will raise a security exception if you try to use it in code that runs in the server.

##### Using native2ascii for Source File Encoding

If you are using a Sun Microsystems JDK, then there is an alternative to having SQLJ do the character encoding for your source files. You can use the `native2ascii` utility to convert sources with native encoding to sources in 7-bit ASCII with Unicode escape sequences.

**Note:**

To use SQLJ to translate source created by `native2ascii`, ensure that the JVM that invokes SQLJ has a `file.encoding` setting that supports some superset of 7-bit ASCII. This is not the case with settings for EBCDIC or Unicode encoding.

Run `native2ascii` as follows:

    % native2ascii <options> <inputfile> <outputfile>

Standard input or standard output are used if you omit the input file or output file. Two options are supported:

- `-reverse` (Reverse the conversion. Convert from Latin-1 or Unicode to native encoding)

- `-encoding <``encoding``>`

For example:

    % native2ascii -encoding SJIS Foo.sqlj Temp.sqlj

For more information, see the following Web site:

https://docs.oracle.com/javase/8/docs/technotes/tools/windows/native2ascii.html
