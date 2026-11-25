After writing the Java classes, use the `loadjava` tool to upload your Java stored procedures into Oracle Database, as follows:

    > loadjava -u HR@myPC:1521:orcl -v -r -t POManager.java
    Password: password
    initialization complete
    loading : POManager
    creating : POManager
    resolver : resolver ( ("*" HR) ("*" public) ("*" -) )
    resolving: POManager

The `-v` option enables the verbose mode, the `-r` option compiles uploaded Java source files and resolves external references in the classes, and the `-t` option tells the `loadjava` tool to connect to the database using the client-side JDBC Thin driver.
