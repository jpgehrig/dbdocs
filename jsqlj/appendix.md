Profiles and profile customization are introduced in "[SQLJ Profiles](key-programming-considerations.md)". This appendix presents more technical detail and discusses customizer options and how to use customizers other than the default Oracle customizer.

There is also discussion of Oracle specialized customizers, particularly the `SQLCheckerCustomizer` for semantics-checking profiles, and the `AuditorInstaller` for installing auditors for debugging.

The following topics are covered:

- More About Profiles

- More About Profile Customization

- Customization Options and Choosing a Customizer

- JAR Files for Profiles

- SQLCheckerCustomizer for Profile Semantics-Checking

- AuditorInstaller Customizer for Debugging

**Note:**

If you use the default Oracle-specific code generation (`-codegen=oracle`), the discussion in this appendix does not pertain to your application.

### A.1 More About Profiles

SQLJ profiles contain information about your embedded SQL operations, with a separate profile being created for each connection context class that your application uses. Profiles are created during the SQLJ translator code generation phase and customized during the customization phase. Customization enables your application to use vendor-specific database features. Separating these vendor-specific operations into your profiles enables the rest of your generated code to remain generic.

Each profile contains a series of entries for the SQLJ statements that use the relevant connection context class, where each entry corresponds to one SQL operation in your application.

Profiles exist as serialized objects stored in resource files packaged with your application. Because of this, profiles can be loaded, read, and modified (added to or recustomized) at any time. When profiles are customized, information is only added, never removed. Multiple customizations can be made without losing preceding customizations, so that your application maintains the capability to run in multiple environments. This is known as binary portability.

For profiles to have binary portability, SQLJ industry-standard requirements have been met in the Oracle SQLJ implementation.

#### A.1.1 Creation of a Profile During Code Generation

During code generation, the translator creates each profile as follows:

1.  It creates a profile object as an instance of the `sqlj.runtime.profile.Profile` class.

2.  It inserts information about your embedded SQL operations into the profile object, for SQLJ statements that use the relevant connection context class.

3.  It serializes the profile object into a Java resource file, referred to as a profile file, with a `.ser` file name extension.

**Note:**

The Oracle SQLJ implementation provides an option to have the translator automatically convert these `.ser` files to `.class` files. The`.ser` files are not supported by some browsers, and can be cumbersome when loading translated applications into the server. However, this prevents any further customization of the profile.

As discussed in "[Code Generation](translator-run-time-functionality.md)", profile file names for application `Foo` are of the form:

    Foo_SJProfilen.ser

SQLJ generates `Foo_SJProfile0.ser`, `Foo_SJProfile1.ser`, and so on, as needed, depending on how many connection context classes you use in your code. Or, if the `-ser2class` option is enabled, then SQLJ generates `Foo_SJProfile0.class`, `Foo_SJProfile1.class`, and so on.

Each profile has a `getConnectedProfile()` method that is called during SQLJ runtime. This method returns something equivalent to a JDBC `Connection` object, but with added functionality. This is further discussed in "Functionality of a Customized Profile at Run Time".

**Note:**

Referring to a "profile object" indicates that the profile is in its original nonserialized state. Referring to a "profile file" indicates that the profile is in its serialized state in a `.ser` file.

#### A.1.2 Sample Profile Entry

Following is a sample SQLJ executable statement with the profile entry that would result. For simplicity, the profile entry is presented as plain text with irrelevant portions omitted.

Note that in the profile entry, the host variable is replaced by JDBC syntax (the question mark).

##### A.1.2.1 SQLJ Executable Statement

Presume the following declaration:

    #sql iterator Iter (double sal, String ename);

And presume the following executable statements:

    String empname = 'Smith';
    Iter it;
    ...
    #sql it = { SELECT first_name, salary FROM employees WHERE first_name = :empname };

##### A.1.2.2 Corresponding SQLJ Profile Entry

    =================================================================
    ...
    #sql { SELECT first_name, salary FROM employees WHERE first_name = ? };
    ...
    PREPARED_STATEMENT executed through EXECUTE_QUERY
    role is QUERY
    descriptor is null
    contains one parameter
    1. mode: IN, java type: java.lang.String (java.lang.String),
       sql type: VARCHAR, name: ename, ...
    result set type is NAMED_RESULT
    result set name is Iter
    contains 2 result columns
    1. mode: OUT, java type: double (double),
       sql type: DOUBLE, name: sal, ...
    2. mode: OUT, java type: java.lang.String (java.lang.String),
       sql type: VARCHAR, name: ename, ...
    =================================================================

**Note:**

This profile entry is presented here as text for convenience only; profiles are not actually in text format. They can be printed as text, however, using the SQLJ `-P-print` option, as discussed in "Overview of Customizer Harness Options".

### A.2 More About Profile Customization

When using ISO SQLJ code, running the `sqlj` script on a SQLJ source file includes an automatic customization process, where each profile created during the code generation phase is customized for use with your particular database. The default customizer is Oracle customizer, `oracle.sqlj.runtime.OraCustomizer`, which optimizes your profiles to use type extensions and performance enhancements specific to Oracle Database 12c Release 2 (12.2).

You can also run the `sqlj` script to customize profiles created previously. On the SQLJ command line, you can specify `.ser` files individually, JAR files containing `.ser` files, or both.

**Note:**

- Whenever you use the default Oracle customizer during translation, your application will require Oracle SQLJ run time and an Oracle JDBC driver when it runs, even if you do not use Oracle extensions in your code.

- If an application has no customizations, or none suitable for the connection, then the generic SQLJ run time is used.

- You can run SQLJ to process `.sqlj` and `.java` files (for translation, compilation, and customization) or to process `.ser` and `.jar` files (for customization only), but not both categories at once.

#### A.2.1 Overview of the Customizer Harness and Customizers

Regardless of whether you use Oracle customizer or an alternative customizer, SQLJ uses a front-end customization utility known as the customizer harness in accomplishing your customizations.

When you run SQLJ, you can specify customization options for the customizer harness (for general customization settings that apply to any customizer you use) and for your customizer (for settings used by the particular customizer). In either case, you can specify these options either on the command line or in a properties file. This is discussed in "Customization Options and Choosing a Customizer".

A customizer is required to be a JavaBeans component adhering to the standard JavaBeans API to expose its properties, and must implement the `sqlj.runtime.profile.util.ProfileCustomizer` interface, which specifies a `customize()` method. For each profile to be customized, the customizer harness calls the `customize()` method of the customizer object.

Oracle customizer meets the preceding requirements and is defined in the `oracle.sqlj.runtime.OraCustomizer` class.

#### A.2.2 Steps in the Customization Process

The SQLJ customization process during translation consists of the following steps, as applicable, either during the customization stage of an end-to-end SQLJ run, or when you run SQLJ to customize existing profiles only:

1.  SQLJ instantiates and invokes the customizer harness and passes it any general customization options you specified.
2.  The customizer harness instantiates the customizer you are using and passes it any customizer-specific options you specified.
3.  When you run SQLJ for customization only, specifying one or more JAR files on the command line, the customizer harness discovers and extracts the profile files within these JAR files.
4.  The customizer harness deserializes each profile file into a profile object (`.ser` files automatically created during an end-to-end SQLJ run, `.ser` files specified on the command line for customization only, or `.ser` files extracted from JAR files specified on the command line for customization only).
5.  If the customizer you use requires a database connection, the customizer harness establishes that connection.
6.  For each profile, the harness calls the `customize()` method of the customizer object instantiated in step 2 (customizers used with SQLJ must have a `customize()` method).
7.  For each profile, the `customize()` method typically creates and registers a profile customization within the profile. This depends on the intended functionality of the customizer, however. Some might have a specialized purpose that does not require a customization to be created and registered in this way.
8.  The customizer harness reserializes each profile and puts it back into a `.ser` file.
9.  When you run SQLJ for customization only, specifying one or more JAR files on the command line, the customizer harness recreates the JAR contents, inserting each customized `.ser` file to replace the original corresponding uncustomized `.ser` file.

**Note:**

- If an error occurs during customization of a profile, the original `.ser` file is not replaced.

- If an error occurs during customization of any profile in a JAR file, the original JAR file is not replaced.

- SQLJ can run only one customizer at a time. If you want to accomplish multiple customizations on a single profile, you must run SQLJ multiple times. For the additional customizations, enter the profile name directly on the SQLJ command line.

#### A.2.3 Creation and Registration of a Profile Customization

When the harness calls the `customize()` method to customize a profile, it passes in the profile object, a SQLJ connection context object (if you are using a customizer that requires a connection), and an error log object (which is used in logging error messages during the customization).

The same error log object is used for all customizations throughout a single running of SQLJ, but its use is transparent. The customizer harness reads messages written to the error log object and reports them in real-time to the standard output device (whatever SQLJ uses, typically your screen).

