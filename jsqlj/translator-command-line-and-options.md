Once you have written your source code, you must translate it using the SQLJ translator. This chapter covers the SQLJ translator command line options and properties files. The following topics are covered:

- Translator Command Line and Properties Files

- Basic Translator Options

- Advanced Translator Options

- Translator Support and Options for Alternative Environments

### 9.1 Translator Command Line and Properties Files

The `sqlj` script invokes a Java virtual machine (JVM) and passes the class name of the SQLJ translator, `sqlj`.`tools`.`Sqlj`, to the JVM. The JVM invokes the translator and performs operations such as parsing the command line and properties files. For simplicity, running the script is referred to as running SQLJ, and its command line is referred to as the SQLJ command line.

The typical general syntax for the command line is as follows:

    % sqlj <optionlist> filelist

The `optionlist` is a list of SQLJ option settings separated by spaces. There are also prefixes to mark options to pass to the Java interpreter, compiler, and customizer.

The `filelist` is the list of files, delimited by spaces, to be processed by the SQLJ translator. The files can be .`sqlj`, `.java`, `.ser`, or `.jar` files. The `*` wildcard entry can be used in file names. For example, `Foo*.sqlj` would find `Foo1.sqlj`, `Foo2.sqlj,` and `Foobar.sqlj`.

**Note:**

- All options need not precede the file list. Options may appear anywhere in the command line and are processed in order.

- All command-line options apply to all files being translated. It is not possible to have file-specific option settings.

Do not include `.class` files in the file list, but ensure that your classpath is set so that the SQLJ translator can find any classes it must have for type resolution of variables in your SQLJ source files. If the -`checksource` flag is enabled, which is the default setting, then the SQLJ translator can also find classes it needs in uncompiled `.java` files in the classpath.

**Note:**

If you run the script by entering only `sqlj`, you will receive a synopsis of the most frequently used SQLJ options. In fact, this is true whenever you run the script without specifying any files to process. This is equivalent to using the -`help` flag setting.

This section covers the following topics:

- SQLJ Options\_ Flags\_ and Prefixes

- Command-Line Syntax and Operations

- Properties Files for Option Settings

- SQLJ_OPTIONS Environment Variable for Option Settings

- Order of Precedence of Option Settings

#### 9.1.1 SQLJ Options, Flags, and Prefixes

This section discusses options supported by the SQLJ translator. Boolean options are referred to as flags. Prefixes used to pass options to the JVM, which the SQLJ script invokes, and to the Java compiler and SQLJ profile customizer, which the JVM invokes, are also listed.

##### Summary of SQLJ Options

Table 9-1 lists options supported by the SQLJ translator, categorized as follows:

- Flags and options listed as Basic are discussed in "Basic Translator Options".

- Flags, options, and prefixes listed as Advanced are discussed in "Advanced Translator Options".

- Flags and options listed as Environment are discussed in "Translator Support and Options for Alternative Environments". These flags and options are for use of a nonstandard JVM, compiler, or customizer.

- Options with a category of `javac` are `javac` compiler options that SQLJ recognizes directly, without the compiler prefix. They are passed to the Java compiler, typically `javac`, and some also affect SQLJ translator settings. These options are discussed in "Option Support for javac".

Table 9-1 SQLJ Translator Options

| Option                             | Description                                                                                                                                                                                                                                                                                                        | Default                                                                                                                                      | Category    |
|:-----------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------|:------------|
| `-bind-by-identifier`              | Flag to treat multiple appearances of the same host variable in a given SQLJ statement as a single bind occurrence.                                                                                                                                                                                                | `false`                                                                                                                                      | Advanced    |
| `-C`                               | Prefix that marks options to pass to the Java compiler.                                                                                                                                                                                                                                                            | NA                                                                                                                                           | Advanced    |
| `-cache`                           | Enables caching of online semantics-checking results (to reduce trips to database).                                                                                                                                                                                                                                | `false`                                                                                                                                      | Advanced    |
| `-checkfilename`                   | Specifies whether a warning is issued during translation if a source file name does not correspond to the name of the public class (if any) defined there.                                                                                                                                                         | `true`                                                                                                                                       | Environment |
| `-checksource`                     | Instructs SQLJ type resolution to examine source files in addition to class files in certain circumstances.                                                                                                                                                                                                        | `true`                                                                                                                                       | Advanced    |
| `-classpath`                       | Specifies the classpath to the JVM and Java compiler; also passed to `javac`. Use this on the command line only.                                                                                                                                                                                                   | None                                                                                                                                         | Basic       |
| `-codegen`                         | Specifies mode of code generation: `oracle` for Oracle-specific code generation with direct Oracle Java Database Connectivity (JDBC) calls; `iso` for ISO standard SQLJ code generation.                                                                                                                           | `oracle`                                                                                                                                     | Basic       |
| `-compile`                         | Enables or disables the Java compilation step, either for `.java` files generated during the current SQLJ run or for previously generated or other `.java` files specified on the command line.                                                                                                                    | `true`                                                                                                                                       | Advanced    |
| `-compiler-executable`             | Specifies the Java compiler to use.                                                                                                                                                                                                                                                                                | `javac`                                                                                                                                      | Environment |
| `-compiler-encoding- flag`         | Instructs SQLJ whether to pass the -`encoding` setting, if set, to the Java compiler.                                                                                                                                                                                                                              | `true`                                                                                                                                       | Environment |
| `-compiler-output-file`            | Specifies a file to which the Java compiler output should be written. If this option is not set, then SQLJ assumes that compiler output goes to standard output.                                                                                                                                                   | None                                                                                                                                         | Environment |
| `-compiler-pipe-output-flag`       | Instructs SQLJ whether to set the `javac.pipe.output` system property, which determines whether the Java compiler prints errors and messages to `STDOUT` instead of `STDERR`.                                                                                                                                      | `true`                                                                                                                                       | Environment |
| `-components`                      | Specifies the components (packages and classes) to instrument for use with Oracle Dynamic Monitoring Service (DMS). This assumes instrumentation is enabled through the -`instrument` option. Use `all` to instrument all components being translated.                                                             | `all`                                                                                                                                        | Basic       |
| `-d`                               | Specifies the output directory for `.ser` profile files, if applicable, generated by SQLJ, and `.class` files generated by the compiler; also passed to `javac`.                                                                                                                                                   | Empty<br>(Use directory of `.java` files to place generated `.class` files; use directory of `.sqlj` files to place generated `.ser` files.) | Basic       |
| `-default-customizer`              | Determines the profile customizer to use. Specify a class name.                                                                                                                                                                                                                                                    | `oracle.sqlj. runtime.util. OraCustomizer`                                                                                                   | Environment |
| `-default-url-prefix`              | Sets the default prefix for URL settings.                                                                                                                                                                                                                                                                          | `jdbc:oracle:thin:`                                                                                                                          | Basic       |
| `-depend`                          | Passed to `javac`; enables -`checksource`. This option requires the -`C` compiler prefix if set in a properties file.                                                                                                                                                                                              | NA                                                                                                                                           | `javac`     |
| `-deprecation`                     | Passed to `javac` only. This option requires the -`C` compiler prefix if set in a properties file.                                                                                                                                                                                                                 | NA                                                                                                                                           | `javac`     |
| `-dir`                             | Sets the output directory for SQLJ-generated `.java` files.                                                                                                                                                                                                                                                        | Empty<br>(Use directory of `.sqlj` input file.)                                                                                              | Basic       |
| `-driver`                          | Determines the JDBC driver class to register. Specify a class name or comma-delimited list of class names.                                                                                                                                                                                                         | oracle.jdbc.OracleDriver                                                                                                                     | Basic       |
| `-encoding`                        | Specifies the encoding that SQLJ and the compiler will use in globalization support; also passed to `javac`. You can use -`e` on the command line.                                                                                                                                                                 | JVM `file.encoding` setting                                                                                                                  | Basic       |
| `-explain`                         | Flag to request cause and action information to be displayed with translator error messages.                                                                                                                                                                                                                       | `false`                                                                                                                                      | Basic       |
| `-fixedchar`                       | Flag to account for blank padding when binding a string into a `WHERE` clause for comparison with `CHAR` data.                                                                                                                                                                                                     | `false`                                                                                                                                      | Basic       |
| `-g`                               | Passed to `javac`; enables -`linemap`. This option requires the -`C` compiler prefix if set in a properties file.                                                                                                                                                                                                  | NA                                                                                                                                           | `javac`     |
| `-help` `-help-long` `-help-alias` | Flags to display different levels of information about SQLJ option names, descriptions, and current values. Use these on the command line only. You can use -`h` instead of -`help`.                                                                                                                               | Disabled                                                                                                                                     | Basic       |
| `-instrument`                      | Specifies whether to instrument translated files for use with Oracle DMS.                                                                                                                                                                                                                                          | `false`                                                                                                                                      | Basic       |
| `-jdblinemap`                      | Variant of -`linemap` option for use with the Sun Microsystems `jdb` debugger.                                                                                                                                                                                                                                     | `false`                                                                                                                                      | Basic       |
| `-J`                               | Prefix that marks options to pass to the JVM. Use this on the command line only.                                                                                                                                                                                                                                   | NA                                                                                                                                           | Advanced    |
| `-linemap`                         | Enables mapping of line numbers between the generated Java class file and the original SQLJ code.                                                                                                                                                                                                                  | `false`                                                                                                                                      | Basic       |
| `-n`                               | Instructs the `sqlj` script to echo the full command line as it would be passed to the SQLJ translator, including settings in `SQLJ_OPTIONS`, without having the translator execute it. This is equivalent to `-vm=echo`. Use this on the command line only.                                                       | Disabled                                                                                                                                     | Basic       |
| `-ncharconv`                       | Performs bind to `NCHAR` columns for `String` host variables.                                                                                                                                                                                                                                                      | `false`                                                                                                                                      | Basic       |
| `-nowarn`                          | Passed to `javac`; sets `-warn=none`. This option requires the -`C` compiler prefix if set in a properties file.                                                                                                                                                                                                   | NA                                                                                                                                           | `javac`     |
| `-O`                               | Passed to `javac`; disables -`linemap`. This option requires the -`C` compiler prefix if set in a properties file.                                                                                                                                                                                                 | NA                                                                                                                                           | `javac`     |
| `-offline`                         | Determines the offline checker to use for semantics-checking. Specify a list of fully qualified class names.                                                                                                                                                                                                       | oracle.sqlj.checker. OracleChecker                                                                                                           | Advanced    |
| `-online`                          | Determines the online checker to use for semantics-checking. Specify a fully qualified class name. (You must also set -`user` to enable online checking.)                                                                                                                                                          | oracle.sqlj.checker. OracleChecker                                                                                                           | Advanced    |
| `-optcols`                         | Enables iterator column type and size definitions to optimize performance. It is used directly by the translator for Oracle-specific code generation, or forwarded to Oracle customizer along with user, password, and URL settings for ISO code generation.                                                       | `false`                                                                                                                                      | Basic       |
| `-optparams`                       | Enables parameter size definitions to optimize JDBC resource allocation (used with -`optparamdefaults`). This is used directly by the translator for Oracle-specific code generation, or forwarded to Oracle customizer for ISO code generation.                                                                   | `false`                                                                                                                                      | Basic       |
| `-optparamdefaults`                | Sets parameter size defaults for particular data types (used with -`optparams`). This is used directly by the translator for Oracle-specific code generation, or forwarded to Oracle customizer for ISO code generation.                                                                                           | `false`                                                                                                                                      | Basic       |
| `-P`                               | Prefix that marks options to pass to the SQLJ profile customizer.                                                                                                                                                                                                                                                  | NA                                                                                                                                           | Advanced    |
| `-parse`                           | Option to enable the offline SQL parser. Possible settings: `both`, `online`-`only`, `offline`-`only`, `none`, or the name of a Java class that implements an alternative parser.<br>Note: Some settings for this option will also disable online semantics-checking, overriding the effect of the -`user` option. | `both`                                                                                                                                       | Advanced    |
| `-passes`                          | Instructs the `sqlj` script to run SQLJ in two separate passes, with compilation in between. Use this on the command line only.                                                                                                                                                                                    | `false`                                                                                                                                      | Environment |
| `-password`                        | Sets the user password for the database connection for online semantics-checking. You can use -`p` on the command line.                                                                                                                                                                                            | None                                                                                                                                         | Basic       |
| `-profile`                         | For ISO code generation, enables or disables the profile customization step for profile files generated during the current SQLJ run.                                                                                                                                                                               | `true`                                                                                                                                       | Advanced    |
| `-props`                           | Specifies a properties file, an alternative to the command line for setting options. (The `sqlj`.`properties` is also still read.) Use this on the command line only.                                                                                                                                              | None                                                                                                                                         | Basic       |
| `-ser2class`                       | For ISO code generation, instructs SQLJ to translate generated `.ser` profiles to `.class` files.                                                                                                                                                                                                                  | `false`                                                                                                                                      | Advanced    |
| `-status`                          | Requests SQLJ to display status messages as it runs. Instead of -`status`, you can use -`v` on the command line.                                                                                                                                                                                                   | `false`                                                                                                                                      | Basic       |
| `-url`                             | Sets the URL for the database connection for online semantics-checking.                                                                                                                                                                                                                                            | `jdbc:oracle:oci:@`                                                                                                                          | Basic       |
| `-user`                            | Enables online semantics-checking and sets the user name (and optionally password and URL) for the database connection. You can use -`u` on the command line.                                                                                                                                                      | None (no online semantics-checking)                                                                                                          | Basic       |
| `-verbose`                         | Passed to `javac`; enables -`status`. This requires the -`C` compiler prefix if set in a properties file.                                                                                                                                                                                                          | NA                                                                                                                                           | `javac`     |
| `-version` `-version-long`         | Flag to display different levels of SQLJ and JDBC driver version information. Use these settings on the command line only.                                                                                                                                                                                         | Disabled                                                                                                                                     | Basic       |
| `-vm`                              | Specifies the JVM to use for running the SQLJ translator. Use this on the command line only.                                                                                                                                                                                                                       | `java`                                                                                                                                       | Environment |
| `-warn`                            | Comma-delimited list of flags to enable or disable different SQLJ warnings. Individual flags are `cast`/`nocast` `precision`/`noprecision`, `nulls`/`nonulls`, `portable`/`noportable`, `strict`/`nostrict`, and `verbose`/`noverbose`. The global flag is `all`/`none`.                                           | `cast precision nulls noportable strict noverbose`                                                                                           | Basic       |

##### Notes Regarding Options, Flags, and Prefixes

Keep the following in mind:

- Flags, options, and prefixes listed as command line only in the Description column of the preceding table cannot be set in a properties file.

- The names of command-line options, including options passed elsewhere, are case-sensitive and usually all lowercase. Option values are usually case-sensitive as well.

- Most SQLJ options can also be set in a properties file.

- The `SQLJ_OPTIONS` environment variable can be used in addition to, or instead of, the command line for setting options.

- In this document, boolean flags are usually discussed as being `true` or `false`, but they can also be enabled or disabled by setting them to `yes`/`no`, `on`/`off`, or `1`/`0`.

**See Also:**

"Command-Line Syntax and Operations"

##### Notes Regarding the -password Option

You can choose one of the following ways to provide the password, ensuring that it is not being intercepted by other users through utilities such as `ps`:

- Omit the` -password` argument. In this case, you will be prompted on the command line to enter the password. Then the password argument will not be visible to the operating system.

- Place the password setting into a properties file, and instruct the SQLJ translator to use this properties file. Thus it is possible to script SQLJ translation without exposing the password to the operating system.

- Use SQLJ under JDeveloper. This does not expose the password to the operating system.

##### Options for loadjava Compatibility

For compatibility with the `loadjava` utility used to load Java and SQLJ applications into an Oracle Database 12c Release 2 (12.2) instance, the following alternative syntax is recognized for the indicated options when specified on the command line:

- \-`e` (for `-encoding`)

- \-`h` (for -`help`)

