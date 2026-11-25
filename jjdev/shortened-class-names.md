Each Java source, class, and resource is stored in its own schema object in the server. The name of the schema object is derived from the fully qualified name, which includes relevant path or package information. Dots are replaced by slashes.

Schema object names, however, have a maximum of only 30 characters, and all characters must be legal and convertible to characters in the database character set. If any fully qualified name is longer than 30 characters or contains illegal or nonconvertible characters, then Oracle Database converts it to a short name, or alias, to use as the name of the schema object. Oracle Database keeps track of both the names and how to convert between them. If the fully qualified name is 30 characters or less and has no illegal or inconvertible characters, then it is used as the schema object name.

Because Java classes and methods can have names exceeding the maximum SQL identifier length, Oracle Database uses abbreviated names internally for SQL access. Oracle Database provides the `LONGNAME()` function within the `DBMS_JAVA` package for retrieving the original Java class name for any truncated name.

    FUNCTION longname (shortname VARCHAR2) RETURN VARCHAR2

This function returns the fully qualified name of the Java schema object, which is specified using its alias. The following is an example of a statement used to display the fully qualified name of classes that are invalid:

    SELECT dbms_java.longname (object_name) FROM user_objects WHERE object_type = 'JAVA CLASS' and status = 'INVALID';

You can also specify a full name to the database by using the `SHORTNAME() `function of the `DBMS_JAVA` package. The function takes a full name as input and returns the corresponding short name. This function is useful for verifying whether the classes are loaded successfully, by querying the `USER_OBJECTS` view.

    FUNCTION shortname (longname VARCHAR2) RETURN VARCHAR2

**Related Topics**

- [System Classes](Oracle-JVM-components.md)