Recall that each profile has a set of entries, where each entry corresponds to a SQL operation. (These would be the SQL operations in your application that use instances of the connection context class associated with this profile.)

A `customize()` method implements special processing on these entries. It could be as simple as checking each entry to verify its syntax, or it could be more complicated, such as creating new entries that are equivalent to the original entries but are modified to use features of your particular database.

**Note:**

- Any `customize()` processing of profile entries does not alter the original entries.

- Customizing your profiles for use in a particular environment does not prevent your application from running in a different environment. You can customize a profile multiple times for use in multiple environments, and these customizations will not interfere with each other.

#### A.2.4 Customization Error and Status Messages

The customizer harness outputs error and status messages in much the same way as the SQLJ translator, outputting them to the same output device. None of the warnings regarding customization are suppressible, however.

Error messages reported by the customizer harness fall into four categories:

- Unrecognized or illegal option

- Connection instantiation error

- Profile instantiation error

- Customizer instantiation error

Status messages reported by the customizer harness during customization enable you to determine whether a profile was successfully customized. They fall into three categories:

- Profile modification status

- JAR file modification status

- Name of backup file created (if the customizer harness `backup` option is enabled)

Additional customizer-specific errors and warnings might be reported by the `customize()` method of the particular customizer.

During customization, the profile customizer writes messages to its error log, and the customizer harness reads the log contents in real-time and outputs these messages to the SQLJ output device, along with any other harness output. You never have to access error log contents directly.

#### A.2.5 Functionality of a Customized Profile at Run Time

A customized profile is a static member of the connection context class with which it is associated. For each SQLJ statement in your application, the SQLJ run time determines the connection context class and instance associated with that statement, then uses the customized profile of the connection context class, together with the underlying JDBC connection of the particular connection context instance, to create a connected profile. This connected profile is the vehicle that the SQLJ run time uses in applying vendor-specific features to the execution of your SQLJ application.

### A.3 Customization Options and Choosing a Customizer

This section discusses options for profile customization, which fall into three categories:

- Options you specify to the customizer harness, which apply to whatever customizer you use.

  This includes general options, connection options, and options that invoke specialized customizers.

- Customizer-specific options you specify to your customizer through the customizer harness.

- SQLJ options, which determine basic aspects of customization, such as whether to customize at all and which customizer to use.

All categories of options are specified through the SQLJ command line or properties files.

The following topics are included in this section:

- Overview of Customizer Harness Options

- General Customizer Harness Options

- Customizer Harness Options for Connections

- Customizer Harness Options that Invoke Specialized Customizers

- Overview of Customizer-Specific Options

- Oracle Customizer Options

- SQLJ Translator Options for Profile Customization

To choose a customizer other than the default Oracle customizer, you can use either the customizer harness `customizer` option (discussed in "Overview of Customizer Harness Options") or the SQLJ `-default-customizer` option (discussed in "SQLJ Translator Options for Profile Customization").

#### A.3.1 Overview of Customizer Harness Options

The customizer harness provided with the Oracle SQLJ implementation offers a number of options that are not specific to a particular customizer. The harness uses these options in its front-end coordination of the customization process.

##### A.3.1.1 Syntax for Customizer Harness Options

Customizer harness option settings on the SQLJ command line have the following syntax:

    -P-option=value

Alternatively, in a SQLJ properties file:

    profile.option=value

Enable boolean options (flags) either with:

    -P-option

or:

    -P-option=true

Boolean options are disabled by default, but you can explicitly disable them with:

    -P-option=false

##### A.3.1.2 Options Supported by the Customizer Harness

The customizer harness supports the following general options:

- `backup`: Save a backup copy of the profile before customizing it.

- `context`: Limit customizations to profiles associated with the listed connection context classes.

- `customizer`: Specify the customizer to use.

- `digests`: Specify digests for JAR file manifests (relevant only if specifying JAR files to customize).

- `help`: Display customizer options (specified only in SQLJ command line).

- `verbose`: Display status messages during customization.

The customizer harness supports the following options for customizer database connections. Currently, these are used by Oracle customizer if you enable its `optcols` option for column definitions (for performance optimization). In addition, they are used by the `SQLCheckerCustomizer` if you use this specialized customizer to perform online semantics-checking on profiles.

- `user`: Specify the user name for the connection used in this customization.

- `password`: Specify the password for the connection used in this customization.

- `url`: Specify the URL for the connection used in this customization.

- `driver`: Specify the JDBC driver for the connection used in this customization.

For information about the Oracle customizer `optcols` flag, see "Oracle Customizer Column Definition Option (optcols)". For information about the `SQLCheckerCustomizer`, see "SQLCheckerCustomizer for Profile Semantics-Checking".

The following commands function as customizer harness options, but are implemented through specialized customizers provided with the Oracle SQLJ implementation.

- `debug`: Insert debugging information into the specified profiles, to be output at run time. This is a shortcut to invoke the Oracle SQLJ `AuditorInstaller`, which is described in "AuditorInstaller Customizer for Debugging".

- `print`: Output the contents of the specified profiles, in text format.

- `verify`: Perform semantics-checking on a profile that was produced during a previous execution of the SQLJ translator (equivalent to semantics-checking performed on source code during translation). This is a shortcut to invoke Oracle SQLJ `SQLCheckerCustomizer`, which is described in "SQLCheckerCustomizer for Profile Semantics-Checking".

#### A.3.2 General Customizer Harness Options

This section describes general options supported by the customizer harness.

##### A.3.2.1 Profile Backup Option (backup)

Use the `backup` flag to instruct the harness to save a backup copy of each `.jar` file and standalone `.ser` file before replacing the original. (Separate backups of `.ser` files that are within `.jar` files are not necessary.)

Backup file names are given the extension `.bak``n`, where `n` indicates digits used as necessary where there are similarly named files. For each backup file created, an informational message is issued.

If an error occurs during customization of a standalone `.ser` file, then the original `.ser` file is not replaced and no backup is created. Similarly, if an error occurs during customization of any `.ser` file within a JAR file, then the original JAR file is not replaced and no backup is created.

The command-line syntax for this option is:

    -P-backup<=true|false>

Command-line example is:

    -P-backup

Properties file syntax is:

    profile.backup<=true|false>

Default value is:

    false

##### A.3.2.2 Customization Connection Context Option (context)

Use the `context` option to limit customizations to profiles that correspond to the specified connection context classes. Fully qualify the class names and use a comma-delimited list to specify multiple classes. For example:

    -P-context=sqlj.runtime.ref.DefaultContext,foo.bar.MyCtxtClass

There must be no space on either side of the comma.

If this option is not specified, then all profiles are customized, regardless of their associated connection context classes.

Command-line syntax is:

    -P-context=ctx_class1<,ctx_class2,...>

Command-line example is:

    -P-context=foo.bar.MyCtxtClass

Properties file syntax is:

    profile.context=ctx_class1<,ctx_class2,...>

Properties file example is:

    profile.context=foo.bar.MyCtxtClass

##### A.3.2.3 Customizer Option (customizer)

Use the `customizer` option to specify which customizer to use. Fully qualify the class name, such as in the following example:

    -P-customizer=oracle.sqlj.runtime.util.OraCustomizer

If you do not set this option, then SQLJ will use the customizer specified in the SQLJ `-default-customizer` option. Unless set otherwise, this is the following:

    oracle.sqlj.runtime.util.OraCustomizer

Command-line syntax is:

    -P-customizer=customizer_class

Command-line example is:

    -P-customizer=a.b.c.MyCustomizer

Properties file syntax is:

    profile.customizer=customizer_class

Properties file example is:

    profile.customizer=a.b.c.MyCustomizer

Default value is:

    None

##### A.3.2.4 Customization JAR File Digests Option (digests)

When a JAR file is produced, the JAR utility can optionally include one or more digests for each entry, based on one or more specified algorithms, so that the integrity of the JAR file entries can later be verified. Digests are similar conceptually to checksums, for readers familiar with those.

If you are customizing profiles in a JAR file and want the JAR utility to add new digests (or update existing digests) when the JAR file is updated, use the `digests` option to specify a comma-delimited list of one or more algorithms. These are the algorithms that the JAR utility will use in creating the digests for each entry. The JAR utility produces one digest for each algorithm for each JAR file entry in the JAR manifest file. Specify algorithms as follows:

    -P-digests=SHA,MD5

There must be no space on either side of the comma.

In this example, there will be two digests for each entry in the JAR manifest file: an `SHA` digest and an `MD5` digest.

**Note:**

Visit the Sun site more information about JAR manifest file.

For information about JAR files and the JAR utility, see one of the following Web sites:

    http://www.javasoft.com/products/jdk/1.2/docs/guide/jar/index.html

Command-line syntax is:

    -P-digests=algo1<,algo2,...>

Command-line example is:

    -P-digests=SHA,MD5