- \-`p` (for -`password`)

- \-`u` (for -`user`)

- \-`v` (for verbose message output; equivalent to -`status`)

To maintain full consistency with `loadjava` syntax, you can use a space instead of equal sign (=) in setting these options, as in the following example:

    -u HR -v -e SJIS

**Note:**

This alternative option syntax is recognized only on the command line or in the `SQLJ_OPTIONS` environment variable, not in properties files.

**See Also:**

[Oracle Database Java Developer’s Guide](../jjdev/loadjava-tool.md)

##### Option Support for javac

SQLJ supports option settings for `javac`, the Java compiler supplied with the Sun Microsystems Java Development Kit (JDK), in the following ways:

- Some `javac` options that take values are combined into SQLJ options (`-classpath`, `-d`, `-encoding`).

- For other `javac` options that take values, special processing has been implemented to correctly pass the value to the compiler (`-bootclasspath`, `-extdirs`, `-target`). These require a compiler prefix. They have no effect on SQLJ operation.

- Flags for `javac` are recognized on the command line without a `compiler` prefix (`-depend`, `-deprecation`, `-g`, `-nowarn`, `-O`, `-verbose`). Some of these flags affect SQLJ translator flag settings as well.

This is summarized in Table 9-2. All of these options can be set on the SQLJ command line or in a properties file, though sometimes a compiler prefix is required, as noted in the table.

**Note:**

- By default, `javac` compiles classes against the bootstrap and extension classes of the platform with which it was shipped. But `javac` also supports cross-compiling classes against bootstrap and extension classes of a different Java platform. The `javac` `-bootclasspath` and `-extdirs` options are for use in cross-compiling (JDK 6).

- By default, `javac` generates `.class` files that are compatible with the JDK version from which `javac` was obtained. Use the `-target` option to alter this.

Table 9-2 SQLJ Support for javac Options

| Command-Line Option (with -C Prefix if Noted) | Description                                                                                                     | Relationship to SQLJ                    |
|:----------------------------------------------|:----------------------------------------------------------------------------------------------------------------|:----------------------------------------|
| `-C-bootclasspath`                            | Instructs `javac` to cross-compile against the specified set of bootstrap classes.                              | None                                    |
| `-classpath`                                  | Sets the classpath for `javac` and the JVM.                                                                     | This is also a SQLJ option.             |
| `-d`                                          | Sets the output directory for `.class` files and SQLJ profile files.                                            | This is also a SQLJ option              |
| `-depend`                                     | Instructs `javac` to compile out-of-date files recursively.                                                     | Enables the SQLJ `-checksource` option. |
| `-deprecation`                                | Instructs `javac` to output source locations where deprecated APIs are used.                                    | None                                    |
| `-encoding`                                   | Sets the encoding for both `SQLJ` and `javac`.                                                                  | This is also a SQLJ option.             |
| `-C-extdirs`                                  | Instructs `javac` to cross-compile against the specified extension directories.                                 | None                                    |
| `-g`                                          | Generates `javac` debugging information.                                                                        | Enables the `SQLJ` `-linemap` option.   |
| `-nowarn`                                     | Instructs `javac` to generate no warnings.                                                                      | Sets the `SQLJ` option `-warn=none`.    |
| `-O`                                          | Instructs `javac` to optimize.                                                                                  | Disables the `SQLJ` `-linemap` option.  |
| `-C-target`                                   | Instructs `javac` to generate `.class` files to work only on JVMs of the specified JDK version level or higher. | None                                    |
| `-verbose`                                    | Instructs `javac` to produce real-time status messages.                                                         | Enables the `SQLJ` `-status` option.    |

Refer to `javac` documentation for additional information about `javac` option settings and functionality.

##### Syntax Notes for javac Options

Keep the following in mind regarding the `javac` options syntax:

- If you want to set different classpath values for the Java compiler and for the JVM that runs SQLJ, then you must use separate settings, one with a `-C` prefix and one with a `-J` prefix. Otherwise, no prefix is required.

- Do not use the `-C` prefix to specify the `-d` or `-encoding` compiler options. Note that this also means that SQLJ and the compiler use the same settings for `-d` and `-encoding`.

- You can optionally use the `-C` prefix for `-depend`, `-deprecation`, `-g`, `-nowarn`, `-O`, and `-verbose`.

- All `javac` options, aside from those that are also SQLJ options (`-classpath`, `-d`, and `-encoding`) require the `compile.` prefix if you set them in a properties file.

- For consistency, it is advisable to use an equal sign (=) for options that take values, but a space also works when using a compiler prefix (`-C` on the command line or `compile.` in a properties file).

##### Example

The following example, which is a single wraparound command line, uses the `-C-bootclasspath`, `-C-extdirs`, and `-C-target options`.

    % sqlj -vm=/usr/local/packages/jdk6/bin/java
           -compiler-executable=/usr/local/packages/jdk6/bin/javac
           -C-bootclasspath=/usr/local/packages/jdk6/jre/lib/rt.jar
           -C-extdirs="" -C-target=1.1.8 Demo.sqlj

##### Profile Customizer Options

Profile customizer options, that is, options for the customizer harness front end, the default Oracle customizer, and special customizers for debugging and deployment-time semantics-checking, are documented in " [Customization and Specialized Customizers](appendix.md)". This is relevant for ISO standard code generation only (`-codegen`=`iso`).

#### 9.1.2 Command-Line Syntax and Operations

The general sequence of events triggered by running the script `sqlj` was discussed in "[SQLJ Translation Steps](intro-to-SQLJ.md)". This section will add some operational details to that discussion, as part of this overview of the command line.

##### Use of Command-Line Arguments

Recall the typical general syntax for the command line:

    % sqlj <optionlist> filelist

When the `sqlj` script invokes a JVM, it passes all of its command-line arguments to the JVM, which later passes them elsewhere, such as to the Java compiler or profile customizer, as appropriate.

Use an equal sign (=) to specify option and flag settings, although for simplicity you do not have to specify `=true` to turn on a flag. Typing the flag name alone will suffice. However, you must specify `=false` to turn a flag off. A flag will not toggle from its previous value. For example:

`-linemap=true` or just `-linemap` to enable line-mapping

`-linemap=false` to disable line-mapping

**Note:**

If the same option appears more than once on the command line or in the properties file, then the last value is used.

##### Arguments from the Option List

Option list arguments are used in the following ways:

- Options not designated by the `-J`, `-C`, or `-P` prefixes are SQLJ options (except for directly supported compiler options) and are passed to the SQLJ translator as the JVM invokes it.

- Options designated by the `-J` prefix are JVM options and are used by the JVM directly. Such options must be specified on the command line or in the `SQLJ_OPTIONS` environment variable. As with translator options, use an equal sign (=) in setting the option, such as:

      -J-Djavac.pipe.output=true

  If you want to set different classpath values for the Java compiler and for the JVM that runs SQLJ, you must use separate settings, one with a `-C` prefix and one with a `-J` prefix.

- Options designated by the `-C` prefix are Java compiler options and are passed to the compiler as the JVM invokes it. Compiler options taking values require special support, which has been implemented for `javac` options. You can use an equal sign for these, as follows (though a space also works):

      -C-bootclasspath=/usr/local/packages/jdk6/jre/lib/rt.jar

- Options designated by the `-P` prefix are SQLJ profile customizer options and are passed to the customizer as the JVM invokes it (relevant only for ISO standard code generation, `-codegen``=``iso`). As with translator options, use an equal sign (=) in setting the option, such as:

      -P-user=HR

  Any profile customization other than what SQLJ performs automatically is considered an advanced feature.

  **See Also:**

  [Customization and Specialized Customizers](appendix.md)

##### Arguments from the File List

The SQLJ front end parses the file list, processes wildcard characters, and expands file names. By default, files are processed as follows:

- The `.sqlj` files are processed by the SQLJ translator, Java compiler, and SQLJ profile customizer (profile customizer for `-codegen``=``iso` only).

- The `.java` files are processed by the Java compiler and are also used by the SQLJ translator for type resolution.

- The `.ser` profiles and `.jar` files are processed only by the profile customizer (relevant only for `-codegen``=``iso`).

Note that you can specify `.sqlj` files together with `.java` files on the command line, or you can specify `.ser` files together with `.jar` files, but you cannot mix the two categories. If you have `.sqlj` files and `.java` files with interdependencies, each requiring access to code in the others, then enter them all on the command line for a single execution of SQLJ. You cannot specify them for separate executions of SQLJ, because then SQLJ would be unable to resolve all the types.

**Note:**

As an alternative to entering `.java` file names on the command line, you can enable the `-checksource` option and then ensure that the `.java` files are in the classpath.

##### Processing to Avoid Source Conflicts

The SQLJ translator takes steps to try to prevent having multiple source files define the same class in the same location. If your command-line file list includes multiple references to the same `.sqlj` or `.java` file, then all but the first reference are discarded from the command line. In addition, if you list a `.java` and `.sqlj` file with the same base name and in the same location without using the `-dir` option, then only the `.sqlj` file is processed. This processing also applies to wildcard characters.

Consider the following command-line examples, where `%` is the system prompt. Assume that your current directory is `/myhome/mypackage`, which contains the files `Foo.sqlj` and `Foo.java`:

    % sqlj Foo.sqlj /myhome/mypackage/Foo.sqlj

These both refer to the same file, so the translator discards `/myhome/mypackage/Foo.sqlj` from the command line.

    % sqlj Foo.sqlj Foo.java

The translator discards `Foo.java` from the command line. Otherwise, this command line would result in the translator writing and reading from `Foo.java` in the same execution.

    % sqlj Foo.*

Again, the translator discards `Foo.java` from the command line. Otherwise, the translator would find both `Foo.sqlj` and `Foo.java`, which again would cause it to write and read from `Foo.java` in the same execution.

    % sqlj -dir=outdir -d=outclasses Foo.sqlj Foo.java

This is fine, because the generated `Foo.java` will be in the `outdir` subdirectory, while the `Foo.java` being read is in the `/myhome/mypackage` directory. Presuming that `Foo.java` and `Foo.sqlj` define classes in different packages, the `.class` files created by Java compilation will be placed in different subdirectories under the `outclasses` directory hierarchy.

This processing of the command line means that you can, for example, type the following command and have it execute without difficulty (with file references being automatically discarded as necessary):

    % sqlj *.sqlj *.java

This is convenient in many situations.

##### Command-Line Example and Results

The following is a sample command line, where `%` is the system prompt. This example uses some advanced concepts more fully explained later in this chapter, but is presented in the interest of showing a complete example of command-line syntax.

    % sqlj -J-Duser.language=ja  -warn=none -J-prof -encoding=SJIS *Bar.sqlj Foo*.java

The `sqlj` script invokes a JVM, passes it the class name of the SQLJ translator, then passes it the command-line arguments. The JVM passes the SQLJ options to the translator and compiler. If there are any options for the JVM, as designated by `-J`, then the script passes them to the JVM ahead of the translator class file name (just as you would type Java options prior to typing the class file name if you were invoking Java manually). There is no customization in this example, because it uses the default Oracle-specific code generation.

After these steps are completed, the results are equivalent to the user having typed the following (presuming `SushiBar.sqlj`, `DiveBar.sqlj`, `FooBar.java`, and `FooBaz.java` were all in the current directory):

    % java -Duser.language=ja -prof sqlj.tools.Sqlj -warn=none -encoding=SJIS SushiBar.sqlj DiveBar.sqlj FooBar.java FooBaz.java

Note that this is one wraparound command line.

##### Echoing the Command Line without Executing

You can use the SQLJ `-n` option (or, alternatively, `-vm`=`echo`) to echo the command line that the `sqlj` script would construct and pass to the SQLJ translator, without executing it. This includes settings in the `SQLJ_OPTIONS` environment variable as well as on the command line, but does not include settings in properties files.

#### 9.1.3 Properties Files for Option Settings

You can use properties files, instead of the command line, to set options for the SQLJ translator, Java compiler, and SQLJ profile customizer.

In addition, if your Java compiler will be running in a separate JVM and you want to specify options to this JVM regarding operation of the compiler, then you can use properties files to supply such options. Such options are passed to the JVM at the time the compiler is run, after the SQLJ translation step. However, it is typical to pass options to the JVM of the compiler by using the command-line `-C-J` prefix.

You cannot use properties files to set the following SQLJ options, flags, and prefixes:

- `-classpath`

- `-help`, `-help-long`, `-help-alias`, `-C-help`, `-P-help`

- `-J`

- `-n`

- `-passes`

- `-props`

- `-version`, `-version-long`

- `-vm`

It is not possible to use properties files to specify options to the JVM, for example, because properties files are read after the JVM is invoked.

Also note that in properties files you cannot use option abbreviations recognized on the command line for compatibility with `loadjava` (`-e`, `-h`, `-p`, `-u`, `-v`).

##### Properties File Syntax

Option settings in a properties file are placed one per line. Lines with SQLJ options, compiler options, and customizer options can be interspersed. They are parsed by the SQLJ front end and processed appropriately.

Syntax for the different kinds of options is as follows:

- Each SQLJ option is prefixed by `sqlj.` (including the period) instead of an initial hyphen. Only options that start with this prefix are passed to the SQLJ translator. For example:

      sqlj.warn=none
      sqlj.linemap=true

- Each Java compiler option is prefixed by `compile.` (including the period) instead of `-C-`. Options that start with this prefix are passed to the Java compiler. For example:

      compile.verbose
      compile.bootclasspath=/usr/local/packages/jdk6/jre/lib/rt.jar

- General profile customization options, which apply regardless of the particular customizer you are using, are prefixed by `profile.` (including the period) instead of `-P-`. Only options that start with this prefix are passed to the profile customizer. For example:

      profile.backup
      profile.user=HR/hr

  You can also specify options to a particular customizer by using `profile.C` as follows:

      profile.Csummary
      profile.Coptparamdefaults=VAR%(50),LONG%(500),RAW_TYPE()

  Any profile customization other than the default Oracle customization is considered an advanced feature.

  **See Also:**

  [Customization and Specialized Customizers](appendix.md)

- Comment lines start with a pound sign (`#`). For example:

      # Comment line.

- Blank lines are also permitted.

As on the command line, a flag can be enabled or disabled in a properties file with `true`/`false`, `on`/`off`, `1`/`0`, or `yes`/`no`. A flag can also be enabled simply by entering it without a setting, such as the following:

    sqlj.linemap

**Note:**

For consistency, it is best to always use the equal sign (=) in a properties file for options that take values, even though there are some circumstances where a space also works.

##### Properties File: Simple Example

The following are sample properties file entries:

    # Set user and JDBC driver
    sqlj.user=HR
    sqlj.driver=oracle.jdbc.OracleDriver

    # Turn on the compiler verbose option
    compile.verbose

These entries are equivalent to having the following on the SQLJ command line:

    % sqlj -user=HR -driver=oracle.jdbc.OracleDriver -C-verbose

##### Properties File: Nondefault Connection Context Classes

Following is a sample properties file that specifies settings for a connection context class, `SourceContext`, that you declared:

    # JDBC driver
    sqlj.driver=oracle.jdbc.OracleDriver

    # Oracle 9.2 on spock.natdecsys.com
    sqlj.user@SourceContext=sde
    sqlj.password@SourceContext=fornow
    sqlj.url@SourceContext=jdbc:oracle:thin:@localhost:5221/myservice

    # Warning settings
    sqlj.warn=all

    # Cache
    sqlj.cache=on

##### Default Properties Files

Regardless of whether a properties file is specified on the SQLJ command line, the SQLJ front end looks for files named `sqlj.properties`. It looks for them in the Java home directory, the user home directory, and the current directory, in that order. It processes each `sqlj.properties` file it finds, overriding previously set options as it encounters new ones. Thus, options set in the `sqlj.properties` file in the current directory override those set in the `sqlj.properties` file in the user home directory or Java home directory.

**See Also:**

"Order of Precedence of Option Settings"

#### 9.1.4 SQLJ_OPTIONS Environment Variable for Option Settings

