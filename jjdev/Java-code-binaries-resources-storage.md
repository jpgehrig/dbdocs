In the standard Java development environment, Java source code, binaries, and resources are stored as files in a file system, as follows:

- Source code files are saved as `.java` files.

- Compiled Java binary files are saved as `.class` files.

- Resources are any data files, such as `.properties` or `.ser` files, that are stored in the file system hierarchy and are loaded and used at run time.

In addition, when you run a Java application, you specify the `CLASSPATH`, which is a file or directory path in the file system that contains your `.class` files. Java also provides a way to group these files into a single archive form, a ZIP or Java Archive (JAR) file.

Both these concepts are different in Oracle Database environment.

Table 2-1 describes how Oracle Database handles Java classes and locates dependent classes.

Table 2-1 Description of Java Code and Classes Storage in Oracle Database

| Tasks                                      | How it differs for Oracle JVM                                                                                                                                                                                                                                                                                                                                                                              |
|:-------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Storing Java code, binaries, and resources | In Oracle Database, source code, classes, and resources reside within the database and are known as Java schema objects, where a schema corresponds to a database user. There are three types of Java schema objects: source, class, and resource. There are no `.java`, `.class`, `.sqlj`, `.properties`, or `.ser` files on the server. Instead, these files map to the appropriate Java schema objects. |
| Locating Java classes                      | Instead of the `CLASSPATH`, you use a resolver to specify one or more schemas to search for Java source, class, and resource schema objects.                                                                                                                                                                                                                                                               |