Properties file syntax is:

    profile.digests=algo1<,algo2,...>

Properties file example is:

    profile.digests=SHA,MD5

Default value is:

    SHA,MD5

##### A.3.2.5 Customization Help Option (help)

Use the `help` option to display the option lists of the customizer harness and the default customizer or a specified customizer. For the harness and Oracle customizer, this includes a brief description and the current setting of each option.

Display the option lists for the harness and default customizer as follows (where the default customizer is Oracle customizer or whatever you have specified in the SQLJ `-default-customizer` option):

    -P-help

Use the `help` option in conjunction with the `customizer` option to display the option list of a particular customizer, as follows:

    -P-help -P-customizer=sqlj.runtime.profile.util.AuditorInstaller

**Note:**

- You can use the `-P-help` option on the SQLJ command line only, not in a SQLJ properties file.

- No customizations are performed if the `-P-help` flag is enabled, even if you specify profiles to customize on the command line.

Command-line syntax is:

    -P-help <-P-customizer=customizer_class>

Command-line example is:

    -P-help

Properties file syntax is:

    NA

Properties file example is:

    NA

Default value is:

    None

##### A.3.2.6 Customization Verbose Option (verbose)

Use the `verbose` flag to instruct the harness to display status messages during customizations. These messages are written to the standard output device, wherever SQLJ writes its other messages.

Command-line syntax is:

    -P-verbose<=true|false>

Command-line example is:

    -P-verbose

Properties file syntax is:

    profile.verbose<=true|false>

Properties file example is:

    profile.verbose

Default value is:

    false

#### A.3.3 Customizer Harness Options for Connections

This section describes connection options supported by the customizer harness. These are used as follows:

- Oracle customizer uses database connections only for column definitions. If you do not enable Oracle customizer `optcols` option, then there is no need to set the customizer harness `user`, `password`, `url`, and `driver` options.

- The `SQLCheckerCustomizer`, a specialized customizer that performs semantics-checking on profiles, uses the customizer harness `user`, `password`, `url`, and `driver` settings for online checking.

  Use `-P-verify` on the SQLJ command line to invoke this customizer.

**Note:**

Do not confuse the customizer harness `user`, `password`, `url`, and `driver` options with the translator options of the same names, which are for semantics-checking during the translation step. However, the translator settings are passed to the customizer for convenience, in case customization is to use the same connection as translation. Override these initial settings through the customizer harness options if you wish.

##### A.3.3.1 Customization User Option (user)

Set the `user` option to specify a database schema if your customizer uses database connections.

In addition to specifying the schema, you can optionally specify the password, URL, or both in your `user` option setting. The password is preceded by a forward-slash (/), and the URL is preceded by an "at" sign (@), as in the following examples:

    -P-user=HR/hr
    -P-user=HR@jdbc:oracle:oci:@
    -P-user=HR/hr@jdbc:oracle:oci:@

**Note:**

When you use column definitions (`optcols` option), the user setting for the SQLJ translator is forwarded to the profile customizer as well, but you can use the customizer `user` option to override the translator setting.

Command-line syntax is:

    -P-user=username</password><@url>

Command-line examples is:

    -P-user=HR
    -P-user=HR/password
    -P-user=HR/password@jdbc:oracle:oci:@

Properties file syntax is:

    profile.user=username</password><@url>

Properties file examples is:

    profile.user=HR
    profile.user=HR/hr
    profile.user=HR/hr@jdbc:oracle:oci:@

Default value is:

    null

##### A.3.3.2 Customization Password Option (password)

Use the `password` option if your customizer uses database connections.

The password can also be set with the `user` option, as described in "Customization User Option (user)".

**Note:**

When you use column definitions (`optcols` option), the password setting for the SQLJ translator is forwarded to the profile customizer as well, but you can use the customizer `password` option to override the translator setting.

Command-line syntax is:

    -P-password=password

Command-line example is:

    -P-password=password

Properties file syntax is:

    profile.password=password

Properties file example is:

    profile.password=password

Default value is:

    null

##### A.3.3.3 Customization URL Option (url)

Use the `url` option if your customizer uses database connections.

The URL can also be set with the `user` option, as described in "Customization User Option (user)".

**Note:**

When you use column definitions (`optcols` option), the URL setting for the SQLJ translator is forwarded to the profile customizer as well, but you can use the customizer `url` option to override the translator setting.

Command-line syntax is:

    -P-url=url

Command-line example is:

    -P-url=jdbc:oracle:oci:@

Properties file syntax is:

    profile.url=url

Properties file example is:

    profile.url=jdbc:oracle:oci:@

Default value is:

    jdbc:oracle:oci:@

##### A.3.3.4 Customization JDBC Driver Option (driver)

Use the `driver` option to register a comma-delimited list of JDBC driver classes if your customizer uses database connections. For example:

    -P-driver=sun.jdbc.odbc.JdbcOdbcDriver,oracle.jdbc.OracleDriver

There must be no space on either side of the comma.

Command-line syntax is:

    -P-driver=dvr_class1<,dvr_class2,...>

Command-line example is:

    -P-driver=sun.jdbc.odbc.JdbcOdbcDriver

Properties file syntax is:

    profile.driver=dvr_class1<,dvr_class2,...>

Properties file example is:

    profile.driver=sun.jdbc.odbc.JdbcOdbcDriver

Default value is:

    oracle.jdbc.OracleDriver

#### A.3.4 Customizer Harness Options that Invoke Specialized Customizers

The customizer harness supports the following options that invoke specialized customizers:

- `debug`: This invokes the `AuditorInstaller` customizer, used in debugging.

- `print`: This invokes a customizer that prints a text version of a profile.

- `verify`: This invokes the `SQLCheckerCustomizer` customizer, which performs semantics-checking on a profile.

**Note:**

Because each of these options invokes a customizer, and only one customizer can run in a single execution of SQLJ, you cannot perform any other customization when you use any of these options.

You also cannot use more than one of `print`, `debug`, or `verify` simultaneously.

##### A.3.4.1 Specialized Customizer: Profile Debug Option (debug)

The `debug` option runs a specialized customizer, called the `AuditorInstaller`, that inserts debugging statements into profiles. Use this option in conjunction with a SQLJ command line file list to insert debugging statements into the specified profiles. These profiles must already be customized from a previous SQLJ run.

For detailed information about this customizer, including additional options that it supports, see "AuditorInstaller Customizer for Debugging".

The debugging statements will execute during SQLJ run time (when someone runs your application), displaying a trace of method calls and values returned.

Following are examples of how to specify the `debug` option:

    % sqlj -P-debug Foo_SJProfile0.ser Bar_SJProfile0.ser

    % sqlj -P-debug *.ser

Command-line syntax is:

    sqlj -P-debug profile_list

Command-line example is:

    sqlj -P-debug Foo_SJProfile*.ser

Properties file syntax is:

    profile.debug

(Also specify profiles in the SQLJ file list.)

Properties file example is:

    profile.debug

Default value is:

    NA

##### A.3.4.2 Specialized Customizer: Profile Print Option (print)

The `print` option runs a specialized customizer that prints profiles in text format. Use this option in conjunction with a SQLJ command line file list to output the contents of one or more specified profiles. The output goes to the standard SQLJ output device, typically the user screen. For example:

    % sqlj -P-print Foo_SJProfile0.ser Bar_SJProfile0.ser

Use the following command, if you want to see all the customizer options:

    % sqlj -P-print *.ser

The output of the preceding command is like the following:

    printing contents of profile Sample_SJProfile0
    created 1154609279331 (8/3/06 5:47 AM)
    associated context is Mycontext1
    profile loader is sqlj.runtime.profile.DefaultLoader@12a3793
    contains one customization
    OracleCustomization Options  :
    Version is :2300
    Cstmtcache :5
    Ccompat    :false
    Cforce     :false
    Coptcols   :false
    Coptparams :false
    Coptparamdefaults:null
    CshowSQL   :false
    Csummary   :false
    CuserSQL   :true

    #sql { SELECT a    FROM test WHERE name= ?  }
    setFixedchar is enabled
    Ncharconv  is disabled

    #sql { commit }
    setFixedchar is disabled
    Ncharconv  is disabled
    ………

Command-line syntax is:

    sqlj -P-print profile_list

Command-line example is:

    sqlj -P-print Foo_SJProfile*.ser

Properties file syntax is:

    profile.print

(Also specify profiles in SQLJ file list.)

Properties file example is:

    profile.print

Default value is:

NA

##### A.3.4.3 Specialized Customizer: Profile Semantics-Checking Option (verify)

The `verify` option runs a specialized customizer, called the `SQLCheckerCustomizer`, that performs semantics-checking on a profile. This is equivalent to the semantics-checking that is performed on source code during translation. The profile will have been created during a previous execution of the SQLJ translator.