The Oracle SQLJ implementation supports an environment variable called `SQLJ_OPTIONS` as an alternative to the command line for setting SQLJ options. Any option referred to as command line only, meaning it cannot be set in a properties file, can also be set using the `SQLJ_OPTIONS` variable.

You can use the `SQLJ_OPTIONS` variable to set any SQLJ option, but it is intended especially for option settings to be passed to the JVM. And it is particularly useful for command-line-only options, such as `-classpath`, that you use repeatedly with the same setting.

Following is an example of a `SQLJ_OPTIONS` setting:

    -vm=jview -J-verbose

When you use `SQLJ_OPTIONS`, SQLJ effectively inserts the `SQLJ_OPTIONS` settings, in order, at the beginning of the SQLJ command line, prior to any other command-line option settings.

**Note:**

Generally, syntax in `SQLJ_OPTIONS` is the same as on the command line, but this may depend on your operating system. There can be operating system specific restrictions. For example, on Microsoft Windows 95 you use the `Environment` tab in the `System` control panel. Additionally, because Windows 95 does not support the equal sign (=) in variable settings, SQLJ supports the use of `#` instead of `=` in setting `SQLJ_OPTIONS`. Refer to your operating system documentation.

#### 9.1.5 Order of Precedence of Option Settings

SQLJ takes option settings in the following order:

1.  Sets options to default settings, where applicable.

2.  Looks for a `sqlj.properties` file in the Java home directory. If it finds one, it sets options as specified there.

3.  Looks for a `sqlj.properties` file in the user home directory. If it finds one, it sets options as specified there.

4.  Looks for a `sqlj.properties` file in the current directory. If it finds one, it sets options as specified there.

5.  It looks for option settings in the `SQLJ_OPTIONS` environment variable and effectively prepends them to the beginning of the command line. It sets options as specified in `SQLJ_OPTIONS`.

6.  It looks for option settings on the command line and sets options as specified there. As SQLJ processes the command line, it looks in any file specified by the `-props` option and sets options as specified there.

**Note:**

- At each step, SQLJ overrides any previous settings for any given option.

- In the `sqlj.properties` files, SQLJ reads option settings from top to bottom, with later entries taking precedence over earlier entries.

- If there is a properties file specified by the `-props` option on the command line, SQLJ effectively inserts the option settings of the file into the position on the command line where the `-props` option was specified.

- SQLJ reads options on the command line, with options from a `-props` file inserted, in order from left to right. Any later (right-hand) setting takes precedence over earlier (left-hand) settings.

##### Example

Presume SQLJ is run as follows:

    % sqlj -user=HR -props=myprops.properties -dir=/home/java

And presume the file `myprops.properties` is in the current directory and contains the following entries:

    sqlj.user=tony
    sqlj.dir=/home/myjava

These settings are processed as if they were inserted into the command line where the `-props` option was specified. Therefore, the `tony` entry takes precedence over the `HR` entry for the `user` option, but the `/home/java` entry takes precedence over the `/home/myjava` entry for the `dir` option.

### 9.2 Basic Translator Options

This section documents the syntax and functionality of the basic flags and options you can specify in running SQLJ. These options enable you to run in a fairly standard mode of operation. For options that can also be specified in a properties file, that syntax is noted as well.

This section covers the following topics:

- Basic Options for the Command Line Only

- Options for Output Files and Directories

- Connection Options

- Options for Reporting and Line-Mapping

- Options for DMS

- Options for Code Generation\_ Optimizations\_ and CHAR Comparisons

**See Also:**

- "Properties Files for Option Settings"

- "Advanced Translator Options"

- "Translator Support and Options for Alternative Environments"

#### 9.2.1 Basic Options for the Command Line Only

The following basic options can be specified only on the SQLJ command line or, equivalently, in the `SQLJ_OPTIONS` environment variable:

- `-props`

- `-classpath`

- `-help`, `-help-long`, `-help-alias`, `-P-help`, `-C-help`

- `-version`, `-version-long`

- `-n`

These options cannot be specified in properties files. The command-line-only flags (`-help`, `-version`, and `-n`) do not support `=``true` syntax. Enable them by typing only the flag name, as follows:

    sqlj -version-long

**Note:**

Additionally, there are advanced options, flags, and prefixes that can be set only on the command line or in `SQLJ_OPTIONS`:` -J`, `-passes`, and `-vm`.

##### Input Properties File (-props)

The `-props` option specifies a properties file from which SQLJ can read option settings. The command-line syntax is as follows:

    -props=filename

For example:

    -props=myprops.properties

##### Classpath for Java Virtual Machine and Compiler (-classpath)

For compatibility with the syntax of most JVMs and compilers, SQLJ recognizes the `-classpath` option if it is specified on the command line. In setting this option, you can use either a space, as with most JVMs or compilers, or the equal sign (=), as with other SQLJ options. The following examples (both for a UNIX environment) demonstrate this:

    -classpath .:$ORACLE_HOME/jdbc/lib/ojdbc6.jar:$ORACLE_HOME/sqlj/lib/translator.jar:$ORACLE_HOME/sqlj/lib/runtime12.jar

    -classpath= .:$ORACLE_HOME/jdbc/lib/ojdbc6.jar:$ORACLE_HOME/sqlj/lib/translator.jar:$ORACLE_HOME/sqlj/lib/runtime12.jar

The `-classpath` option sets the Java classpath for both the JVM and the Java compiler. If you do not want to use the same classpath for both, then set them separately using the SQLJ `-J` and `-C` prefixes.

**See Also:**

"Prefixes that Pass Option Settings to Other Executables"

**Note:**

As with other options described in this chapter, if you use `=` in setting the `-classpath` option, then it is stripped out when the option string is passed to the JVM and compiler, because JVMs and compilers do not support the `=` syntax in their option settings.

The command-line syntax is as follows

    sqlj -classpath=class_path

For example:

    sqlj -classpath=$ORACLE_HOME/jdbc/lib/ojdbc6.jar:$ORACLE_HOME/sqlj/lib/translator.jar:$ORACLE_HOME/sqlj/lib/runtime12.jar

##### SQLJ Option Information (-help)

The following settings of the `-help` flag, specified on the command line, instruct SQLJ to display varying levels of information about SQLJ options:

- `-help`

- `-help-long`

- `-help-alias`

You can enable this option by typing the desired setting on the command line as in the following examples:

    % sqlj -help

    % sqlj -help-long

    % sqlj -help-alias

No input-file translation is performed when you use the `-help` flag in any of these forms, even if you include file names and other options on the command line as well. SQLJ assumes that you either want to run the translator or you want help, but not both.

You can also receive information about the profile customizer or Java compiler, requesting help through the `-P` and `-C` prefixes, as in the following examples. As with the `-help` flag, no translation is performed if you request customizer or compiler help.

    % sqlj -P-help

    % sqlj -C-help

As with other command-line-only flags, `-help` (as well as `-P-help` and `-C-help`) does not support `=true` syntax. Enable it by typing only the desired flag setting.

**Note:**

- For compatibility with the `loadjava` utility, `-h` is recognized as equivalent to `-help` when specified on the command line.

- You can use multiple `-help` flag settings on the same command line, including `-P-help` and `-C-help`.

- Although `-P` and `-C` settings can generally be set in properties files, `-P-help` and `-C-help` are for only the command line.

- Help is also provided if you run SQLJ without specifying any files to process. This is equivalent to using the `-help` setting.

The most basic level of help is achieved by specifying the `-help` setting. This provides the following:

- A synopsis of the most frequently used SQLJ options

- A listing of the additional `-help` flag settings available

The `-help-long` setting provides a complete list of SQLJ option information, including the following for each option:

- Option name

- Option type (the Java type that the option takes as input, such as `int` or `String`)

- Description

- Current value

- How the current value was set (from the command line, from a properties file, or by default)

**Note:**

It is often useful to include other option settings on the command line with a `-help-long` option, especially with complex options, such as `-warn`, or combinations of options, so that you can see what option settings resulted from your actions.

The `-help-alias` setting provides a synopsis of the command-line abbreviations supported for compatibility with the `loadjava` utility.

The command-line syntax is as follows:

    sqlj help_flag_settings

For example:

    sqlj -help
    sqlj -help -help-alias
    sqlj -help-long
    sqlj -warn=none,null -help-long
    sqlj -help-alias

By default, these settings are disabled.

##### SQLJ Version Number (-version)

The following settings of the `-version` flag, specified on the command line, instruct SQLJ to display varying levels of information about SQLJ and JDBC driver versions:

- `-version`

- `-version-long`

You can enable this option by typing the desired setting on the command line as in the following examples:

    % sqlj -version

    % sqlj -version-long

No input-file translation is performed when you use the `-version` option, even if you include file names and other options on the command line. SQLJ assumes that you either want to run the translator or you want version information, but not both. Properties files and anything else you type on the command line are ignored. As with other command-line-only flags, `-version` does not support the `=true` syntax. Enable it by typing only the flag name.

The `-version` setting displays the SQLJ release number, as follows:

    sqlj -version
    Oracle SQLJ Release 12.1.0.1.0 Production
    Copyright © 1997, 2012, Oracle Corporation. All Rights Reserved.

The `-version-long` setting displays information about the SQLJ and SQLJ run-time library release, the JDBC driver release number if one can be found, and the Java environment. For example, if an Oracle JDBC driver is used, this option would display something as follows:

    sqlj -version-long
    Oracle SQLJ Release 12.1.0.1.0 Production
    Copyright © 1997, 2012, Oracle Corporation. All Rights Reserved.
    JDBC version: Oracle JDBC driver version 12.1 (12.1.0.1.0)
    Java version: 1.6 (1.6.0_04)

This flag offers a good way to check your SQLJ installation and the JDBC and JDK versions you are using. The command-line syntax is as follows:

    sqlj version_flag_settings

For example:

    sqlj -version
    sqlj -version -version-long
    sqlj -version-long

By default, these settings are disabled.

##### Command Line Echo without Execution (-n)

The `-n` flag, specified on the command line, instructs the `sqlj` script to construct the full command line that would be passed to the SQLJ translator, including any `SQLJ_OPTIONS` settings, and echo it to the user without having the SQLJ translator execute it. This includes capturing and echoing the name of the JVM that would be launched to execute the SQLJ translator and echoing the full class name of the translator. This does not include settings from properties files.

This is useful in displaying the following:

- The fully expanded form of any options you abbreviated, such as `-u` and other abbreviations supported for `loadjava` compatibility.

- The order in which options would be placed when the overall command string is constructed and passed to the translator.

- Possible conflicts between `SQLJ_OPTIONS` settings and command-line settings.

The `-n` option can appear anywhere on the command line or in the `SQLJ_OPTIONS` variable. As with other command-line-only flags, `-n` does not support the `=true` syntax. Enable it by typing only the flag name.

Consider a sample scenario. You have the following setting for `SQLJ_OPTIONS`:

    -user=HR/hr@jdbc:oracle:thin:@ -classpath=/myclasses/bin

You enter the following command line:

    % sqlj -n -e SJIS myapp.sqlj

You would see the following echo:

    java -classpath /myclasses/bin sqlj.tools.Sqlj -user=HR/hr@jdbc:oracle:thin:@ -C-classpath=/myclasses/bin
    -encoding=SJIS myapp.sqlj

Note that this is all one wraparound line.

**Note:**

- Echoing your password at the command-line is not a secure practice.

- As an alternative to `-n`, you can use the `-vm`=`echo` setting.

- Another effective way to check option settings is to use the `-help-long` flag. This displays current settings for all options, including other options you set on the command line as well as settings in properties files and in `SQLJ_OPTIONS`.

The command-line syntax is as follows:

    -n

For example:

    -n

By default, this setting is disabled.

#### 9.2.2 Options for Output Files and Directories

The `-encoding` option specifies encoding for SQLJ input and output source files. The following options specify where SQLJ output files are placed:

- `-d`

- `-dir`

##### Encoding for Input and Output Source Files (-encoding)

The `-encoding` option specifies the encoding to be applied to `.sqlj` and `.java` input files and `.java` generated files for globalization support. For compatibility with `javac`, you can use either a space or equal sign (=) in setting this option on the command line, as in the following examples:

    -encoding=SJIS

    -encoding SJIS

However, if setting `sqlj.encoding` in a properties file, then use `=`, not a space.

When this option is specified, it is also passed to the Java compiler, unless the `-compiler-encoding-flag` is off, which uses it to specify encoding for `.java` files processed by the compiler.

Note the following:

- As with the `-classpath` and `-d` options, if you do use an `=` in setting the `-encoding` option, then it is stripped out when the option string is passed to the JVM and compiler. This is because JVMs and compilers do not support the `=` syntax in their option settings.

- For compatibility with the `loadjava` utility, `-e` is recognized as equivalent to `-encoding` when specified on the command line.

- The `-encoding` option does not apply to Java properties files, such as `sqlj.properties` and `connect.properties`. Properties files always use the encoding `8859_1`. This is a feature of Java in general, not SQLJ in particular. However, you can use Unicode escape sequences in a properties file. You can use the `native2ascii` utility to create escape sequences for a natively encoded file.

  **See Also:**

  [Translator and Run-Time Functionality](translator-run-time-functionality.md)

The command-line syntax is as follows:

    -encoding=Java_character_encoding

For example:

    -encoding=SJIS

The syntax for a properties file entry for this option is as follows:

    sqlj.encoding=Java_character_encoding

For example

    sqlj.encoding=SJIS

By default, this option is set to the JVM system property `file.encoding`.

##### Output Directory for Generated .ser and .class Files (-d)

The `-d` option specifies the root output directory for profiles generated by the SQLJ translator (relevant for ISO standard code generation, `-codegen`=`iso`), and is also passed to the Java compiler to specify the root output directory for `.class` files generated by the compiler. Whether profiles are generated as `.ser` files (default) or `.class` files (if the `-ser2class` option is enabled) is irrelevant for placement through the `-d` option.

Whenever a directory is specified, the output files are generated under this directory according to the package name, if applicable. For example, if you have source files in the `a.b.c` package and specify directory, `/mydir`, output files will be placed in the `/mydir/a/b/c` directory. If you specify a relative directory path, then this will be from your current directory.

For compatibility with `javac`, you can use either a space or `=` in setting this option on the command line, as in the following examples (both of which make `/root` the root directory for generated profile files):

    -d=/root

    -d /root

However, if setting `-d` in a properties file, then use `=`, not a space. For example:

    sqlj.d=/root

If your current directory is `/root/home/mydir` and you set the `-d` option to the relative directory path, `mysubdir/myothersubdir`, as follows, then `/root/home/mydir/mysubdir/myothersubdir` will be the root directory for the generated profile files:

    -d=mysubdir/myothersubdir

You can also use standard syntax, such as a period for the current directory or two periods to go up a level, as follows:

    -d=.

    -d=../paralleldir

If the `-d` option is empty or not specified, then a generated `.class` file is placed in the same directory as the corresponding `.java` file, which is according to the `-dir` option for a `.java` file generated by SQLJ, and a generated `.ser` file is placed in the same directory as the corresponding `.sqlj` file.

**Note:**

- You can specifically set `-d` to be empty (to override settings in a properties file, for example) as follows:

      -d=

- Throughout this discussion, slash (/) was used as the file separator. However, it is important to note that in specifying this, or similar options, you must actually use the file separator of your operating system, as specified in the `file.separator` system property of your JVM.

- As with the `-classpath` and `-encoding` options, if you do use an equal sign (=) in setting the `-d` option, then it is stripped out when the option string is passed to the JVM and compiler. This is because JVMs and compilers do not support the `=` syntax in their option settings.

The command-line syntax is as follows:

    -d=directory_path

For example:

    -d=/topleveldir/mydir

The syntax for a properties file entry for this option is as follows:

    sqlj.d=directory_path

For example:

    sqlj.d=/topleveldir/mydir

This option does not have any default value.

##### Output Directory for Generated .java Files (-dir)

