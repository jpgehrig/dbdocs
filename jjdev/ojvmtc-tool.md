This section describes the following topics:

- About the ojvmtc Tool

- Arguments of ojvmtc Command

### 12.5.1 About the ojvmtc Tool

The `ojvmtc` tool enables you to resolve all external references, prior to running the `loadjava` tool. The `ojvmtc` tool allows the specification of a classpath that specifies the JARs, classes, or directories to be used to resolve class references. When an external reference cannot be resolved, this tool either produces a list of unresolved references or generated stub classes to allow resolution of the references, depending on the options specified. Generated stub classes throw a `java.lang.ClassNotfoundException` if it is referenced at runtime.

The syntax is:

    ojvmtc [-help ] [-bootclasspath] [-server connect_string] [-jar jar_name] [-list] -classpath jar1:path2:jar2
    jars,...,classes

For example:

    ojvmtc -bootclasspath $JAVA_HOME/jre/lib/rt.jar -classpath classdir/lib1.jar:classdir/lib2.jar -jar set.jar app.jar

The preceding example uses `rt.jar`, `classdir/lib1.jar`, and `classdir/lib2.jar` to resolve references in `app.jar.` All the classes examined are added to `set.jar,` except for those found in `rt.jar.`

Another example is:

    ojvmtc -server thin:HR/@localhost:5521:orcl -classpath jar1:jar2 -list app2.jar
    Password:password

The preceding example uses classes found in the server specified by the connection string as well as `jar1` and `jar2` to resolve `app2.jar.` Any missing references are displayed to `stdout.`

### 12.5.2 Arguments of ojvmtc Command

Table 12-1 summarizes the arguments of this command.

Table 12-1 ojvmtc Argument Summary

| Argument                  | Description                                                                                                                                                                                                                                                                                                                              |
|:--------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-classpath`              | Uses the specified JARs and classes for the closure set.                                                                                                                                                                                                                                                                                 |
| `-bootclasspath`          | Uses the specified classes for closure, but does not include them in the closure set.                                                                                                                                                                                                                                                    |
| `-server connect_string`  | Connects to the server using visible classes in the same manner as `-bootclasspath.`                                                                                                                                                                                                                                                     |
| `connect_string thin|OCI` | Connects to the server using thin or Oracle Call Interface (OCI) specific driver.<br>If you use thin driver, the syntax is as follows:<br>`thin:user/passwd@host:port:sid`<br>If you use OCI driver, the syntax is as follows:<br>`oci:user/passwd@host:port:sid`<br>`oci:user/passwd@tnsname`<br>`oci:user/passwd@(connect descriptor)` |
| `-jar jar_name`           | Writes each class of the closure set to a JAR and generates stubs for missing classes                                                                                                                                                                                                                                                    |
| `-list`                   | Lists the missing classes.                                                                                                                                                                                                                                                                                                               |