This option is useful for checking semantics against the run-time database, after deployment, and after the source code may no longer be available.

For detailed information about this customizer, including additional options that it supports, see "SQLCheckerCustomizer for Profile Semantics-Checking".

**Note:**

For online semantics-checking of the profile, you must also use the customizer harness `user`, `password`, and `url` options.

Following are examples of how to specify the `verify` option. Both of these examples use the `SQLCheckerCustomizer` default semantics-checker, which employs online checking through the specified database connection. (The first is a single wraparound command.)

    % sqlj -P-verify -P-user=HR -P-url=jdbc:oracle:oci:@ Foo_SJProfile0.ser Bar_SJProfile0.ser
    Password: password

    % sqlj -P-verify -P-user=HR -P-url=jdbc:oracle:oci:@ *.ser
    Password: password

Command-line syntax is:

    sqlj -P-verify <conn params> profile_list

Command-line example is:

    sqlj -P-verify <conn params> Foo_SJProfile*.ser

Properties file syntax is:

    profile.verify

(You must also specify profiles, and typically customizer harness connection options, in the SQLJ command line.)

Properties file example is:

    profile.verify

Default value is:

    NA

#### A.3.5 Overview of Customizer-Specific Options

You can set customizer-specific options, such as options for Oracle customizer, on the SQLJ command line or in a SQLJ properties file. The syntax is similar to that for setting customizer harness options.

Set a customizer option on the SQLJ command line by preceding it with:

    -P-C

Alternatively, you can set it in a SQLJ properties file by preceding it with:

    profile.C

The remainder of this section discusses features of Oracle customizer, which supports several options. Most of these options are boolean and are enabled as follows:

    -P-Coption

or:

    -P-Coption=true

Boolean options are disabled by default, but you can explicitly disable them with:

    -P-Coption=false

Numeric or string options are set similarly:

    -P-Coption=value

#### A.3.6 Oracle Customizer Options

This section describes options that are specific to Oracle customizer, beginning with an overview of the options supported.

##### A.3.6.1 Options Supported by Oracle Customizer

Oracle customizer implements the following options:

- `compat`: Display version-compatibility information.

- `force`: Instruct the customizer to customize even if a valid customization already exists.

- `optcols`: Enable iterator column type and size definitions to optimize performance.

- `optparams`: Enable parameter size definitions to optimize JDBC resource allocation (used in conjunction with `optparamdefaults`).

- `optparamdefaults`: Set parameter size defaults for particular data types (used in conjunction with `optparams`).

- `fixedchar`: Enable `CHAR` comparisons with blank padding for `WHERE` clauses.

- `showSQL`: Display SQL statement transformations.

- `stmtcache`: Set the statement cache size (the number of statements that can be cached for each connection during run time) for performance optimization, or set it to zero to disable statement caching.

- `summary`: Display a summary of Oracle features used in your application.

Any output displayed by these options is written to the standard output device, wherever SQLJ writes its other messages.

##### A.3.6.2 Oracle Customizer Version Compatibility Option (compat)

Use the `compat` flag to instruct Oracle customizer to display information about compatibility of your application with different versions of Oracle Database and Oracle JDBC drivers. This can be accomplished either during a full SQLJ translation run or on profiles previously created.

For example, to see compatibility output when translating and customizing the application `MyApp`:

    % sqlj <...SQLJ options...> -P-Ccompat MyApp.sqlj

In this example, the `MyApp` profiles will be created, customized, and checked for compatibility in a single running of SQLJ.

To see compatibility output for `MyApp` profiles previously created:

    % sqlj <...SQLJ options...> -P-Ccompat MyApp_SJProfile*.ser

In this example, the `MyApp` profiles were created (and possibly customized) in a previous running of SQLJ and will be customized (if needed) and checked for compatibility in the above running of SQLJ.

Following are two output samples from a -P-C`compat` setting when using the default Oracle customizer. The first example indicates that the application can be used with all Oracle JDBC driver versions:

    MyApp_SJProfile0.ser: Info: compatible with all Oracle JDBC drivers

This second example indicates that the application can be used only with the JDBC implementation from an Oracle 8.1.x or later release:

    MyApp_SJProfile0.ser: Info: compatible with Oracle 8.1 or later JDBC driver

**Note:**

If customization does not take place because a valid previous customization is detected, the `compat` option reports compatibility regardless.

Command-line syntax is:

    -P-Ccompat<=true|false>

Command-line example is:

    -P-Ccompat

Properties file syntax is:

    profile.Ccompat<=true|false>

Properties file example is:

    profile.Ccompat

Default value is:

    false

##### A.3.6.3 Oracle Customizer Force Option (force)

Use the `force` flag to instruct Oracle customizer to force the customization of a given profile (specified on the command line) even if a valid customization already exists in that profile. For example:

    % sqlj -P-Cforce MyApp_SJProfile*.ser

This will customize all the `MyApp` profiles, regardless of whether they have already been customized. Otherwise, by default, Oracle customizer will not reinstall over a previously existing customization unless the previous one had been installed with an older version of the customizer.

Command-line syntax is:

    -P-Cforce<=true|false>

Command-line example is:

    -P-Cforce

Properties file syntax is:

    profile.Cforce<=true|false>

Properties file example is:

    profile.Cforce

Default value is:

    false

##### A.3.6.4 Oracle Customizer Column Definition Option (optcols)

Use the `optcols` flag to instruct Oracle customizer to determine types and sizes of iterator or result set columns and add this information to the profile. This enables the SQLJ run time to automatically register the columns with Oracle JDBC driver when your application runs, saving round trips to Oracle depending on the particular driver implementation. Specifically, this is effective for the Thin driver and positional iterators.

For an overview of column definitions, see "[Column Definitions](performance-and-debugging.md)".

An error will be generated if you enable Oracle customizer `optcols` option without setting the user name, password, and URL for a database connection. You can accomplish this through the translator `-user`, `-password`, and `-url` options, which are forwarded to the customizer during ISO standard code generation, or directly through the customizer `user`, `password`, and `url` options.

The customizer does not have to connect to the same schema or even the same database that your application will connect to at run time, but the relevant columns will have to be in the same order and of identical types and sizes to avoid run-time errors.

For information about the customizer harness connection options, see the `user`, `password`, `url`, and `driver` sections under "Overview of Customizer Harness Options".

**Note:**

You can use the SQLJ translator `-optcols` option instead. This sets the customizer option automatically. For Oracle-specific code generation, which uses no profiles, you must use the translator option instead.

That section also has some additional conceptual information.

You can enable or disable the customizer `optcols` flag on the SQLJ command line or in a properties file.

Enable it on the command line as follows:

    -P-Coptcols

or:

    -P-Coptcols=true

This flag is disabled by default, but you can also disable it explicitly. Disable it on the command line as follows:

    -P-Coptcols=false

Column definitions require the customizer to make a database connection to examine columns of tables being queried, so the customizer harness `user`, `password`, and `url` options must be set appropriately (as well as the customizer harness `driver` option if you are not using the default `OracleDriver` class). For example:

    % sqlj <...SQLJ options...> -P-user=HR@jdbc:oracle:oci:@ -P-Coptcols MyApp.sqlj
    Password: password

Note that as with the SQLJ translator, you can optionally set the password and URL in the `user` option instead of in the `password` and `url` options.

Alternatively, you can insert column definitions into a previously existing profile. In this case you must also use the Oracle customizer `force` option to force a recustomization:

    % sqlj -P-user=HR@jdbc:oracle:oci:@ -P-Cforce -P-Coptcols MyApp_SJProfile*.ser
    Password: password

You also can insert column definitions into previously existing profiles in a JAR file:

    % sqlj -P-user=HR@jdbc:oracle:oci:@ -P-Cforce -P-Coptcols MyAppProfiles.jar
    Password: password

When you run Oracle customizer with its `optcols` flag enabled, either during translation and creation of a new profile or during customization of an existing profile, you can also enable the customizer harness `verbose` flag. This will instruct Oracle customizer to display information about what iterators and result sets are being processed and what their column type and size definitions are. For example:

    % sqlj -P-user=HR@jdbc:oracle:oci:@ -P-verbose -P-Cforce -P-Coptcols MyApp_SJProfile*.ser
    Password: password

For general information about the `verbose` flag, see that section under "Overview of Customizer Harness Options".

You can execute Oracle customizer with its `summary` flag enabled on an existing profile to determine if column definitions have been added to that profile:

    % sqlj -P-Csummary MyApp_SJProfile*.ser

For general information about the `summary` flag, see that section under "Overview of Customizer-Specific Options".

Command-line syntax is:

    -P-Coptcols<=true|false>

Command-line example is:

    -P-Coptcols

Properties file syntax is:

    profile.Coptcols<=true|false>

Properties file example is:

    profile.Coptcols

Default value is:

    false