The `-dir` option specifies the root directory for `.java` files generated by the SQLJ translator. Whenever a directory is specified, the output files are generated under this directory according to the package name, if applicable. For example, if you have source files in the `a.b.c` package and specify directory, `/mydir`, then output files will be placed in the `/mydir/a/b/c` directory. If you specify a relative directory path, then it will be from your current directory.

A simple example is as follows, which will make `/root` the root directory for generated `.java` files:

    -dir=/root

Consider that your current directory is `/root/home/mydir` and you set the `-dir` option to the relative directory path `mysubdir/myothersubdir` as follows:

    -dir=mysubdir/myothersubdir

Then `/root/home/mydir/mysubdir/myothersubdir` will be the root directory for generated `.java` files.

You can also use standard syntax, such as a period for the current directory or two periods to go up a level, as follows:

    -dir=.

    -dir=../paralleldir

If the `-dir` option is not specified, then files are generated under the same directory as the original `.sqlj` source file (not under the current directory). If you specifically want the output directory to be the same as your `.sqlj `source directory (perhaps overriding other `-dir` settings, such as in properties files), then you can use the `-dir` option as follows:

    -dir=

**Note:**

If you specify the `-dir` option but not the `-d` option, then generated `.class` files will also be placed in the directory specified by `-dir`, but generated `.ser` files will be placed in the directory of the `.sqlj` file.

The command-line syntax is as follows:

    -dir=directory_path

For example:

    -dir=/topleveldir/mydir

The syntax for a properties file entry for this option is as follows:

    sqlj.dir=directory_path

For example:

    sqlj.dir=/topleveldir/mydir

This option does not have any default value.

#### 9.2.3 Connection Options

You can use the following options for the database connection for online semantics-checking:

- `-user`

- `-password`

- `-url`

- `-default-url-prefix`

- `-driver`

- `driver_name`

There is no requirement for the SQLJ translator to connect to the same database or schema as the application does at run time. The connection information in application source code can be independent of the connection information in the SQLJ options. In fact, the deployment environment might be unavailable during development and testing.

##### Online Semantics-Checking and User Name (-user)

Simple semantics-checking not involving a database connection is referred to as offline checking. The more thorough semantics-checking requiring a connection is referred to as online checking. Online checking offers one of the prime advantages of the SQLJ strong-typing paradigm, namely that type incompatibilities that would usually result in run-time SQL exceptions are caught during translation, before users ever run the application.

The `-user` option enables online semantics-checking and specifies the user name (schema name) for the exemplar schema, which is the sample database schema that you provide to the translator for it to use in performing the checking. You can also use the `-user` option to specify the password and URL, as opposed to using the `-password` and `-url` options separately.

Note that there is no other flag to enable or disable online semantics-checking. SQLJ enables or disables it according to the presence or absence of the `-user` option.

**Note:**

- Some settings of the SQLJ `-parse` option will disable online semantics-checking, overriding the effect of the `-user` option.

- For compatibility with the `loadjava` utility, `-u` is recognized as equivalent to `-user` when specified on the command line.

- User names cannot contain the characters `/` or `@`.

- You are allowed to use a space instead of `=` in a user name setting on the command line, as in the following examples:

      -user HR/password
      -user@CtxClass HR/password
      -u HR/password
      -u@CtxClass HR/password

- If a password contains the character `@`, then you cannot set the password through the `-user` option. You must use separate `-user` and `-password` settings.

- If your login name is a member of the `DBA` group, you may have special privilege to connect as `SYSDBA` to the `SYS` schema. In this case, you can specify the user name `SYS` or `INTERNAL`.

- For ISO code generation, the translator `-user` setting is forwarded to the profile customizer, but can be overridden by the customizer `user` setting.

The most basic usage of the `-user` option is as follows:

    -user=HR

When you are using only the default connection or other instances of the `DefaultContext` class, such a setting will apply to all your SQLJ executable statements. This example results in online checking against the `HR` schema.

You can also specify the password, URL, or both along with the user name, using syntax as in the following examples (with `/` preceding the password and `@` preceding the URL):

    -user=HR/password

    -user=HR@jdbc:oracle:oci:@

    -user=HR/password@jdbc:oracle:oci:@

Otherwise, the URL can be specified through the `-url` option, and the password can be specified interactively or through the `-password` option.

You can disable online semantics-checking by setting the `-user` option to an empty string, as follows:

    -user=

Again, when you are using only the default connection or other instances of the `DefaultContext` class, this will apply to all your SQLJ executable statements.

Disabling online semantics-checking is useful, for example, if you have online checking enabled in a properties file, but want to override that on the command line, or have it enabled in the default properties file but want to override that in a user-specified properties file, specified using the `-props` option.

There is also a special user name, `URL.CONNECT`, which you can use when the URL specifies the user and password as well as the other details of the connection.

If you declare and use additional connection context classes in your application, then you can specify `-user` settings for the testing of SQLJ executable statements that use instances of those classes. Specify a user name for online checking against a particular connection context class, for example, `CtxClass`, as follows:

    -user@CtxClass=HR

This results in online checking against the `HR` schema for any of your SQLJ executable statements that specify a connection context instance of `CtxClass`.

As with the default connection context class, you can also specify the password or URL in your -`user` setting for a particular connection context class, as in the following example:

    -user@CtxClass=HR/password@jdbc:oracle:oci:@

The `CtxClass` connection context class must be declared in your source code or previously compiled into a `.class` file.

Use the -`user` option separately for each connection context class for which you want to enable online checking and set a user name. These settings have no influence on each other. For example:

    -user@CtxClass1=user1 -user@CtxClass2=user2 -user@CtxClass3=user3

When you are using multiple connection context classes in your application, a -`user` setting that does not specify a class will apply to the `DefaultContext` class as well as to all classes for which you do not otherwise specify a -`user` setting. Presumably, though, you will specify a -`user` setting for each connection context class, given that different connection context classes are typically intended for use with different sets of SQL objects.

Consider a situation where you have declared connection context classes `CtxClass1`, `CtxClass2`, and `CtxClass3` and you set -`user` as follows:

    -user@CtxClass2=HR/password -user=bill/lion

Any statement in your application that uses an instance of `CtxClass2` will be checked against the `HR` schema. Any statement that uses an instance of `DefaultContext`, `CtxClass1`, or `CtxClass3` will be checked against the `bill` schema.

In addition, once you enable online checking by setting the -`user` option, you can disable online checking for a particular connection context by setting the -`user` option again with an empty user name for that connection context. For example, consider the following setting:

    -user@CtxClass2=

This disables online semantics-checking for any SQLJ executable statements that specify a connection object that is an instance of `CtxClass2`.

You can disable online semantics-checking for the default connection context class and any other connection context classes for which you do not specify a user name as follows:

    -user=

The general command-line syntax for this option is as follows:

    -user<@conn_context_class>=username</password><@url>

For example:

    -user=HR
    -user=HR/password
    -user=HR@jdbc:oracle:oci:@
    -user=HR/password@jdbc:oracle:oci:@
    -user=
    -user=URL.CONNECT
    -user@CtxClass=HR/password
    -user@CtxClass=

The syntax for a properties file entry for this option is as follows:

    sqlj.user<@conn _context_class>=username</password><@url>

For example:

    sqlj.user=HR
    sqlj.user=HR/password
    sqlj.user=HR@jdbc:oracle:oci:@
    sqlj.user=HR/password@jdbc:oracle:oci:@
    sqlj.user=
    sqlj.user=URL.CONNECT
    sqlj.user@CtxClass=HR/password
    sqlj.user@CtxClass=

This option does not have a default value. By default, there is no online-semantics checking.

**Note:**

Be aware of the difference in format between specifying user, password, and URL in the `user` option and specifying them in the -`url` option. In the -`url` option, the user name and password are included in the URL, immediately following the JDBC driver type. In the -`user` option they precede the URL.

##### User Password for Online Semantics-Checking (-password)

The -`password` option specifies the user password for the database connection for online semantics-checking. For the -`password` setting to be meaningful, the -`user` option must also be set.

You can also specify the password as part of the -`user` option setting. Do not use the -`password` option for a connection context class if you have already set its password in the -`user` option, which takes precedence.

For the most part, functionality of the `-password` option parallels that of the `-user` option. That is, if your application uses only the default connection or other instances of `DefaultContext`, then the following will set the password for the schema to be used in checking all of your SQLJ statements:

    -password=password

If you declare and use additional connection context classes, `CtxClass1` for example, then you will presumably use the -`user` option to specify additional exemplar schemas to use in testing statements that use those connection context classes. Similarly, use the -`password` option to specify passwords for those schemas, as in the following example:

    -password@CtxClass1=password

A connection context class without a password setting, either through the -`password` setting or the -`user` setting, uses the password setting for the default connection context class. If you set no password for the default connection context class, then SQLJ prompts you interactively for that password. If you also set no password for a user-defined connection context class, then SQLJ prompts you interactively for that password as well. An exception to this discussion is where user name `URL.CONNECT` is used. In this case, user name and password are determined from the string specified in the -`url` setting and any setting of the -`password` option is ignored.

You can specifically set an empty password to override other settings of the -`password` option, such as in a properties file, and be prompted interactively. You can do this for the `DefaultContext` class or any particular connection context class, as in the following examples:

    -password=

    -password@CtxClass1=

If you actually want to use an empty password to log in, specify `EMPTY.PASSWORD` as in the following examples:

    -password=EMPTY.PASSWORD

    -password@CtxClass2=EMPTY.PASSWORD

However, Oracle Database 12c Release 1 (12.1) does not permit an empty password.

**Note:**

- When specified on the command line, -`p` is recognized as equivalent to -`password`.

- You are allowed to use a space instead of `=` in a password setting on the command line, as in the following examples:

      -password password
      -password@CtxClass password
      -p password
      -p@CtxClass password

- For ISO code generation, the translator -`password` setting is forwarded to the profile customizer, but can be overridden by the customizer `password` setting.

The command-line syntax for this option is as follows:

    -password<@conn_context_class>=user_password

For example:

    -password=password
    -password=
    -password=EMPTY.PASSWORD
    -password@CtxClass=password

The syntax for a properties file entry for this option is as follows:

    sqlj.password<@conn_context_class>=user_password

For example:

    sqlj.password=hr
    sqlj.password=
    sqlj.password=EMPTY.PASSWORD
    sqlj.password@CtxClass=hr

This option does not have a default value. Either the password for `DefaultContext` is used or the user is prompted.

##### Connection URL for Online Semantics-Checking (-url)

The -`url` option specifies a URL for establishing a database connection for online semantics-checking. As necessary, the URL can include a host name, port number, and database service name (or SID, which is deprecated in Oracle Database 12c Release 1 (12.1)).

You can also specify the URL as part of the -`user` option setting. Do not use the -`url` option for a connection context class if you have already set its URL in the -`user` option, which takes precedence.

For the most part, functionality of the -`url` option parallels that of the -`user` option. That is, if your application uses only the default connection or other instances of `DefaultContext`, then the following example would set the URL to use for the connection for checking all your SQLJ statements:

    -url=jdbc:oracle:oci:@

Alternatively, to include the host name, port number, and service name:

    -url=jdbc:oracle:thin:@myhost:5221/myservice

If you do not begin a URL setting with `jdbc:`, then the setting is assumed to be of the form `host``:``port``/``servicename` and, by default, is automatically prefixed with the following:

    jdbc:oracle:thin:@

A -`url` setting of `localhost:5221/myservice` would result in the following URL:

    jdbc:oracle:thin:@localhost:5221/myservice

You can remove or alter this default prefix with the -`default`-`url`-`prefix` option.

You can specify the user and password in the `-url` setting, instead of in the -`user` and -`password` settings. In such a case, set -`user` to `URL.CONNECT`, as follows:

    -url=jdbc:oracle:oci:HR/hr@ -user=URL.CONNECT

If you declare and use additional connection context classes, `CtxClass1` for example, you will presumably specify additional exemplar schemas to use in testing statements that use those connection context classes. You can use the -`url` option to specify URLs for those schemas, as in the following example:

    -url@CtxClass1=jdbc:oracle:oci:@

Any connection context class without a URL setting, either through the -`url` setting or the -`user` setting, uses the URL setting for the default connection context class, presuming a URL has been set for the default context class.

**Note:**

- Remember that any connection context class with a URL setting must also have a user name setting for online checking to occur.

- You are allowed to use a space instead of `=` in a URL setting on the command line, as in the following examples:

      -url jdbc:oracle:oci:@
      -url@CtxClass jdbc:oracle:oci:@

- For ISO code generation, the translator -`url` setting is forwarded to the profile customizer, but can be overridden by the customizer `url` setting.

The command-line syntax for this option is as follows:

    -url<@conn_context_class>=URL

For example:

    -url=jdbc:oracle:oci:@
    -url=jdbc:oracle:thin:@hostname:5221/myservice
    -url=jdbc:oracle:oci:HR/password@
    -url=hostname:5221/myservice
    -url@CtxClass=jdbc:oracle:oci:@

The syntax for a properties file entry for this option is as follows:

    sqlj.url<@conn_context_class>=URL

For example:

    sqlj.url=jdbc:oracle:oci:@
    sqlj.url=jdbc:oracle:thin:@hostname:5221/myservice
    sqlj.url=jdbc:oracle:oci:HR/hr@
    sqlj.url=hostname:5221/myservice
    sqlj.url@CtxClass=jdbc:oracle:oci:@

The default value for this option is:

    jdbc:oracle:oci:@

**Note:**

Be aware of the difference in format between specifying user, password, and URL in the -`user` option and specifying them in the -`url` option. In the -`url` option, the user name and password are included in the URL, immediately following the JDBC driver type. In the -`user` option, they precede the URL.

##### Default URL Prefix (-default-url-prefix)

Use the -`default-url-prefix` option to alter or remove the default prefix. The following is the default prefix for any URL setting you specify that does not already start with `jdbc:`

    jdbc:oracle:thin:@

This enables you to use a shorthand in specifying a URL setting, either in the -`user` option or the `-url` option. It is permissible to specify only the host, port, and service name (or SID, which is deprecated) of the database. As an example, presume you set a URL as follows:

    -url=myhost:5221/myservice

    -user=HR/hr@myhost:5221/myservice

By default, the URL will be interpreted to be the following:

    jdbc:oracle:thin:@myhost:5221/myservice

If you specify a full URL that starts with `jdbc:`, then the default prefix will not be used.

However, if you want your URL settings to default to the JDBC Oracle Call Interface (OCI) driver, for example, instead of the JDBC Thin driver, then set the default prefix as follows:

    -default-url-prefix=jdbc:oracle:oci:@

If you do not want any prefix, then set the -`default`-`url-prefix` option to an empty string, as follows:

    -default-url-prefix=

The command-line syntax for this option is as follows:

    -default-url-prefix=url_prefix

For example

    -default-url-prefix=jdbc:oracle:oci:@
    -default-url-prefix=

The syntax for a properties file entry for this option is as follows:

    sqlj.default-url-prefix=url_prefix

For example:

    sqlj.default-url-prefix=jdbc:oracle:oci:@
    sqlj.default-url-prefix=

The default value for this option is:

    jdbc:oracle:thin:@

##### JDBC Drivers to Register for Online Semantics-Checking (-driver)

The `-driver` option specifies the JDBC driver class to register for interpreting JDBC connection URLs for online semantics-checking. Use this option to specify a driver class or comma-delimited list of classes. The default, `OracleDriver`, supports Oracle JDBC OCI, JDBC Thin, and server-side JDBC drivers for use with Oracle Database 12c Release 1 (12.1).

The command-line syntax for this option is as follows:

    -driver=driver1<,driver2,driver3,...>

For example:

    -driver=oracle.jdbc.OracleDriver
    -driver=oracle.jdbc.OracleDriver,sun.jdbc.odbc.JdbcOdbcDriver

The syntax for a properties file entry for this option is as follows:

    sqlj.driver=driver1<,driver2,driver3,...>