##### A.3.6.5 Oracle Customizer Parameter Definition Option (optparams)

Use the `optparams` flag to enable parameter size definitions. If this flag is enabled, SQLJ will register your input and output parameters (host variables) to optimize JDBC resource allocations according to sizes you specify.

For an overview of parameter size definitions and a discussion of source code hints, see "[Parameter Size Definitions](performance-and-debugging.md)".

**Note:**

You can use the SQLJ translator `-optparams` option instead. This sets the customizer option automatically. (And for Oracle-specific code generation, which uses no profiles, you must use the translator option instead.)

That section also has some additional conceptual information.

You can enable or disable the `optparams` flag on the command line or in a SQLJ properties file.

Enable it on the command line as follows:

    -P-Coptparams

or:

    -P-Coptparams=true

This flag is disabled by default, but you can also disable it explicitly. Disable it on the command line as follows:

    -P-Coptparams=false

**Note:**

Unlike the `optcols` option, the `optparams` option does not require a database connection by the customizer, because you are providing the size specifications yourself.

Following is a command-line example (omitting a setting for the `optparamdefaults` option, which is discussed in the next section):

    % sqlj <...SQLJ options...> -P-Coptparams -P-Coptparamdefaults=defaults_string MyApp.sqlj

Alternatively, to enable parameter size definitions for a previously existing profile:

    % sqlj -P-Coptparams -P-Coptparamdefaults=defaults_string MyApp_SJProfile*.ser

You can also use previously existing profiles in a JAR file:

    % sqlj -P-Coptparams -P-Coptparamdefaults=defaults_string MyAppProfiles.jar

Command-line syntax is:

    -P-Coptparams<=true|false>

Command-line example is:

    -P-Coptparams

Properties file syntax is:

    profile.Coptparams<=true|false>

Properties file example is:

    profile.Coptparams

Default value is:

    false

##### A.3.6.6 Oracle Customizer Parameter Default Size Option (optparamdefaults)

If you enable the `optparams` option to set parameter sizes, use the `optparamdefaults` option as desired to set default sizes for specified data types. If `optparams` is not enabled, then any `optparamdefaults` setting is ignored.

For an overview of parameter size definitions and a discussion of source code hints, see "[Parameter Size Definitions](performance-and-debugging.md)".

**Note:**

You can use the SQLJ translator `-optparamdefaults` option instead. This sets the customizer option automatically. (And for Oracle-specific code generation, which uses no profiles, you must use the translator option instead.)

That section also has important additional conceptual and syntax information. Functionality of the two options is equivalent.

You can set the `optparamdefaults` flag on the command line or in a SQLJ properties file.

Set it on the command line as follows:

    -P-Coptparamdefaults=datatype1(size1),datatype2(size2),...

Following is a command-line example, including the `optparams` setting as well:

    % sqlj <..SQLJ options..> -P-Coptparams -P-Coptparamdefaults=CHAR_TYPE(50),RAW_TYPE(500),CHAR(10)MyApp.sqlj

Alternatively, you can specify parameter size defaults for a previously existing profile, in which case you must also use the Oracle customizer `force` option to force a recustomization:

    % sqlj -P-Cforce -P-Coptparams -P-Coptparamdefaults=CHAR_TYPE(50),RAW_TYPE(500),CHAR(10) MyApp_SJProfile*.ser

You also can specify parameter size defaults for previously existing profiles in a JAR file:

    % sqlj -P-Cforce -P-Coptparams -P-Coptparamdefaults=CHAR_TYPE(50),RAW_TYPE(500),CHAR(10) MyAppProfiles.jar

**Note:**

If at run time, the actual size exceeds the registered size of any parameter, run-time errors will occur.

Command-line syntax is:

    -P-Coptparamdefaults=defaults_string

Command-line example is:

    -P-Coptparamdefaults=VAR%(50),LONG%(500),RAW_TYPE()

Properties file syntax is:

    profile.Coptparamdefaults=defaults_string

Properties file example is:

    profile.Coptparamdefaults=VAR%(50),LONG%(500),RAW_TYPE()

Default value is:

    null

##### A.3.6.7 Oracle Customizer CHAR Comparisons with Blank Padding (fixedchar)

Set this flag to `true` to account for blank padding in `CHAR` database columns when binding character strings for `WHERE` clause comparisons. This way, for example, "mystring" would compare positively against "mystring ".

Here is an example of Oracle customizer `fixedchar` usage:

    % sqlj -P-Cfixedchar MyProgram.sqlj AnotherProg.java ...

**Note:**

- You can use the SQLJ translator `-fixedchar` option instead. This sets the customizer option automatically. (And for Oracle-specific code generation, which uses no profiles, you must use the translator option instead.)

- If you also enable the Oracle customizer `summary` flag, the number of usages of the Oracle `setFixedCHAR()` API (used behind the scenes for `fixedchar` functionality) will be displayed. See "Oracle Customizer Summary Option (summary)" for an example.

Command-line syntax is:

    -P-Cfixedchar<=true|false>

Command-line example is:

    -P-Cfixedchar

Properties file syntax is:

    profile.Cfixedchar<=true|false>

Properties file example is:

    profile.Cfixedchar

Default value is:

    false

##### A.3.6.8 Oracle Customizer Show-SQL Option (showSQL)

Use the `showSQL` flag to display any SQL statement transformations performed by Oracle customizer. Such transformations are necessary in cases where SQLJ supports syntax that the database does not directly support.

To show SQL transformations when translating and customizing the application `MyApp`:

    % sqlj <...SQLJ options...> -P-CshowSQL MyApp.sqlj

In this example, the `MyApp` profiles will be created and customized and their SQL transformations displayed in a single running of SQLJ.

To show SQL transformations when customizing `MyApp` profiles previously created:

    % sqlj <...SQLJ options...> -P-CshowSQL MyApp_SJProfile*.ser

In this example, the `MyApp` profiles were created (and possibly customized) in a previous running of SQLJ and will be customized (if needed) and have their SQL transformations displayed in the above running of SQLJ.

The `showSQL` output might include an entry such as this:

    MyApp.sqlj:14: Info: <<<NEW SQL>>> #sql {BEGIN  ? := VALUES(tkjsSET_f1); END};

    in file MyApp, line 14, we had:


    #sql {set :v1= VALUES(tkjsSET_f1) };

During customization, Oracle customizer replaces the `SET` statement with an equivalent PL/SQL block.

**Note:**

If customization does not take place because a valid previous customization is detected, the `showSQL` option shows SQL transformations regardless.

Command-line syntax is:

    -P-CshowSQL<=true|false>

Command-line example is:

    -P-CshowSQL

Properties file syntax is:

    profile.CshowSQL<=true|false>

Properties file example is:

    profile.CshowSQL

Default value is:

    false

##### A.3.6.9 Oracle Customizer Statement Cache Size Option (stmtcache)

Use the Oracle customizer `stmtcache` option to set the statement cache size—the number of statements that can be cached for each database connection as your application runs—or to disable statement caching.

The default statement cache size is 5. For an overview of statement caching, see "[Statement Caching](performance-and-debugging.md)".

**Note:**

With the default Oracle-specific code generation (`-codegen=oracle`), SQLJ does not produce profiles and skips the customization step. In this case, use connection context methods to control SQLJ statement caching.

You can set the statement cache size on the command line or in a properties file.

To use the command line to set the statement cache size to 15 (for example) for the application `MyApp`:

    % sqlj <...SQLJ options...> -P-Cstmtcache=15 MyApp.sqlj

To disable statement caching, set the cache size to 0:

    % sqlj <...SQLJ options...> -P-Cstmtcache=0 MyApp.sqlj

You also can alter the statement cache size in an existing profile without retranslating the application, but you must also use the Oracle customizer `force` option to force a recustomization, as follows:

    % sqlj -P-Cforce -P-Cstmtcache=15 MyApp_SJProfile0.ser

If you have multiple profiles, you can set their statement cache sizes individually by running SQLJ separately for each profile, after you have translated your application:

    % sqlj -P-Cforce -P-Cstmtcache=10 MyApp_SJProfile0.ser
    % sqlj -P-Cforce -P-Cstmtcache=15 MyApp_SJProfile1.ser
    % sqlj -P-Cforce -P-Cstmtcache=0 MyApp_SJProfile2.ser

Of course, you must determine which profile corresponds to each of your connection context classes. This is determined as follows: profile 0 will correspond to the connection context class used for the first executable statement in your application; profile 1 will correspond to the connection context class used for the first executable statement that does not use the first connection context class, and so on. You can verify the correlation by using the customizer harness `print` option to examine each profile.

Command-line syntax is:

    -P-Cstmtcache=value

Command-line example is:

    -P-Cstmtcache=10

Properties file syntax is:

    profile.Cstmtcache=value

Properties file example is:

    profile.Cstmtcache=10