For example:

    sqlj.driver=oracle.jdbc.OracleDriver
    sqlj.driver=oracle.jdbc.OracleDriver,sun.jdbc.odbc.JdbcOdbcDriver

The default value for this option is:

    oracle.jdbc.OracleDriver

##### Driver Name (sqlj.driver_name)

Use the `sqlj.driver_name` option in the properties file to set the driver name. You can set the `driver_name` attribute for end-to-end diagnosis. The value of this attribute is not validated. This value is passed directly to the server and is displayed as the value of the `CLIENT_DRIVER` column of the `V$SESSION_CONNECT_INFO` view and the `GV$SESSION_CONNECT_INFO` view. The maximum length of this value is 8 characters.

If you do not set this property in the properties file, then the default value for this property is "SQLJ". You can set this property in the following way:

    sqlj.driver_name=MYDRIVER

**Note:**

This attribute can be set only through the properties file and does not have an equivalent command-line option.

#### 9.2.4 Options for Reporting and Line-Mapping

The following options specify what types of conditions SQLJ should monitor, whether to generate real-time error and status messages and whether to include cause and action information with translator error messages:

- `-warn`

- `-status`

- `-explain`

The following options enable line-mapping from the generated Java `.class` file back to the `.sqlj` source file, so that you can trace run-time errors back to the appropriate location in your original source code:

- `-linemap`

- `-jdblinemap`

Use `-jdblinemap` in conjunction with the Sun Microsystems `jdb` debugger. Otherwise, use `-linemap`.

##### Translator Warnings (-warn)

There are various warnings and informational messages that the SQLJ translator can display as dictated by conditions it encounters during the translation. The `-warn` option consists of a set of flags that specify which of those warnings and messages should be displayed, in other words, which conditions should be monitored and which should be ignored. All the flags for thisoption must be combined into a single, comma-delimited string.

Table 9-3 lists the conditions that can be tested, what the `true` and `false` flag values are for each condition, what a `true` flag value means, and which value is the default.

Table 9-3 Tests and Flags for SQLJ Warnings

| Test and Flag Functions                                                                                                                                                                                                                                                                                                                                                                                                                                     | TRUE/FALSE Values                      |
|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------|
| Test for requirement of subtypes of declared object type in an inheritance hierarchy: Enable `cast` to receive warnings when usage of SQL object types in a SQL inheritance hierarchy requires that subtypes of a declared type must be passed at run time.                                                                                                                                                                                                 | `cast` (default)<br>`nocast`           |
| Data precision test: Enable `precision` to receive warnings if there was a possible loss of precision when moving values from database columns to Java host variables.                                                                                                                                                                                                                                                                                      | `precision` (default)<br>`noprecision` |
| Conversion loss test for nullable data: Enable `nulls` to receive warnings if there was possible conversion loss when moving nullable columns or nullable Java types from database columns to Java host variables.                                                                                                                                                                                                                                          | `nulls` (default)<br>`nonulls`         |
| Portability test: Enable `portable` to check SQLJ clauses for portability and receive warnings if there are nonportable clauses. (Where nonportable refers to the use of extensions to the SQLJ standard, such as vendor-specific types or features.)                                                                                                                                                                                                       | `portable`<br>`noportable` (default)   |
| Strict matching test for named iterators: Enable `strict` to instruct SQLJ to require that the number of columns selected from the database must equal the number of columns in the named iterator being populated. A warning is issued for any column in the database cursor for which there is no corresponding column in the iterator. The `nostrict` setting allows more (but not fewer) columns in the database cursor. Unmatched columns are ignored. | `strict` (default)<br>`nostrict`       |
| Translation-time informational messages: Enable `verbose` to provide additional informational messages about the translation process, such as what database connections were made for online checking.                                                                                                                                                                                                                                                      | `verbose`<br>`noverbose` (default)     |
| Global enabling or disabling of warnings: Use `all` or `none` to enable or disable all warnings.                                                                                                                                                                                                                                                                                                                                                            | `all`<br>`none`                        |

The `verbose/noverbose` flag works differently from the others. It does not enable a particular test but enables output of general informational messages about the semantics-checking.

**Note:**

Do not confuse `-warn``=``verbose` with the `-status` flag. The `-status` flag provides real-time informational messages about all aspects of SQLJ translation: translation, semantics-checking, compilation, and profile customization, if applicable. The `-warn``=``verbose` flag results in additional reporting about the translation phase only.

The global `all`/`none` flag takes priority over default settings. You can use it to enable or disable all flags, or to serve as an initialization to ensure that all flags are off before you turn selected flags on, or all flags are on before you turn selected flags off.

The `all` setting is equivalent to the following:

    cast,precision,nulls,portable,strict,verbose

And the `none` setting is equivalent to the following:

    nocast,noprecision,nonulls,noportable,nostrict,noverbose

There is no default for `all`/`none`. There are only defaults for individual flags.

Following are some examples:

- Use the following sequence to ensure that only the `nulls` flag is on:

      -warn=none,nulls

- The following sequence will have the same result, because the `verbose` setting will be overridden:

      -warn=verbose,none,nulls

- Use the following to ensure that everything except the portability flag is on:

      -warn=all,noportable

- This sequence will have the same result, because the `nonulls` setting will be overridden:

      -warn=nonulls,all,noportable

Other than placement of the `all`/`none` flag, the order in which flags appear in a `-warn` setting is unimportant, except in the case of conflicting settings. If there are conflicts, such as in `-warn``=``portable,noportable`, then the last (right-most) setting is used.

Separate settings of the `-warn` option in properties files and on the command line are not cumulative. Only the last setting is processed. In the following example, the `-warn``=``portable` setting is ignored. That flag and all other flags besides `nulls/nonulls` are set according to their defaults:

    -warn=portable -warn=nonulls

**Note:**

The cast, precision, nullability, and strictness tests are part of online semantics-checking and require a database connection.

The command-line syntax for this option is as follows:

    -warn=comma-delimited_list_of_flags

For example:

    -warn=none,nulls,precision

The syntax for a properties file entry for this option is as follows:

    sqlj.warn=comma-delimited_list_of_flags

For example:

    sqlj.warn=none,nulls,precision

The default value for this option is as follows:

    cast,precision,nulls,noportable,strict,noverbose

##### Real-Time Status Messages (-status)

The `-status` flag instructs SQLJ to display additional status messages throughout all aspects of the SQLJ process: translation, semantics-checking, compilation, and customization. Messages are displayed as each file is processed and at each stage of the SQLJ operation.

**Note:**

- Do not confuse `-warn``=``verbose` with the `-status` flag. The `-status` flag provides real-time informational messages about all aspects of SQLJ translation. The `-warn``=``verbose` flag results in additional reporting about the translation phase only.

- For compatibility with the `loadjava` utility, `-v` is recognized as equivalent to `-status` when specified on the command line.

The command-line syntax for this option is as follows:

    -status<=true|false>

For example:

    -status

The syntax for a properties file entry for this option is as follows:

    sqlj.status<=true|false>

For example:

    sqlj.status

The default value for this option is:

    false

##### Cause and Action for Translator Errors (-explain)

The `-explain` flag instructs the SQLJ translator to include cause and action information, as available, with translator error message output for the first occurrence of each error.

The command-line syntax for this option is as follows:

    -explain<=true|false>

For example:

    -explain

The syntax for a properties file entry for this option is as follows:

    sqlj.explain<=true|false>

For example:

    sqlj.explain

The default value for this option is:

    false

##### Line-Mapping to SQLJ Source File (-linemap)

The `-linemap` flag instructs SQLJ to map line numbers from a SQLJ source code file to locations in the corresponding `.class` file. This will be the `.class` file created during compilation of the `.java` file generated by the SQLJ translator. As a result, when Java run-time errors occur, the line number reported by the JVM is the line number in the SQLJ source code, making it much easier to debug.

Usually, the instructions in a `.class` file map to source code lines in the corresponding `.java` file. This would be of limited use to SQLJ developers, though, as they would still need to map line numbers in the generated `.java` file to line numbers in their original `.sqlj` file.

The SQLJ translator modifies the `.class` file to implement the `-linemap` option, replacing line numbers and the file name from the generated `.java` file with corresponding line numbers and the file name from the original `.sqlj` file. This process is known as instrumenting the class file.

In performing this, SQLJ takes the following into account:

- The `-d` option setting, which determines the root directory for `.class` files

- The `-dir` option setting, which determines the root directory for generated `.java` files

**Note:**

- If you are processing a `.sqlj` file and the compilation step is skipped due to error, then no line-mapping can be performed either, because no `.class` file is available for mapping.

- When the Java compiler is invoked from SQLJ, it always reports compilation errors using line numbers of the original `.sqlj` source file, not the generated `.java` file. No option needs to be set for this mapping.

- Anonymous classes in a `.sqlj` file will not be instrumented.

- If you are using the Sun Microsystems `jdb` debugger, then use the `-jdblinemap` option instead of the `-linemap` option.

The command-line syntax for this option is as follows:

    -linemap<=true|false>

For example:

    -linemap

The syntax for a properties file entry for this option is as follows:

    sqlj.linemap<=true|false>

For example:

    sqlj.linemap

The default value for this option is:

    false

##### Line-Mapping to SQLJ Source File for jdb Debugger (-jdblinemap)

This option is equivalent to the `-linemap` option, but you should use it instead of `-linemap` if you are using the Sun Microsystems `jdb` debugger. This is because `jdb` can access only source files with a `.java` file name extension.

With the `-jdblinemap` setting, SQLJ does the following:

- Overwrites the contents of the `.java` file generated by the translator with the contents of the original `.sqlj` file

- Preserves the `.java` file name, instead of the `.sqlj` file name, in the generated `.class` file

In this way, the SQLJ source code is accessible to `jdb`.

The command-line syntax for this option is as follows:

    -jdblinemap<=true|false>

For example:

    -jdblinemap

The syntax for a properties file entry for this option is as follows:

    sqlj.jdblinemap<=true|false>

For example:

    sqlj.jdblinemap

The default value for this option is:

    false

#### 9.2.5 Options for DMS

The Oracle SQLJ implementation provides translator front-end options to support DMS:

- `-instrument`: Enable instrumentation and designate a name for the application (the collective of the components being translated).

- `-components`: Specify the components (packages and classes) to be instrumented.

**See Also:**

"[SQLJ Support for Oracle Performance Monitoring](performance-and-debugging.md)"

##### Instrumentation for DMS (-instrument)

Use the SQLJ `-instrument` option to enable instrumentation and specify an application name. In this context, the term application refers to all the SQLJ and Java components specified for translation in the SQLJ command line.

Possible settings of the `-instrument` option are as follows:

- `application_name`: To enable instrumentation and use the specified application name, optionally prefixed with a package name in the standard Java dot syntax. Use a slash (/), with no spaces, between the package name and the application name.

- `true`: To enable instrumentation and use the default application name, `defaultApp`.

- `false` (default): To disable instrumentation.

If instrumentation is enabled, a SQLJ DMS properties file is created. Its name and location are according to the `-instrument` setting, starting from the current directory, according to the package name and also according to any setting of the SQLJ `-d` option. If no application name is specified, as is the case with the setting `true`, then the properties file is named `sqlmonitor.properties` in the current directory.

As a simple example, a setting of `-instrument``=``myapp` will result in creation of the properties file, `myapp.properties`, in the current directory.

Now consider the following example, for an application name of `stock` and the package `com.acme`:

    % sqlj -instrument=com.acme/stock Stock.sqlj Trading.sqlj

In this case, the properties file `./com/acme/stock.properties` is created.

Now consider the following example:

    % sqlj -instrument=com.acme/stock -d /home Stock.sqlj Trading.sqlj

In this case, because of the `-d` option, the file `/home/com/acme/stock.properties` is created.

You can also set the `-instrument` option in `sqlj.properties` as follows:

    sqlj.instrument=com.acme/stock

**Note:**

A setting of `-instrument` is equivalent to `-instrument``=``true`.

The command-line syntax for this option is as follows:

    -instrument<=true|false|application_name>

For example:

    -instrument=com.acme/stock

The syntax for a properties file entry for this option is as follows:

    sqlj.instrument<=true|false|application_name>

For example:

    sqlj.instrument=com.acme/stock

The default value for this option is:

    false

##### Components to Instrument for DMS (-components)

When instrumentation is enabled through the` -instrument` option, use the `-components` option to specify the components to be instrumented for DMS monitoring. This is a subset of the components being translated, typically most or all of them to allow flexibility in what you can monitor during run time. At run time, instrumented components are monitored according to what is specified in the SQLJ DMS properties file.

**See Also:**

"[SQLJ Run-Time Commands and Properties File Settings for DMS](performance-and-debugging.md)"

Note that any components that are not instrumented during translation cannot be monitored during run time, regardless of what is specified in the properties file.

The `-components` option supports either of the following settings:

- `list_of_components`: A comma-delimited list of packages or classes to instrument

- `all` (default): Specification to instrument all components being translated

For the list of components, you can specify fully qualified class names, using the standard Java dot syntax, or you can specify package names to instrument all classes in the packages.

For example, to instrument the `Stock` and `Trading` classes:

    % sqlj ... -components=com.acme.Stock,com.acme.Trading

Alternatively, here is an equivalent specification in the `sqlj.properties` file:

    sqlj.components=com.acme.Stock,com.acme.Trading

The command-line syntax for this option is as follows:

    -components=all|list_of_components

For example:

    -components=com.acme.Stock,com.acme.Trading

The syntax for a properties file entry for this option is as follows:

    sqlj.components=all|list_of_components

For example:

    sqlj.components=com.acme.Stock,com.acme.Trading

The default value for this option is:

    all

#### 9.2.6 Options for Code Generation, Optimizations, and CHAR Comparisons

By default, the Oracle SQLJ implementation uses Oracle-specific code generation, which generates Oracle JDBC code directly, as an alternative to ISO standard code generation. With Oracle-specific code generation, no profiles are generated, and the SQLJ run time is largely bypassed during code execution.

Because profile customization is not applicable with Oracle-specific code generation, some generally useful optimization options, formerly available only through Oracle customizer, are now available directly through the SQLJ translator.

There is also an option for `CHAR` comparisons in a `WHERE` clause, accounting for any blank padding in the column. This option is also available as either a translator option (for Oracle-specific code generation) or an Oracle customizer option (for ISO standard code generation).

This section describes the following code generation, optimization, and `CHAR` comparison and bind options:

- `-codegen`

- `-optcols`

- `-optparams`

- `-optparamdefaults`

- `-fixedchar`

- `-ncharconv`

##### Code Generation (-codegen)

The Oracle SQLJ implementation can either generate Oracle-specific JDBC code directly or generate ISO standard code that calls the SQLJ run time, which in turn calls JDBC. With Oracle-specific code generation, there are no profile files and the SQLJ run time is largely bypassed during program execution.

If you want to specify code generation according to the ISO standard, then use the SQLJ translator `-codegen` option as follows:

    -codegen=iso

The default is Oracle-specific SQLJ code generation, but you can also explicitly specify this as follows:

    -codegen=oracle

**Note:**

When `codegen`=`iso`, translator settings for `-user`, `-password`, `-url`, `-optparams`, `-optparamdefaults`, and `-fixedchar` are forwarded to the profile customizer as well. However, if you want to override these settings for customization, particularly for `-user`, `-password`, and `-url`, then you can do so by setting the customizer options directly.

The command-line syntax for this option is as follows:

    -codegen=iso|oracle

For example:

    -codegen=iso

The syntax for as properties file entry for this option is as follows:

    sqlj.codegen=iso|oracle

For example:

    sqlj.codegen=iso

The default value for this option is:

    oracle

##### Column Definitions (-optcols)

Use the SQLJ translator `-optcols` flag to instruct the translator to determine types and sizes of iterator or result set columns. This enables registration of the columns with Oracle JDBC driver when your application runs, saving round trips to the database, depending on the particular driver implementation. Specifically, this is effective for the JDBC Thin driver and positional iterators.

**See Also:**

"[Column Definitions](performance-and-debugging.md)"