Default value is:

    5

##### A.3.6.10 Oracle Customizer Summary Option (summary)

Use the `summary` flag to instruct Oracle customizer to display a summary of Oracle features used in an application being translated, or in specified profile files. This is useful in identifying features that would prevent portability to other platforms and can be accomplished either during a full SQLJ translation run or on profiles previously created.

To see summary output when translating and customizing the application `MyApp`:

    % sqlj <...SQLJ options...> -P-Csummary MyApp.sqlj

In this example, the `MyApp` profiles will be created, customized, and summarized in a single running of SQLJ.

To see summary output for `MyApp` profiles previously created:

    % sqlj <...SQLJ options...> -P-Csummary MyApp_SJProfile*.ser

In this example, the `MyApp` profiles were created (and possibly customized) in a previous running of SQLJ and will be customized (if needed) and summarized in the above running of SQLJ.

Following are two samples resulting from a `-P-Csummary` setting when using the default Oracle customizer. The first example indicates no Oracle features are used:

    MyApp_SJProfile0.ser: Info: Oracle features used:
    MyApp_SJProfile0.ser: Info: * none

This second example indicates that Oracle features are used—several Oracle extended data types from the `oracle.sql` package—and lists them:

    MyApp_SJProfile0.ser: Info: Oracle features used:
    MyApp_SJProfile0.ser: Info: * oracle.sql.NUMBER: 2
    MyApp_SJProfile0.ser: Info: * oracle.sql.DATE: 2
    MyApp_SJProfile0.ser: Info: * oracle.sql.CHAR: 2
    MyApp_SJProfile0.ser: Info: * oracle.sql.RAW: 2

The following example prints out the number of usages of the Oracle `setFixedCHAR()` API (enabled through the Oracle customizer `fixedchar` option, to account for blank padding when binding a string into a `WHERE` clause for comparison against `CHAR` data):

    % sqlj -P-Cfixedchar -P-Csummary -P-Cforce *.ser
    FC_SJProfile0.ser: Info: re-installing Oracle customization
    FC_SJProfile0.ser: Info: Oracle features used:
    FC_SJProfile0.ser: Info: * setFixedCHAR(): 4

**Note:**

If customization does not take place because a valid previous customization is detected, the `summary` option produces a summary regardless.

Command-line syntax is:

    -P-Csummary<=true|false>

Command-line example is:

    -P-Csummary

Properties file syntax is:

    profile.Csummary<=true|false>

Properties file example is:

    profile.Csummary

Default value is:

    false

#### A.3.7 Options for Other Customizers

The Oracle SQLJ implementation provides additional, specialized customizers described later in this chapter. These customizers also have command-line options:

- `SQLCheckerCustomizer` (for profile semantics-checking): See "SQLCheckerCustomizer for Profile Semantics-Checking" for general information, and "SQLCheckerCustomizer Options" for information about its options.

- `AuditorInstaller` (for debugging): See "AuditorInstaller Customizer for Debugging" for general information, and "AuditorInstaller Options" for information about its options.

#### A.3.8 SQLJ Translator Options for Profile Customization

The following SQLJ translator options relate to profile customization and are described elsewhere in this manual:

- `-default-customizer`: Specify the default profile customizer to use if none is specified in the customizer harness `-customizer` option.

- `-profile`: Specify whether to customize during this running of SQLJ.

### A.4 JAR Files for Profiles

As discussed previously, you can specify a JAR file on the SQLJ command line in order to customize any profiles that the JAR file contains.

**Note:**

- Remember that you can specify `.sqlj` or `.java` files or both on the SQLJ command line for standard SQLJ processing, or you can specify `.ser` or `.jar` files or both on the command line for customization only, but not both categories.

- It is permissible for the `.jar` file to contain files that are not profiles. Any file whose manifest entry indicates that the file is not a profile will be ignored during customization.

- The `.jar` file is used as the class-loading context for each profile it contains. If a profile contains a reference to a class contained within the `.jar` file, then that class is loaded from the `.jar` file. If a profile contains a reference to a class not in the `.jar` file, then the system class loader will find and load the class according to your classpath, as usual.

#### A.4.1 JAR File Requirements

There are requirements for the manifest entry of each profile.

Create a plain text file with two lines for each profile that will be included in the JAR file. One line starts with "Name:", followed by the path or package and name. The other line is the following:

    SQLJProfile: TRUE

The two lines must be consecutive (no blank line in between), and there must be a blank line preceding line-pairs for additional profiles.

Use the JAR utility `-m` option to input this file.

For example, presume your `MyApp` application (in the directory `foo/bar`) has three profiles, and you will be creating a JAR file that will include these profiles. Complete the following steps:

1.  Create a text file with the following eight lines (including the blank lines used as separators):

        Name: foo/bar/MyApp_SJProfile0.ser
        SQLJProfile: TRUE

        Name: foo/bar/MyApp_SJProfile1.ser
        SQLJProfile: TRUE

        Name: foo/bar/MyApp_SJProfile2.ser
        SQLJProfile: TRUE

    Presume you call this file `MyAppJarEntries.txt`.

2.  When you run `jar` to create the JAR file, use the `-m` option to input your text file as follows (presume you want to call the JAR file `myjarfile.jar`):