**Note:**

This translator option is equivalent to the `optcols` Oracle customizer option and was created for the default Oracle-specific code generation scenario, where there are no profiles. But it is also applicable for ISO standard code generation. In this case, setting the translator option will automatically set the customizer option as well.

You can enable or disable this flag on the SQLJ command line or in a properties file.

Enable it on the command line as follows:

    -optcols

or:

    -optcols=true

This flag is disabled by default, but you can also disable it explicitly. Disable it on the command line as follows:

    -optcols=false

Column definitions require a database connection for examination of the columns of tables being queried, so the SQLJ translator `-user`, `-password`, and `-url` options must also be set appropriately. For example:

    % sqlj -user=HR@jdbc:oracle:oci:@ -optcols MyApp.sqlj
    Password: password

**Note:**

- Because definitions are created for all columns that you select, it is advisable in your SQL operations to explicitly select the columns you will use, rather than using the `SELECT *` syntax, if you may not actually use all the columns selected. A situation where you select more than you need exposes you to a greater risk of run-time errors, if any changes were made to the table between customization and run time, especially when you have customized with column definitions. You may want to translate with the SQLJ `-warn`=`strict` flag set, which will warn you if additional (unwanted) columns will be selected by your query.

- Column definitions are not possible for any iterator or result set that includes one or more object or collection columns.

- An error will be generated if you enable the `-optcols` option without setting the user name, password, and URL for a database connection.

- The translator does not have to connect to the same schema or even the same database that your application will connect to at run time, but the relevant columns will have to be in the same order and of identical types and sizes to avoid run-time errors.

The command-line syntax for this option is as follows:

    -optcols<=true|false>

For example:

    -optcols

The syntax for a properties file entry for this option is as follows:

    sqlj.optcols<=true|false>

For example:

    sqlj.optcols

The default value for this option is:

    false

##### Parameter Definitions (-optparams)

Use the SQLJ translator `-optparams` flag to enable parameter size definitions. If this flag is enabled, SQLJ will register your input and output parameters to optimize JDBC resource allocations according to sizes you specify, with the following precedence:

1.  Size specified in a source code hint, if any

2.  Default size, if any, specified for the corresponding data type in the `-optparamdefaults` option setting

If there is no source code hint or default data type size for a given host variable, then resource allocation is left to JDBC.

**See Also:**

"[Column Definitions](performance-and-debugging.md)"

**Note:**

This translator option is equivalent to the `optparams` Oracle customizer option. It was created for the default Oracle-specific code generation scenario, where there are no profiles. But it is also applicable for ISO standard code generation. In this case, setting the translator option will automatically set the customizer option as well.

You can enable or disable the `-optparams` flag on the command line or in a SQLJ properties file.

Enable it on the command line as follows:

    -optparams

or:

    -optparams=true

This flag is disabled by default, but you can also disable it explicitly. Disable it on the command line as follows:

    -optparams=false

**Note:**

Unlike the `-optcols` option, the `-optparams` option does not require a database connection, because you are providing the size specifications yourself.

Following is a command-line example (omitting a setting for the `-optparamdefaults` option):

    % sqlj -optparams -optparamdefaults=defaults_string MyApp.sqlj

The command-line syntax for this option is as follows:

    -optparams<=true|false>

For example:

    -optparams

The syntax for a properties file entry for this option is as follows:

    sqlj.optparams<=true|false>

For example:

    sqlj.optparams

The default value for this option is:

    false

##### Parameter Default Size (-optparamdefaults)

If you enable the `-optparams` option to set parameter sizes, then use the `-optparamdefaults` option as desired to set default sizes for specified data types. If `-optparams` is not enabled, then any `-optparamdefaults` setting is ignored.

If a host variable has a source code hint to specify its size, then that takes precedence over the corresponding data type default size set with this option. If there is no source code hint or corresponding data type default size for a particular host variable, then resource allocation for that variable is determined by the JDBC driver, just as it would be if `-optparams` were not enabled.

There is no requirement to use the `-optparamdefaults` option, although it is typically used whenever `-optparams` is enabled. If `-optparams` is enabled and there are no default size settings, then resources are allocated either according to source code hints, if any, or according to the JDBC driver.

**See Also:**

"[Parameter Size Definitions](performance-and-debugging.md)"

**Note:**

This translator option is equivalent to the `optparamdefaults` Oracle customizer option. It was created for the default Oracle-specific code generation scenario, where there are no profiles. But it is also applicable for ISO standard code generation. In this case, setting the translator option will automatically set the customizer option as well.

You can set the `-optparamdefaults` flag on the command line or in a SQLJ properties file.

Set it on the command line as follows:

    -optparamdefaults=datatype1(size1),datatype2(size2),...

All sizes are in bytes. Do not include any white space. Use empty parentheses for a null setting.

For example, the following will set sizes of 30 bytes for `VARCHAR2` and 1000 bytes for `RAW`, and will specify a null size setting for `CHAR`. So, for any host variable corresponding to the `CHAR` data type, if there is no source code hint, then the JDBC driver is left to allocate the resources.

    -optparamdefaults=VARCHAR2(30),RAW(1000),CHAR()

The `-optparamdefaults` option recognizes the following data type names:

- `CHAR`

- `VARCHAR`, `VARCHAR2` (synonymous)

- `LONG`, `LONGVARCHAR` (synonymous)

- `BINARY`, `RAW` (synonymous)

- `VARBINARY`

- `LONGVARBINARY`, `LONGRAW` (synonymous)

The `-optparamdefaults` option also recognizes group names and wildcards, as follows:

- `CHAR_TYPE` covers `CHAR`, `VARCHAR`/`VARCHAR2`, and `LONG`/`LONGVARCHAR`.

- `RAW_TYPE` covers `BINARY`/`RAW`, `VARBINARY`, and `LONGVARBINARY`/`LONGRAW`.

- A percent sign (`%`) by itself covers all recognized data types or appended to a partial name, covers a subset of data types. For example, `VAR%` includes all data types that start with "VAR".

The `-optparamdefaults` setting is processed from left to right. When using group names or wildcards, you can override a group setting for particular data types.

The following example sets a general default size of 50 bytes, overrides that with a setting of 500 bytes for raw types, then overrides the raw type group setting with a null setting for `VARBINARY` (leaving that to JDBC for corresponding host variables with no source code hints):

    -optparamdefaults=%(50),RAW_TYPE(500),VARBINARY()

Following is a command-line example, including the `-optparams` setting as well:

    % sqlj -optparams -optparamdefaults=CHAR_TYPE(50),RAW_TYPE(500),CHAR(10)MyApp.sqlj

**Note:**

If at run time the actual size exceeds the registered size of any parameter, then run-time errors will occur.

The command-line syntax for this option is as follows:

    -optparamdefaults=defaults_string

For example:

    -optparamdefaults=VAR%(50),LONG%(500),RAW_TYPE()

The syntax for a properties file entry for this option is as follows:

    sqlj.optparamdefaults=defaults_string

For example

    sqlj.optparamdefaults=VAR%(50),LONG%(500),RAW_TYPE()

The default value for this option is:

    null

##### CHAR Comparisons with Blank Padding (-fixedchar)

Set this flag to `true` to account for blank padding in `CHAR` database columns when binding character strings for `WHERE` clause comparisons. This way, for example, "mystring" would compare positively against "mystring ".

This functionality uses the JDBC `setFixedCHAR()` method, an Oracle extension to take padding into account. The standard JDBC `setString()` method does not account for blank padding.

Following is an example of `-fixedchar` usage:

    % sqlj -fixedchar MyProgram.sqlj AnotherProg.java ...

**Note:**

- This translator option is equivalent to the `fixedchar` Oracle customizer option. It was created for the default Oracle-specific code generation scenario, where there are no profiles. But it is also applicable for ISO standard code generation. In this case, setting the translator option will automatically set the customizer option as well.

- In `CHAR` or `VARCHAR2` columns, the Oracle SQL implementation treats the values `NULL` and ''" (empty string) synonymously. Unfortunately, however, while you can insert the string "", you cannot successfully compare against it without using `IS NULL` syntax. Using `-fixedchar` functionality does not resolve this issue.

The command-line syntax for this option is as follows:

    -fixedchar<=true|false>

For example:

    -fixedchar

The syntax for a properties file entry for this option is as follows:

    sqlj.fixedchar<=true|false>

For example:

    sqlj.fixedchar

The default value for this option is:

    false

##### NCHAR Bind (-ncharconv)

Set this option if you want to use `String` host variables to bind to `NCHAR` columns. This option specifies that the `SetFormOfUse` method should be used in the generated code for all binds to character columns. You need to translate the SQLJ file with is option as follows:

    % sqlj -ncharconv MyApp.sqlj AnotherApp.java ...

This option is supported by both `codegen=oracle` and `codegen=iso`.

**Note:**

- When the SQLJ file is compiled with the `-ncharconv` option, the `setFormOfUse` method is used in the generated code for `codegen=oracle`. For `codegen=iso`, this option information is passed to Oracle SQLJ run time, which internally uses `SetFormOfUse` for bind at run time.

- This translator option is not available in database releases prior to Oracle Database 10g Release 2 (10.2).

The command-line syntax for this option is as follows:

    -ncharconv<=true|false>

For example:

    -ncharconv

The syntax for a properties file entry for this option is as follows:

    sqlj.ncharconv<=true|false>

For example:

    sqlj.ncharconv

The default value for this option is:

    false

### 9.3 Advanced Translator Options

This section documents the syntax and functionality of the advanced flags and options you can specify in running SQLJ, as well as prefixes used to pass options to the JVM, Java compiler, or SQLJ profile customizer. These options enable you to exercise any of the specialized features of the Oracle SQLJ implementation. For options that can also be specified in a properties file, that syntax is noted as well.

This section covers the following topics:

- Prefixes that Pass Option Settings to Other Executables

- Flags for Special Processing

- Semantics-Checking and Offline-Parsing Options

#### 9.3.1 Prefixes that Pass Option Settings to Other Executables

The following flags mark options to be passed to the Java interpreter, Java compiler, and SQLJ profile customizer:

- `-J` (mark options for the Java interpreter)

- `-C` (mark options for the Java compiler)

- `-P` (mark options for the profile customizer, for ISO code generation only)

##### Options to Pass to the Java Virtual Machine (-J)

The `-J` prefix, specified on the command line, marks options to be passed to the JVM from which SQLJ was invoked. This prefix immediately precedes a JVM option, with no spaces in between. After stripping off the `-J` prefix, the `sqlj` script passes the Java option to the JVM. For example:

    -J-Duser.language=ja

After stripping the `-J` prefix, the `sqlj` script passes the `-Duser.language=ja` argument as is to the JVM. In the Sun Microsystems JDK, the

`-Duser.language=ja` flag sets the `user.language` system property to the value `ja` (Japanese), but specific flags are dependent on the actual Java executable you are using and are not interpreted or acted upon by the `sqlj` script in any way.

You cannot pass options to the JVM from a properties file, because properties files are read after the JVM is invoked.

**Note:**

- While it is not possible to use a properties file to pass options directly to the JVM in which the SQLJ translator runs, it is possible to use the `SQLJ_OPTIONS` environment variable for this purpose. It is also possible, if applicable, to use a properties file to pass options to the JVM in which the Java compiler runs.

- The JVM `file.encoding` setting does not apply to Java properties files. Properties files always use the encoding `8859_1`. This is a feature of Java in general, not SQLJ in particular. However, you can use Unicode escape sequences in a properties file. You can use the `native2ascii` utility to determine escape sequences.

The command-line syntax for this option is as follows:

    -J-Java_option

For example:

    -J-Duser.language=ja

##### Options to Pass to the Java Compiler (-C)

The `-C` prefix marks options to pass to the Java compiler invoked from the `sqlj` script. This prefix immediately precedes a Java compiler option, with no spaces in between. After stripping off the `-C` prefix, the `sqlj` script passes the compiler option to the Java compiler. For example:

    -C-nowarn

After stripping the `-C` prefix, the `sqlj` script passes the `-nowarn` argument as is to the compiler.

Generally, compiler options are passed without change, but when you use an equal sign (=) to set a compiler option that takes a value, such as for `-bootclasspath`,

`-extdirs`, or `-target`, the equal sign is stripped out when the option is passed to the compiler. Consider the following example:

    % sqlj -C-bootclasspath=/usr/local/packages/jdk6/jre/lib/rt.jar myfile.sqlj

Also note that if the Java compiler runs in its own JVM, then you can pass options to that JVM through the compiler. Accomplish this by prefixing the JVM option with

`-C-J` with no spaces between this prefix combination and the option. For example:

    -C-J-Duser.language=de

Observe the following restrictions in using the `-C` prefix:

- Do not use `-C-encoding` to specify encoding of `.java` files processed by the Java compiler. Instead, use the SQLJ `-encoding` option, which specifies encoding of `.sqlj` files processed by SQLJ and `.java` files generated by SQLJ, and is also passed to the compiler. This ensures that `.sqlj` files and`.java` files receive the same encoding.

- Do not use `-C-d` to specify an output directory for `.class` files. Instead, use the SQLJ `-d` option, which specifies the output directory for generated profile files (`.ser`), and is also passed to the Java compiler. This will ensure that `.class` files and `.ser` files are in the same directory.

**Note:**

- If you specify compiler options but disable compilation (`-compile=false`), then the compiler options are silently ignored.

- The compiler help option (`-C-help`, presuming your compiler supports `-help`) can be specified only on the command line or in the `SQLJ_OPTIONS` variable, not in a properties file. As with the SQLJ `-help` option, no translation will be done. This is true even if you also specify files to process. SQLJ assumes that you want help or you want translation, but not both.

The command-line syntax for this option is as follows:

    -C-Java_compiler_option

For example:

    -C-nowarn

The syntax for a properties file entry for this option is as follows:

    compile.Java_compiler_option

For example:

    compile.nowarn

##### Options to Pass to the Profile Customizer (-P)

During the customization phase (relevant only for ISO standard code generation), the `sqlj` script invokes a front-end customizer harness, which coordinates the customization and runs your particular customizer. The `-P` prefix marks options for customization, as follows:

- Use `-P` by itself to pass generic options to the customizer harness that apply regardless of the customizer.

- Use `-P-C` to pass vendor-specific options to the particular customizer you are using.

The `-P` and `-P-C` prefixes immediately precede a customizer option, with no spaces in between. After stripping off the prefix, the `sqlj` script passes the customizer option as is to the profile customizer.

One use of the `-P` prefix is to override the default customizer determined by the SQLJ `-default-customizer` option, as follows:

    -P-customizer=your_customizer_class

Example of a generic customizer option:

    -P-backup

The `-backup` flag is a generic customizer option to backup the previous customization before generating a new one.

Following is an example of a vendor-specific customizer option (in this case, Oracle-specific):

    -P-Csummary

The `summary` flag is an Oracle customizer option that prints a summary of the customizations performed.

**Note:**

- There is no hyphen between `-P-C` and a vendor-specific customizer option. With other prefixes and prefix combinations, there is a hyphen between the prefix and the option.

- The customizer help option (`-P-help`) can be specified only on the command line or in the `SQLJ_OPTIONS` variable, not in a properties file. As with the SQLJ `-help` option, no translation will be done. This is true even if you also specify files to process. SQLJ assumes that you want help or you want translation, but not both.

- For ISO code generation, if you specify customization options but turn off customization for `.sqlj` files (and have no `.ser` files on the command line), then the customization options are silently ignored.

- The `-P` prefix is not applicable for the default Oracle-specific code generation, where no profiles are produced and so no customization is performed.

The command-line syntax for this option is as follows:

    -P-<C>profile_customizer_option

For example:

    -P-driver=oracle.jdbc.OracleDriver
    -P-Csummary

The syntax for a properties file entry for this option is as follows:

    profile.<C>profile_customizer_option

For example:

    profile.driver=oracle.jdbc.OracleDriver
    profile.Csummary

#### 9.3.2 Flags for Special Processing

The `.sqlj` files are typically processed by the SQLJ translator, the Java compiler, and, for ISO code generation, the SQLJ profile customizer. The following flags limit this processing, directing the SQLJ startup script to skip the indicated process:

- `-compile`

- `-profile`

The `-ser2class` flag, for ISO code generation, directs SQLJ to convert profiles from serialized resource (`.ser`) files to class files after customization.

The `-checksource` flag instructs SQLJ type resolution, in certain circumstances, to examine source files as well as class files or files specified on the SQLJ command line.

The `-bind-by-identifier` flag specifies that SQLJ treat multiple appearances of the same host variable in a given SQLJ statement as a single bind occurrence.

##### Compilation Flag (-compile)

The `-compile` flag enables or disables processing of `.java` files by the compiler. This applies both to generated `.java` files and to `.java` files specified on the command line. This flag is useful, for example, if you want to compile `.java` files later using a compiler other than `javac`. The flag is `true` by default. Setting it to `false` disables compilation.

When you process a `.sqlj` file with` -compile=false`, you are responsible for compiling and customizing it later as necessary.

Setting `-compile=false` also implicitly sets `-profile=false`. In other words, whenever `-compile` is `false`, both compilation and customization are skipped. If you set `-compile=false` and `-profile=true`, then your `-profile` setting is ignored.

**Note:**

There are situations where it is sensible for `-compile` to be set to `false` even when `.java` files must be accessed for type resolution. You may do this, for example, if you are translating a `.sqlj` file and want to specify one or more `.java` files on the command line for type resolution during translation, but want to compile all your `.java` files later using a particular compiler.

Note, however, that the `-checksource` option can simplify the type resolution process by eliminating the need to enter `.java` files for resolution on the SQLJ command line.

The command-line syntax for this option is as follows:

    -compile<=true|false>

For example:

    -compile=false

The syntax for a properties file entry for this option is as follows:

    sqlj.compile<=true|false>

For example:

    sqlj.compile=false

The default value for this option is:

    true

##### Profile Customization Flag (-profile)

For ISO code generation, the `-profile` flag enables or disables processing of generated profile files (`.ser`) by the SQLJ profile customizer. However, this applies only to `.ser` files generated by the SQLJ translator from `.sqlj` files that you specify on the current command line. It does not apply to previously generated `.ser` files (or to `.jar` files) that you specify on the command line. The flag is `true` by default. Setting it to `false` disables customization.

This option acts differently than the `-compile` option for files specified on the command line. Any `.ser` and `.jar` files specified on the command line are still customized if `-profile=false`. However, `.java` files specified on the command line are not compiled if `-compile=false`. The reason for this is that you may want other operations, such as line mapping, to be performed on a `.java` file. There are, however, no other operations that can be performed on a `.ser` or `.jar` file specified on the command line.

When you process a` .sqlj` file with` -profile=false`, you are responsible for customizing it later, as necessary.

**Note:**

- Set this option to `false` if you do not want your application to require Oracle SQLJ run time and an Oracle JDBC driver when it runs. Or accomplish this by specifying a nondefault customizer, using the `-default-customizer` option. If no customization is performed, then the generic SQLJ run time will be used when your application runs.

- Setting `-compile=false` also implicitly sets `-profile=false`. In other words, whenever `-compile` is `false`, both compilation and customization are skipped. If you set `-compile=false` and `-profile=true`, then your `-profile` setting is ignored.

- This option is not applicable for the default Oracle-specific code generation, where no profiles are produced and so no customization is performed.

The command-line syntax for this option is as follows:

    -profile<=true|false>

For example:

    -profile=false

The syntax for a properties file entry for this option is as follows:

    sqlj.profile<=true|false>

For example:

    sqlj.profile=false

The default value for this option is:

    true

##### Conversion of .ser File to .class File (-ser2class)

With ISO standard SQLJ code generation, the `-ser2class` flag instructs SQLJ to convert generated `.ser` files to `.class` files. This is necessary if you are using SQLJ to create an applet that will be run from a browser that does not support resource file names with the `.ser` suffix.

This also simplifies the naming of schema objects for your profiles in situations where you are translating a SQLJ program on a client and then loading classes and resource files into the server. Loaded class schema objects have a simpler naming convention than loaded resource schema objects.

The conversion is performed after profile customization so that it includes your customizations. The base names of converted files are identical to those of the original files. The only difference in the file name is `.ser` being replaced by `.class`. For example, consider the following:

    Foo_SJProfile0.ser

This is converted to:

    Foo_SJProfile0.class

**Note:**

- The original `.ser` file is not saved.

- Once a profile has been converted to a `.class` file, it cannot be further customized. You would have to delete the `.class` file and rerun SQLJ to recreate the profile.

- Where encoding is necessary, the `-ser2class` option always uses `8859_1` encoding, ignoring the SQLJ `-encoding` setting.

- If you use the default Oracle-specific code generation, then no profiles are produced and the `-ser2class` option does not apply.

The command-line syntax for this option is as follows:

    -ser2class<=true|false>

For example:

    -ser2class

The syntax for a properties file entry for this option is as follows:

    sqlj.ser2class<=true|false>

For example

    sqlj.ser2class

The default value for this option is:

    false

##### Source Check for Type Resolution (-checksource)

It may not be sufficient for the SQLJ type resolution process to examine only class files in the classpath and class or source files specified on the SQLJ command line. The `-checksource` flag instructs SQLJ to also examine source files in the classpath under the following circumstances:

- If a class file cannot be found for a required class, but a source file can be found

- If a source file has a more recent modification date than its corresponding class file

**Note:**

This applies only to Java types that appear in `#sql` statements, not elsewhere in your Java code. Therefore, you should always explicitly provide the names of any required `.sqlj` files on the SQLJ command line.

The command-line syntax for this option is as follows:

    -checksource<=true|false>

For example:

    -checksource=false

The syntax for a properties file entry for this option is as follows:

    sqlj.checksource=<=true|false>

For example:

    sqlj.checksource=false

The default value for this option is:

    true

##### Binding Host Expressions by Identifier (-bind-by-identifier)

In keeping with the SQLJ standard, the Oracle implementation by default creates a unique name for each host-variable bind reference in a statement, even if there are multiple occurrences of the same host variable. The SQLJ standard is based on JDBC, and JDBC does not make provisions for binding the same variable into different positions. Instead, each bind position (identified by `?`) is bound to an individual value.

In some situations this causes errors, such as in the following example:

    #sql emps = { SELECT substr(first_name, 1, :bind_var), sum(salary) FROM employees
                  GROUP BY substr(first_name, 1, :bind_var) };

Because separate bind reference names are created for the two occurrences of `bind_var`, this results in a SQL exception at run time. When the differing bind names are detected, the SQL engine concludes that the `GROUP BY` clause is not part of the `SELECT`-list.

To avoid such problems, Oracle extends standard functionality with the `-bind-by-identifier` flag. A setting of `true` results in all bind occurrences of the same identifier in a given SQLJ statement or PL/SQL block being treated as a single bind occurrence. A SQLJ statement with four bind operations, `:x`, `:x`, `:y`, `:x`, would be bound as `:1`, `:1`, `:2`, `:1` instead of `:1`, `:2`, `:3`, `:4`.

In the preceding example, both bindings would be as `substr(ename, 1, :1)` instead of as `substr(ename, 1, :1)` and `substr(ename, 1, :2)`.

**Note:**

The `-bind-by-identifier` flag applies only to host expressions that are simple host variables.

The command-line syntax for this option is as follows:

    -bind-by-identifier<=true|false>

For example:

    -bind-by-identifier

The syntax for a properties file entry for this option is as follows:

    sqlj.bind-by-identifier=<=true|false>

For example:

    sqlj.bind-by-identifier

The default value for this option is:

    false

#### 9.3.3 Semantics-Checking and Offline-Parsing Options

The following options specify characteristics of online and offline semantics-checking and offline parsing:

- `-offline`

- `-online`

- `-cache`

- `-parse`

Description of these options is preceded by two introductory discussions:

- A discussion of `OracleChecker` (the default front-end class for semantics-checking) and an introduction to Oracle semantics-checkers

- A comparison of online semantics-checking versus offline parsing

**Note:**

Online semantics-checking is enabled by setting the translator `-user` option. However, the setting of the `-parse` option, which is used to enable or disable offline parsing, can override this.

##### Semantics-Checkers and OracleChecker Front End (default checker)

Oracle supplies Oracle-specific offline checkers, a generic offline checker, Oracle-specific online checkers, and a generic online checker. The generic checkers assume you use only Entry Level of SQL-92 and standard JDBC features. Oracle recommends that you use Oracle-specific checkers when using Oracle Database.

The default checker, which is satisfactory in the great majority of circumstances, is `oracle.sqlj.checker.OracleChecker` for both online and offline checking. This class acts as a front end and runs the appropriate semantics-checker, depending on your environment and whether you choose offline or online checking.

For Oracle, there is Oracle8 checker for Oracle 10g, Oracle9i, and Oracle8i types, for both online and offline checking (as used in the corresponding JDBC implementations).

##### Online Checking with Oracle Database and JDBC Driver

If you are using Oracle Database and Oracle JDBC driver with online checking, then `OracleChecker` will choose a checker based on the lower of your database version and JDBC driver version. The following table summarizes the choices for the possible combinations of database version and driver version, and also notes any other Oracle checkers that would be legal.

Table 9-4 Oracle Online Semantics-Checkers Chosen by OracleChecker

| Database Release     | JDBC Release | Chosen Online Checker | Other Legal Online Checkers |
|:---------------------|:-------------|:----------------------|:----------------------------|
| Oracle10g, 9i, or 8i | Oracle11g    | Oracle8JdbcChecker    | Oracle8To7JdbcChecker       |

##### Offline Checking with Oracle JDBC Driver

If you are using an Oracle JDBC driver with offline checking, then `OracleChecker` chooses a checker based on your JDBC driver version. The following table summarizes the possible choices.

Table 9-5 Oracle Offline Semantics-Checkers Chosen by OracleChecker

| JDBC Release | Chosen Offline Checker | Other Legal Offline Checkers |
|:-------------|:-----------------------|:-----------------------------|
| Oracle11g    | Oracle8OfflineChecker  | No                           |

##### Online Semantics-Checking Versus Offline Parsing

The Oracle SQLJ implementation supports a feature known as offline parsing that offers a limited alternative to online semantics-checking. Offline parsing does not use a database connection, so cannot perform verification of operations against the database schema, but does offer syntax-checking of all SQL and PL/SQL statements. (Prior to Oracle9i, syntax-checking was not possible without a database connection.)

The following table provides a comparative summary of what offline parsing and online semantics-checking offer.

Table 9-6 Feature Comparison: Offline Parsing Versus Online Semantics-Checking

| Feature                                                                        | By Offline Parsing? | By Online Checking? |
|:-------------------------------------------------------------------------------|:--------------------|:--------------------|
| Verify data manipulation language (DML), SELECT, and PL/SQL syntax.            | Yes                 | Yes                 |
| Verify data definition language (DDL) syntax.                                  | Yes                 | No                  |
| Verify DML, SELECT, and PL/SQL semantics (comparison against database schema). | No                  | Yes                 |
| Verify DDL semantics (comparison against database schema).                     | No                  | No                  |

Online checking offers the primary advantage of verifying SQL and PL/SQL operations against the database schema. This includes verifying that column types match SQL operations and verifying the existence of called stored procedures. It requires a database connection during translation, however, which may be problematic in some circumstances. It also performs no verification of DDL operations.

Offline parsing offers the advantage of SQL syntax-checking without a database connection during translation, and also includes DDL operations in its syntax verifications.

Note that neither mode performs DDL semantics-checking against the database schema.

**Note:**

- If both offline parsing and online checking are enabled, some types of errors will be reported twice.

- Problems detected by either the offline parser or the online checker are reported at a warning or advisory level, not a fatal level.

- Do not confuse offline parsing with offline semantics-checking. Offline checking consists of basic semantics-checking steps that always occur, regardless of whether online checking is enabled and regardless of whether offline parsing is enabled: analysis of the types of Java expressions in your SQLJ executable statements, and categorization of embedded SQL operations according to keyword, such as `SELECT`.

- Compatibility of data corresponding to weakly typed host expressions is never checked.

- Mode compatibility of expressions in PL/SQL anonymous blocks is never checked.

##### Offline Semantics-Checker (-offline)

The `-offline` option specifies a Java class that implements the semantics-checking component of SQLJ for offline checking. With offline checking, there is no database connection. Only SQL syntax and usage of Java types is checked. Note that offline checking is neither enabled nor disabled by the `-offline` option. Offline checking runs only when online checking does not, either because online checking is not enabled or because the database connection cannot be established.

You can specify different offline checkers for different connection contexts, with a limit of one checker per context. Do not list multiple offline checkers for one connection context. The default `OracleChecker`, a front-end class, will serve your needs unless you want to specify a particular checker that would not be chosen by `OracleChecker`.

The following example shows how to select Oracle8 offline checker for a particular connection context (`CtxClass`):

    -offline@CtxClass=oracle.sqlj.checker.Oracle8OfflineChecker

This results in SQLJ using `oracle.sqlj.checker.Oracle8OfflineChecker` for offline checking of any of your SQLJ executable statements that specify a connection object that is a `CtxClass` instance.

The `CtxClass` connection context class must be declared in your source code or previously compiled into a `.class` file. (See "[Connection Contexts](advanced-language-features.md)" for more information.)

Use the `-offline` option separately for each connection context offline checker you want to specify; these settings have no influence on each other. For example:

    -offline@CtxClass2=oracle.sqlj.checker.Oracle8OfflineChecker
    -offline@CtxClass3=sqlj.semantics.OfflineChecker

To specify the offline checker for the default connection context and any other connection contexts for which you do not specify an offline checker:

    -offline=oracle.sqlj.checker.Oracle8OfflineChecker

Any connection context without an offline checker setting uses the offline checker setting of the default connection context, presuming an offline checker has been set for the default context.

The command-line syntax for this option is as follow:

    -offline<@conn_context_class>=checker_class

For example:

    -offline=oracle.sqlj.checker.Oracle8OfflineChecker
    -offline@CtxClass=oracle.sqlj.checker.Oracle8OfflineChecker

The syntax for a properties file entry for this option is as follows:

    sqlj.offline<@conn_context_class>=checker_class

For example:

    sqlj.offline=oracle.sqlj.checker.Oracle8OfflineChecker
    sqlj.offline@CtxClass=oracle.sqlj.checker.Oracle8OfflineChecker

The default value for this option is:

    oracle.sqlj.checker.OracleChecker

##### Online Semantics-Checker (-online)

The `-online` option specifies a Java class or list of classes that implement the online semantics-checking component of SQLJ. This involves connecting to a database. Note that online checking is not enabled by the `-online` option. You must enable it through the `-user` option. The `-password`, `-url`, and `-driver` options must be set appropriately as well.

**Note:**

Some settings of the SQLJ `-parse` option will disable online semantics-checking, overriding the effect of the `-user` option.

You can specify different online checkers for different connection contexts, and you can list multiple checkers (separated by commas) for any given context. In cases where multiple checkers are listed for a single context, SQLJ uses the first checker (reading from left to right in the list) that accepts the database connection established for online checking. At analysis time, a connection is passed to each online checker and the checker decides whether it recognizes the database.

The default `OracleChecker`, a front-end class, will serve your needs unless you want to specify a particular checker that would not be chosen by `OracleChecker`.

The following example shows how to select Oracle8 online checker for the `DefaultContext` class and any other connection context classes without a specified setting:

    -online=oracle.sqlj.checker.Oracle8JdbcChecker

To specify a list of drivers and allow the proper class to be selected depending on what kind of database is being accessed:

    -online=oracle.sqlj.checker.Oracle8JdbcChecker,sqlj.semantics.JdbcChecker