<!-- -->

    % jar -cvfm myjarfile.jar MyAppJarEntries.txt foo/bar/MyApp_SJProfile*.ser foo/bar/*.class

As the JAR utility constructs the manifest during creation of the JAR file, it reads your text file and inserts the `SQLJProfile: TRUE` line into the manifest entry of each profile. It accomplishes this by matching the names in the manifest with the names you specify in your text file.

#### A.4.2 JAR File Logistics

When you specify a JAR file on the SQLJ command line, each profile in the JAR file is deserialized and customized.

A JAR file is successfully customized only if all the profiles it contains are successfully customized. After a successful customization, each profile has been reserialized into a `.ser` file, the JAR file has been modified to replace the original `.ser` files with the customized `.ser` files, and the JAR file manifest has been updated to indicate the new entries.

If any error is encountered in the customization of any profile in a JAR file, then the JAR file customization has failed, and the original JAR file is left completely unchanged.

**Note:**

If you use signature files for authentication, the signature files that appeared in the original JAR file will appear unchanged in the updated JAR file. You are responsible for resigning the new JAR file if the profiles require signing.

### A.5 SQLCheckerCustomizer for Profile Semantics-Checking

Oracle provides a special customizer, `SQLCheckerCustomizer`, that will perform semantics-checking on a profile that was produced during previous execution of the translator. This semantics-checking is similar to what is usually performed during translation of the source code.

This is particularly valuable when the database to be used at run time is not available for semantics-checking during translation. In these circumstances, you can use `SQLCheckerCustomizer` after deployment, against the run-time database, typically in a scenario where the source code is no longer available.

You can specify the checker to use. If you accept the default `OracleChecker` front end, `SQLCheckerCustomizer` will perform online semantics-checking using an appropriate online checker.

**Note:**

For online semantics-checking of the profile, you must also specify connection parameters using the customizer harness connection options.

#### A.5.1 Invoking SQLCheckerCustomizer with the Customizer Harness verify Option

Following are examples of how to specify the Oracle customizer harness `verify` option to run `SQLCheckerCustomizer` in its default mode. Because it defaults to an online checker, you typically must provide connection parameters through the customizer harness `user`, `password`, and `url` options. (The first example is a single wraparound command line.)

    % sqlj -P-verify -P-user=HR -P-url=jdbc:oracle:oci:@ Foo_SJProfile0.ser Bar_SJProfile0.ser
    Password: password

    % sqlj -P-verify -P-user=HR -P-url=jdbc:oracle:oci:@ *.ser
    Password: password

The `verify` option results in the customizer harness instantiating and invoking the following class:

    sqlj.runtime.profile.util.SQLCheckerCustomizer

This class coordinates semantics-checking of the SQL operations in the profile. You can specify a semantics-checker or accept the default `OracleChecker` semantics-checker front end.

The `-P-verify` option is equivalent to the following:

    -P-customizer=sqlj.runtime.profile.util.SQLCheckerCustomizer

This overrides the customizer specified in the SQLJ `-default-customizer` option.

**Note:**

- As with any Oracle customizer, help output and an option list will be provided if you specify `-P-verify` together with `-P-help` on the SQLJ command line.

- It is important to realize that because the `verify` option invokes a customizer, and only one customizer can run in any single running of SQLJ, you cannot do any other customization when you use this option.

- You also cannot use more than one of `-P-print`, `-P-debug`, and `-P-verify` simultaneously, because each of these invokes a specialized customizer.

Command-line syntax is:

    sqlj -P-verify <conn params> profile_list

Command-line example is:

    sqlj -P-verify <conn params> Foo_SJProfile*.ser

Properties file syntax is:

    profile.verify

(You must also specify profiles, and typically customizer harness connection options, in the SQLJ command line.)

Properties file example is:

    profile.verify

Default value is:

    NA

#### A.5.2 SQLCheckerCustomizer Options

Like any customizer, `SQLCheckerCustomizer` has its own options, which can be set using the `-P-C` prefix on the SQLJ command line or the `profile.C` prefix in a SQLJ properties file.

`SQLCheckerCustomizer` supports the following options:

- `checker`: Specify the semantics-checker to use. The default is the `OracleChecker` front end, as for checking during SQLJ translation.

- `warn`: Specify the categories of warnings and messages to display during semantics-checking of the profile. This is equivalent to the SQLJ `-warn` flag for warning categories during translation-time semantics-checking, supports the same settings, and uses the same defaults.

##### A.5.2.1 SQLCheckerCustomizer Semantics-Checker Option (checker)

The `checker` option enables you to specify the semantics-checker to use in checking the SQL operations in a profile.

This defaults to the Oracle semantics-checker front end, `oracle.sqlj.checker.OracleChecker`, which for `SQLCheckerCustomizer` chooses an appropriate online checker for your environment.

Following is a full command-line example, showing how to use the `SQLCheckerCustomizer` `checker` option, in conjunction with the customizer harness `verify` option and connection options.

    % sqlj -P-verify -P-user=HR -P-url=jdbc:oracle:oci:@ -P-Cchecker=abc.def.MyChecker *.ser
    Password: password

(This is a single wraparound command line.)

Command-line syntax is:

    -P-Cchecker=checker_class

Command-line example is:

    -P-Cchecker=a.b.c.MyChecker

Properties file syntax is:

    profile.Cchecker=checker_class

Properties file example is:

    profile.Cchecker=a.b.c.MyChecker

Default value is:

    oracle.sqlj.checker.OracleChecker

##### A.5.2.2 SQLCheckerCustomizer Warnings Option (warn)

The `warn` option is equivalent to the SQLJ translator `-warn` option, enabling you to choose the categories of warnings and messages to be displayed as semantics-checking is performed on a profile.

This defaults to the `all,noverbose,noportable` settings, resulting in all warning categories except `verbose` and `portable` being enabled. You will receive any warnings regarding inheritance hierarchy requirements, data precision, conversion loss for nullable data, and strict matching for named iterators. These are the same defaults as for warnings during SQLJ translation.

Following is a full command-line example showing how to use the `SQLCheckerCustomizer` `warn` option, in conjunction with the customizer harness `verify` option and connection options. This would result in only portability warnings being displayed.

    % sqlj -P-verify -P-user=HR -P-url=jdbc:oracle:oci:@ -P-Cwarn=none,portable *.ser
    Password: password

(This is a single wraparound command line.)

Command-line syntax is:

    -P-Cwarn=comma-delimited_list_of_flags

Command-line example is:

    -P-Cwarn=none,verbose

Properties file syntax is:

    profile.Cwarn=comma-delimited_list_of_flags

Properties file example is:

    profile.Cwarn=none,verbose

Default value is:

    all,noverbose,noportable

### A.6 AuditorInstaller Customizer for Debugging

For ISO code generation, SQLJ provides a special customizer, `AuditorInstaller`. This customizer will insert sets of debugging statements, known as auditors, into profiles specified on the SQLJ command line. These profiles must already exist from previous customization.

The debugging statements will execute during SQLJ run time (when someone runs your application), displaying a trace of method calls and values returned.

Use the customizer harness `debug` option, preceded by `-P-` as with any general customization option, to insert the debugging statements. (Syntax for this option is discussed in "Invoking AuditorInstaller with the Customizer Harness debug Option".)

#### A.6.1 Overview of Auditors and Code Layers

When an application is customized, Oracle customizer implements profiles in layers of code (typically less than five) for different levels of run-time functionality. The deepest layer uses straight Oracle JDBC calls and implements any of your SQLJ statements that can be executed through JDBC functionality. Each higher layer is a specialized layer for some category of SQLJ functionality that is not supported by JDBC and so must be handled specially by the SQLJ run time. For example, a layer for iterator conversion statements (`CAST`) is used to convert JDBC result sets to SQLJ iterators. Another layer is used for assignment statements (`SET`).

At run time, each SQLJ executable statement is first passed to the shallowest layer and then passed, layer-by-layer, until it reaches the layer that can process it (usually the deepest layer, which executes all JDBC calls).

You can install debugging statements at only one layer during a single execution of `AuditorInstaller`. Each set of debugging statements installed at a particular layer of code is referred to as an individual auditor. During run time, an auditor is activated whenever a call is passed to the layer at which the auditor is installed.

Any one of the specialized code layers above the JDBC layer is usually of no particular interest during debugging, so it is typical to install an auditor at either the deepest layer or the shallowest layer. If you install an auditor at the shallowest layer, its run-time debugging output will be a trace of method calls resulting from all your SQLJ executable statements. If you install an auditor at the deepest layer, its run-time output will be a trace of method calls from all your SQLJ executable statements that result in JDBC calls.

Use multiple executions of `AuditorInstaller` to install auditors at different levels. You might want to do that to install auditors at both the deepest layer and the shallowest layer, for example.

See "AuditorInstaller Depth Option (depth)" for information about how to specify the layer at which to install an auditor.

#### A.6.2 Invoking AuditorInstaller with the Customizer Harness debug Option

Following are examples of how to specify the Oracle customizer harness `debug` option to run `AuditorInstaller` in its default mode:

    % sqlj -P-debug Foo_SJProfile0.ser Bar_SJProfile0.ser

    % sqlj -P-debug *.ser

    % sqlj -P-debug myappjar.jar

The `debug` option results in the customizer harness instantiating and invoking the following class:

    % sqlj.runtime.profile.util.AuditorInstaller

This class performs the work of inserting the debugging statements.

The `-P-debug` option is equivalent to the following:

    -P-customizer=sqlj.runtime.profile.util.AuditorInstaller

This overrides the customizer specified in the SQLJ `-default-customizer` option.

Be aware of the following:

- To run an application with auditors installed, the SQLJ file `translator.jar` must be in your classpath. (Usually, running a already translated SQLJ application requires only a runtime library.)

- As with any Oracle customizer, help output and an option list will be provided if you specify `-P-debug` together with `-P-help` on the SQLJ command line.

- It is important to realize that because the `debug` option invokes a customizer, and only one customizer can run in any single running of SQLJ, you cannot perform any other customization when you use this option.

- You also cannot use more than one of `-P-print`, `-P-debug`, and `-P-verify` simultaneously, because each of these invokes a specialized customizer.

Command-line syntax is:

    sqlj -P-debug profile_list

Command-line example is:

    sqlj -P-debug Foo_SJProfile*.ser

Properties file syntax is:

    profile.debug

(You must also specify profiles in the file list.)

Properties file example is:

    profile.debug

Default value is:

    NA

#### A.6.3 AuditorInstaller Run-Time Output

During run time, debugging statements placed by `AuditorInstaller` result in a trace of methods called and values returned. This happens for all profile layers that had debugging statements installed. There is no means of selective debug output at run time.

`AuditorInstaller` output relates to profiles only; there is currently no mapping to lines in your original `.sqlj` source file.

Following is a sample portion of `AuditorInstaller` run-time output. This is what the output might look like for a SQLJ `SELECT INTO` statement:

    oracle.sqlj.runtime.OraProfile@1 . getProfileData (  )
    oracle.sqlj.runtime.OraProfile@1 . getProfileData returned sqlj.runtime.profile.ref.ProfileDataImpl@2
    oracle.sqlj.runtime.OraProfile@1 . getStatement ( 0 )
    oracle.sqlj.runtime.OraProfile@1 . getStatement returned
    oracle.sqlj.runtime.OraRTStatement@3
    oracle.sqlj.runtime.OraRTStatement@3 . setMaxRows ( 1000 )
    oracle.sqlj.runtime.OraRTStatement@3 . setMaxRows returned
    oracle.sqlj.runtime.OraRTStatement@3 . setMaxFieldSize ( 3000 )
    oracle.sqlj.runtime.OraRTStatement@3 . setMaxFieldSize returned
    oracle.sqlj.runtime.OraRTStatement@3 . setQueryTimeout ( 1000 )
    oracle.sqlj.runtime.OraRTStatement@3 . setQueryTimeout returned
    oracle.sqlj.runtime.OraRTStatement@3 . setBigDecimal ( 1 , 5 )
    oracle.sqlj.runtime.OraRTStatement@3 . setBigDecimal returned
    oracle.sqlj.runtime.OraRTStatement@3 . setBoolean ( 2 , false )
    oracle.sqlj.runtime.OraRTStatement@3 . setBoolean returned
    oracle.sqlj.runtime.OraRTStatement@3 . executeRTQuery (  )
    oracle.sqlj.runtime.OraRTStatement@3 . executeRTQuery returned
    oracle.sqlj.runtime.OraRTResultSet@6
    oracle.sqlj.runtime.OraRTStatement@3 . getWarnings (  )
    oracle.sqlj.runtime.OraRTStatement@3 . getWarnings returned null
    oracle.sqlj.runtime.OraRTStatement@3 . executeComplete (  )
    oracle.sqlj.runtime.OraRTStatement@3 . executeComplete returned
    oracle.sqlj.runtime.OraRTResultSet@6 . next (  )
    oracle.sqlj.runtime.OraRTResultSet@6 . next returned true
    oracle.sqlj.runtime.OraRTResultSet@6 . getBigDecimal ( 1 )
    oracle.sqlj.runtime.OraRTResultSet@6 . getBigDecimal returned 5
    oracle.sqlj.runtime.OraRTResultSet@6 . getDate ( 7 )
    oracle.sqlj.runtime.OraRTResultSet@6 . getDate returned 1998-03-28

There are two lines for each method call. The first shows the call and input parameters; the second shows the return value.

**Note:**

The classes you see in the `oracle.sqlj.runtime` package are SQLJ run-time classes with equivalent functionality to similarly named JDBC classes. For example, `OraRTResultSet` is the SQLJ run-time implementation of the JDBC `ResultSet` interface, containing equivalent attributes and methods.

#### A.6.4 AuditorInstaller Options

As with any customizer, `AuditorInstaller` has its own options that can be set using the `-P-C` prefix on the SQLJ command line (or `profile.C` in a SQLJ properties file).

`AuditorInstaller` supports the following options:

- `depth`: Specify how deeply you want to go into the layers of run-time functionality in your profiles.

- `log`: Specify the target file for run-time output of the debugging statements of the installed auditor.

- `prefix`: Specify a prefix for each line of run-time output that will result from this installation of debugging statements.

- `showReturns`: Enable the installed auditor to include return arguments in its run-time call tracing.

- `showThreads`: Enable the installed auditor to include thread names in its run-time call tracing (relevant only for multithreaded applications).

- `uninstall`: Remove the debugging statements placed into the profiles during the most recent previous invocation of `AuditorInstaller` on those profiles.

##### A.6.4.1 AuditorInstaller Depth Option (depth)

As discussed in "Overview of Auditors and Code Layers", `AuditorInstaller` can install a set of debugging statements, known as an auditor, at only a single layer of code during any one execution. The `AuditorInstaller` `depth` option enables you to specify which layer. Use multiple executions of `AuditorInstaller` to install auditors at different levels.

Layers are numbered in integers. The shallowest depth is layer 0; a maximum depth of 2 or 3 is typical. The only depth settings typically used are 0 for the shallowest layer or -1 for the deepest layer. In fact, it is difficult to install an auditor at any other particular layer, because the layer numbers used for the various kinds of SQLJ executable statements are not publicized.

The `depth` option is sometimes used in conjunction with the `prefix` option. By running `AuditorInstaller` more than once, with different prefixes for different layers, you can see at runtime what information is coming from which layers.

If you do not set the `depth` option, or the specification exceeds the number of layers in a given profile, then an auditor will be installed at the deepest layer.

Command-line syntax is:

    -P-Cdepth=n

Command-line example is:

    -P-Cdepth=0

Properties file syntax is:

    profile.Cdepth=n

Properties file example is:

    profile.Cdepth=0

Default value is:

    -1 (deepest layer)

##### A.6.4.2 AuditorInstaller Log File Option (log)

Use the `log` option to specify an output file for runtime output that will result from the auditor that you are currently installing. Otherwise, standard output will be used, so that debug output will go to wherever SQLJ messages go.

When auditors write messages to an output file, they append; they do not overwrite. Therefore, you can specify the same log file for multiple auditors without conflict. In fact, it is typical in this way to have debug information from all layers of your application go to the same log file.

Command-line syntax is:

    -P-Clog=log_file

Command-line example is:

    -P-Clog=foo/bar/mylog.txt

Properties file syntax is:

    profile.Clog=log_file

Properties file example is:

    profile.Clog=foo/bar/mylog.txt

Default value is:

    Empty (for standard output)

##### A.6.4.3 AuditorInstaller Prefix Option (prefix)

Use the `prefix` option to specify a prefix for each line of runtime output resulting from the debugging statements installed during this invocation of `AuditorInstaller`.

This option is often used in conjunction with the `depth` option. By running `AuditorInstaller` multiple times with different prefixes for different layers, you can easily see at runtime what information is coming from which layers.

Command-line syntax is:

    -P-Cprefix="string"

Command-line example is:

    -P-Cprefix="layer 2: "

Properties file syntax is:

    profile.Cprefix="string"

Properties file example is:

    profile.Cprefix="layer 2: "

Default value is:

    Empty

##### A.6.4.4 AuditorInstaller Return Arguments Option (showReturns)

Use the `showReturns` option to enable or disable the display of return arguments as part of the runtime call tracing. This is enabled by default.

The following few lines show sample output with `showReturns` enabled (default):

    oracle.sqlj.runtime.OraRTStatement@3 . executeComplete (  )
    oracle.sqlj.runtime.OraRTStatement@3 . executeComplete returned
    oracle.sqlj.runtime.OraRTResultSet@6 . next (  )
    oracle.sqlj.runtime.OraRTResultSet@6 . next returned true
    oracle.sqlj.runtime.OraRTResultSet@6 . getBigDecimal ( 1 )
    oracle.sqlj.runtime.OraRTResultSet@6 . getBigDecimal returned 5
    oracle.sqlj.runtime.OraRTResultSet@6 . getDate ( 7 )
    oracle.sqlj.runtime.OraRTResultSet@6 . getDate returned 1998-03-28

With `showReturns` disabled, the output would appear as follows:

    oracle.sqlj.runtime.OraRTStatement@3 . executeComplete (  )
    oracle.sqlj.runtime.OraRTResultSet@6 . next (  )
    oracle.sqlj.runtime.OraRTResultSet@6 . getBigDecimal ( 1 )
    oracle.sqlj.runtime.OraRTResultSet@6 . getDate ( 7 )

Instead of both a call line and a return line for each method call, there is only a call line.

Command-line syntax is:

    -P-CshowReturns<=true|false>

Command-line example is:

    -P-CshowReturns=false

Properties file syntax is:

    profile.CshowReturns<=true|false>

Properties file example is:

    profile.CshowReturns=false

Default value is:

    true

##### A.6.4.5 AuditorInstaller Thread Names Option (showThreads)

Use the `showThreads` option to enable or disable the display of thread names as part of the runtime call tracing (relevant only for multithreaded applications). This is disabled by default.

When this option is enabled, thread names prefix the method names in the trace output.

Command-line syntax is:

    -P-CshowThreads<=true|false>

Command-line example is:

    -P-CshowThreads

Properties file syntax is:

    profile.CshowThreads<=true|false>

Properties file example is:

    profile.CshowThreads

Default value is:

    false

##### A.6.4.6 AuditorInstaller Uninstall Option (uninstall)

Use the `uninstall` option to remove debugging statements placed during previous invocations of `AuditorInstaller`. Each time you use the `uninstall` option, it will remove the auditor most recently installed.

To remove all auditors from a profile, run `AuditorInstaller` repeatedly until you get a message indicating that the profile was unchanged.

Command-line syntax is:

    -P-Cuninstall

Command-line example is:

    -P-Cuninstall

Properties file syntax is:

    profile.Cuninstall

Properties file example is:

    profile.Cuninstall

Default value is:

    Disabled

#### A.6.5 Full Command-Line Examples

Following are some full SQLJ command-line examples showing the specification of `AuditorInstaller` options.

Insert a set of debugging statements, or auditor, into the deepest layer (which is the default layer), with runtime output to standard output:

    % sqlj -P-debug MyApp_SJProfile*.ser

Insert an auditor into the deepest layer, with runtime output to `log.txt`:

    % sqlj -P-debug -P-Clog=foo/bar/log.txt MyApp_SJProfile*.ser

Insert an auditor into the deepest layer, with runtime output to standard output, showing thread names but not return arguments:

    % sqlj -P-debug -P-CshowThreads=true -P-CshowReturns=false MyApp_SJProfile*.ser

Insert an auditor into layer 0 (the shallowest layer). Send runtime output to `log.txt`; prefix each line of runtime output with "`Layer 0: `" (the following command is a single wraparound line):

    % sqlj -P-debug -P-Clog=foo/bar/log.txt -P-Cdepth=0 -P-Cprefix="Layer 0: "
    MyApp_SJProfile*.ser

Uninstall an auditor (this uninstalls the auditor most recently installed; do it repeatedly to uninstall all auditors):

    % sqlj -P-debug -P-Cuninstall MyApp_SJProfile*.ser