With this specification, if connection is made to Oracle Database, then SQLJ uses the `oracle.sqlj.checker.Oracle8JdbcChecker` semantics-checker. If connection is made to any other kind of database, then SQLJ uses the generic `sqlj.semantics.JdbcChecker` semantics-checker. This is similar functionally to what the default `OracleChecker`.

To specify the online checker for a particular connection context (`CtxClass`):

    -online@CtxClass=oracle.sqlj.checker.Oracle8JdbcChecker

This results in the use of `oracle.sqlj.checker.Oracle8JdbcChecker` for online checking of any of your SQLJ executable statements that specify a connection object that is an instance of `CtxClass`, presuming you enable online checking for `CtxClass`.

The `CtxClass` connection context class must be declared in your source code or previously compiled into a `.class` file.

Use the `-online` option separately for each connection context online checker you want to specify. These settings have no influence on each other:

    -online@CtxClass2=oracle.sqlj.checker.Oracle8JdbcChecker
    -online@CtxClass3=sqlj.semantics.JdbcChecker

Any connection context without an online checker setting uses the online checker setting of the default connection context.

The command-line syntax for this option is as follows:

    -online<@conn_context_class>=checker_class(list)

For example:

    -online=oracle.sqlj.checker.Oracle8JdbcChecker
    -online=oracle.sqlj.checker.Oracle8JdbcChecker,sqlj.semantics.JdbcChecker
    -online@CtxClass=oracle.sqlj.checker.Oracle8JdbcChecker

The syntax for a properties file entry for this option is as follows:

    sqlj.online<@conn_context_class>=checker_class(list)

For example:

    sqlj.online=oracle.sqlj.checker.Oracle8JdbcChecker
    sqlj.online=oracle.sqlj.checker.Oracle8JdbcChecker,sqlj.semantics.JdbcChecker
    sqlj.online@CtxClass=oracle.sqlj.checker.Oracle8JdbcChecker

The default value for this option is:

    oracle.sqlj.checker.OracleChecker

##### Caching of Online Semantics-Checker Results (-cache)

Use the `-cache` option to enable caching of the results generated by the online checker. This avoids additional database connections during subsequent SQLJ translation runs. The analysis results are cached in a file, `SQLChecker.cache`, that is placed in your current directory. The cache contains serialized representations of all SQL statements successfully translated (translated without error or warning messages), including all statement parameters, return types, translator settings, and modes.

The cache is cumulative and continues to grow through successive invocations of the SQLJ translator. Delete the `SQLChecker.cache` file to empty the cache.

The command-line syntax for this option is as follows:

    -cache<=true|false>

For example:

    -cache

The syntax for a properties file entry for this option is as follows:

    sqlj.cache<=true|false>

For example:

    sqlj.cache

The default value for this option is:

    false

##### Offline Parser (-parse)

Use the `-parse` option to enable offline parsing. This feature is a complement to online semantics-checking, offering SQL and PL/SQL syntax-checking (but not verification against the schema) without a database connection during translation. Offline parsing also checks syntax for DDL statements, which online checking does not.

Also be aware that the setting of the `-parse` option can override the enabling of online checking by the `-user` option. Possible `-parse` settings are as follows:

- `both` (default): Enable the offline parser and allow online checking. In this case, online checking is determined by the `-user` option.

- `online-only`: Disable the offline parser and allow online checking. Again, online checking is determined by the `-user` option.

- `offline-only`: Enable the offline parser and disallow online checking. This overrides any `-user` option setting that would otherwise enable online checking.

- `none`: Disable the offline parser and disallow online checking, Again, this overrides any `-user` option setting that would otherwise enable online checking.

- `parserclassname`: Specify the name of a Java class that implements an alternative SQL parser. The class must implement the `sqlj.framework.checker.SimpleChecker` interface. This setting enables the specified parser, and only that parser is used for SQL-checking. The standard offline parser and online checking are both disabled.

FUTURE: Document the SimpleChecker interface.

The `offline-only` and `none` settings are offered for completeness, but are not typical modes of operation. It is best to let the `-user` option determine online checking. It is also not typical to specify your own parser.

**Note:**

In modes where both offline parsing and online checking are enabled, there may be duplicate reporting of some problems.

The command-line syntax for this option is as follows:

    -parse=both|online-only|offline-only|none|parserclassname

For example:

    -parse=online-only

The syntax for a properties file entry for this option is as follows:

    sqlj.parse=both|online-only|offline-only|none|parserclassname

For example:

    sqlj.parse=online-only

The default value for this option is:

    both

### 9.4 Translator Support and Options for Alternative Environments

By default, the Oracle Database 12c Release 1 (12.1) SQLJ implementation is configured to run under standard JDK 6 and to use the standard compiler `javac`. These are not requirements, however. You can configure SQLJ to work with alternative JVMs or compilers. To do so, you must supply SQLJ with the following information:

- The name of the JVM to use (`-vm` option)

- The name of the Java compiler to use (`-compiler-executable` option)

- Any settings the compiler requires

A set of SQLJ options enables you to provide this information. SQLJ also defaults to Oracle profile customizer, but can work with alternative customizers as well.

**Note:**

Be aware of the limitations of any operating system and environment you use. In particular, the complete, expanded SQLJ command line must not exceed the maximum command-line size. Consult your operating system documentation.

This section covers the following topics:

- Java and Compiler Options

- Customization Options

#### 9.4.1 Java and Compiler Options

The following options relate to the operation of the JVM and Java compiler:

- `-vm` (to specify the JVM, on the command line only)

- `-compiler-executable` (to specify the Java compiler)

- `-compiler-encoding-flag`

- `-compiler-output-file`

- `-compiler-pipe-output-flag`

Some compilers, such as the standard `javac`, require a Java source file name to match the name of the public class, if any, defined there. Therefore, by default the SQLJ translator verifies that this is true. However, you can use the `-checkfilename` option to instruct SQLJ not to verify this.

For some JVM and compiler configurations, there may be problems with the way SQLJ usually invokes the compiler. You can use the `-passes` option to alleviate this by breaking SQLJ processing into a two-pass process. You can also pass options directly to the particular JVM or compiler you use, through the `-J` and `-C` prefixes.

**Note:**

The `-vm` option, `-passes` option, and `-J` prefix cannot be used in a properties file. You can set them on the command line or, more conveniently, in the `SQLJ_OPTIONS` environment variable.

##### Name of the Java Virtual Machine (-vm)

Use the `-vm` option if you want to specify a particular JVM for SQLJ to use. Otherwise, SQLJ uses the standard `java` from the Sun Microsystems JDK. You cannot set this option in a properties file, because properties files are read after the JVM is invoked.

If you do not specify a directory path along with the name of the JVM executable file, then SQLJ looks for the executable according to the setting of your operating system `PATH` variable.

**Note:**

Special functionality of this option, `-vm=echo`, is supported. This is equivalent to the `-n` option, instructing the `sqlj` script to construct the full command line that would be passed to the SQLJ translator, and echo it to the user without having the translator execute it.

The command-line syntax for this option is as follows:

    -vm=JVM_path+name

For example:

    -vm=/myjavadir/myjavavm

The default value is:

    java

##### Name of the Java Compiler (-compiler-executable)

Use the `-compiler-executable` option if you want to specify a particular Java compiler for SQLJ to use. Otherwise SQLJ, uses the standard `javac` from the Sun Microsystems JDK.

If you do not specify a directory path along with the name of the compiler executable file, then SQLJ looks for the executable according to the setting of your operating system `PATH` variable.

The following is required of any Java compiler that you use:

- It can write error and status information to the standard output device (for example, `STDOUT` on a UNIX system) or to a file, as directed by the `-compiler-output-file` option.

- It will understand the SQLJ `-d` option, which determines the root directory for class files.

- It must return a nonzero exit code to the operating system whenever a compilation error occurs.

- The line information that it provides in any errors or messages must be in one of the following formats (items in `<>` brackets being optional):

  - Sun Microsystems `javac` format

        filename.java:line<.column><-line<.column>>

    Example: `myfile.java:15: Illegal character: '\u01234'`

  - Microsoft `jvc` format

        filename.java(line,column)

    Example: `myfile.java(15,7) Illegal character: '\u01234'`

As always, SQLJ processes compiler line information so that it refers to line numbers in the original `.sqlj` file, not in the produced `.java` file.

**Note:**

For a compiler that does not support an `-encoding` option, disable the `-compiler-encoding-flag`.

The command-line syntax for this option is as follows:

    -compiler-executable=Java_compiler_path+name

For example:

    -compiler-executable=/myjavadir/myjavac

The syntax for a properties file entry for this option is as follows:

    sqlj.compiler-executable=Java_compiler_path+name

For example:

    sqlj.compiler-executable=myjavac

The default value is:

    javac

##### Compiler Encoding Support (-compiler-encoding-flag)

When you use the `-encoding` option to specify an encoding character set for SQLJ to use, SQLJ passes this to the Java compiler for the compiler to use as well. Set the `-compiler-encoding-flag` to `false` if you do not want SQLJ to pass the character encoding to the compiler. For example, if you are using a compiler other than `javac` and it does not support an `-encoding` option by that name.

The command-line syntax for this option is as follows:

    -compiler-encoding-flag<=true|false>

For example:

    -compiler-encoding-flag=false

The syntax for a properties file entry for this option is as follows:

    sqlj.compiler-encoding-flag<=true|false>

For example:

    sqlj.compiler-encoding-flag=false

The default value is:

    true

##### Compiler Output File (-compiler-output-file)

If you want the Java compiler to write its results to a file, then use the `-compiler-output-file` option to make SQLJ aware of the file name. Otherwise, SQLJ assumes that the compiler writes to the standard output device, such as `STDOUT` on a UNIX system. As appropriate, specify an absolute path or a relative path from the current directory.

**Note:**

You cannot use this option if you enable `-passes`, which requires output to `STDOUT`.

The command-line syntax for this option is as follows:

    -compiler-output-file=output_file_path+name

For example:

    -compiler-output-file=/myjavadir/mycmploutput

The syntax for a properties file entry for this option is as follows:

    sqlj.compiler-output-file=output_file_path+name

For example:

    sqlj.compiler-output-file=/myjavadir/mycmploutput

This option does not have a default value.

##### Compiler Message Output Pipe (-compiler-pipe-output-flag)

**Note:**

This option is relevant only for JDK 1.2.x.

By default, the Java compiler writes errors and message output to `STDERR`. However, if the error messages from the Java compiler should also be redirected to the same file as specified with the `-compiler-output-file` option, then set this flag to true. This option is meaningful only if used in conjunction with the `-compiler-output-file` option.

If SQLJ sets the `javac.pipe.output` system property to `true`, which is the SQLJ default behavior when it invokes the Java compiler, then compiler error and message output will be sent to `STDOUT`. However, you can specify `-compiler-pipe-output-flag=false` to instruct SQLJ to not set this system property when it invokes the Java compiler. You should do this, for example, if the Java compiler you are using does not support the `javac.pipe.output` system property.

You can set this flag in a properties file, as well as on the command line or in the `SQLJ_OPTIONS` environment variable.

**Note:**

For a Java compiler that originates from Sun Microsystems and writes its output to `STDERR` by default, you must leave `-compiler-pipe-output-flag` enabled, if you enable `-passes`, which requires output to `STDOUT`.

The command-line syntax for this option is as follows:

    -compiler-pipe-outflag=<true|false>

For example, while compiling a file called `MyDemo.sqlj`, for which the Java compiler messages and error messages are to be redirected to the same file, the following syntax should be used:

    sqlj -compiler-output-file=/myjavadir/mycmploutput
    -compiler-pipe-output-flag=true MyDemo.sqlj

The syntax for a properties file entry for this option is as follows:

    sqlj.compiler-pipe-output-flag<=true|false>

The default value is:

    true

**Note:**

If this flag is set to false, then the error messages from the Java compiler will be directed to `STDERR`.

##### Source File Name Check (-checkfilename)

It is generally advisable for the source file name to always match the name of the public class defined or, if there is no public class, the name of the first class defined. For example, public class `MyPublicClass` should be defined in a `MyPublicClass.sqlj` source file.

The `-checkfilename` flag instructs SQLJ whether to verify that the SQLJ source file name matches the name of the public class, if any, defined there. Some compilers, such as the standard `javac`, require this to be the case, while others do not.

To maximize portability of your code, this flag should be enabled, which it is by default.

**Note:**

If you are translating in the server, where there is no equivalent naming requirement, there is no `-checkfilename` option and the translator executes no such check.

The command-line syntax for this option is as follows:

    -checkfilename<=true|false>

For example:

    -checkfilename=false

The syntax for a properties file entry for this option is as follows:

    sqlj.checkfilename<=true|false>

For example:

    sqlj.checkfilename=false

The default value is:

    true

##### SQLJ Two-Pass Execution (-passes)

By default, the following occurs when you invoke the `sqlj` script:

1.  The `sqlj` script invokes your JVM, which runs the SQLJ translator.

2.  The translator completes the semantics-checking and translation of your `.sqlj` files, generating translated `.java` files.

3.  The translator invokes your Java compiler, which compiles the generated `.java` files.

4.  The translator processes the compiler output.

5.  If any profile files were generated, then the translator invokes a profile customizer to customize them.

For some JVM and compiler configurations, however, the compiler invocation in Step 3 might not return, in which case your translation will suspend.

If you encounter this situation, the solution is to instruct SQLJ to run in two passes, with the compilation step in between. To accomplish this, you must enable the two-pass execution flag as follows:

    -passes

The `-passes` option must be specified on the command line or, equivalently, in the `SQLJ_OPTIONS` environment variable. It cannot be specified in a properties file.

**Note:**

- If you enable `-passes`, then compiler output must go to `STDOUT`. Therefore, leave `-compiler-pipe-output-flag` enabled, which is its default. In addition, you cannot use the `-compiler-output-file` option, which would result in writing to a file instead of to `STDOUT`.

- Like other command-line-only flags (`-help`, `-version`, `-n`), the `-passes` flag does not support `=true` syntax.

With `-passes` enabled, the following occurs when you invoke the `sqlj` script:

1.  The `sqlj` script invokes your JVM, which runs the SQLJ translator for its first pass.

2.  The translator completes the semantics-checking and translation of your `.sqlj` files, generating translated `.java` files.

3.  The JVM is terminated.

4.  The `sqlj` script invokes the Java compiler, which compiles the generated `.java` files.

5.  The `sqlj` script invokes your JVM again, which runs the SQLJ translator for its second pass.

6.  The translator processes compiler output.

7.  If any profile files were generated, the JVM runs your profile customizer to customize them.

With this sequence, you circumvent any problems the JVM might have in invoking the Java compiler.

The command-line syntax for this option is as follows:

    -passes

For example:

    -passes

The default value is:

    off

#### 9.4.2 Customization Options

The following options relate to the customization of your SQLJ profiles, if applicable:

- `-default-customizer`

- Options passed directly to the customizer

**Note:**

If you use the default Oracle-specific code generation, then SQLJ generates no profiles and, therefore, performs no customization. In that case, these options do not apply.

##### Default Profile Customizer (-default-customizer)

Use the `-default-customizer` option to instruct SQLJ to use a profile customizer other than the default, which is:

    oracle.sqlj.runtime.util.OraCustomizer

In particular, use this option if you are not using Oracle Database. This option takes a fully qualified Java class name as its argument.

**Note:**

You can override this option with the `-P-customizer` option in your SQLJ command line or properties file.

The command-line syntax for this option is as follows:

    -default-customizer=customizer_classname

For example:

    -default-customizer=sqlj.myutil.MyCustomizer

The syntax for a properties file entry for this option is as follows:

    sqlj.default-customizer=customizer_classname

For example:

    sqlj.default-customizer=sqlj.myutil.MyCustomizer

The default value for this option is:

    oracle.sqlj.runtime.util.OraCustomizer

**Note:**

When you use Oracle Database and ISO code generation, Oracle recommends that you use the default `OraCustomizer` for your profile customization.

##### Options Passed Directly to the Customizer

As with the JVM and compiler, you can pass options directly to the profile customizer harness using a prefix, in this case `-P`.
