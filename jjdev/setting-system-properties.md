Within an RDBMS session you can maintain a set of values that are added to the system properties whenever a Java session is started in the RDBMS session. This set of values remains valid for the duration of the longer tier of Java session state, which is typically the same as the duration of the RDBMS session.

There is a set of PL/SQL functions in the `DBMS_JAVA` package for setting, retrieving, removing and displaying key value pairs in an internal, RDBMS session duration table, where both elements of a pair are strings (`VARCHAR2`) and there is at most one pair for a given key. These functions are as follows:

- set_property

- get_property

- remove_property

- show_property

### set_property

This function establishes a value for a system property that is then used for the duration of the current RDBMS session, whenever a Java session is initialized. The first argument is the name of the property and the second is the value to be established for it. The return value for `set_property` is null unless there is some error. For example, if an attempt is made to set a value for a prescribed property, then an error message is returned.

    FUNCTION set_property(name VARCHAR2, value VARCHAR2) RETURN VARCHAR2;

### get_property

This function returns any value previously established by `set_property.` It returns null if there is no such value.

    FUNCTION get_property(name VARCHAR2) RETURN VARCHAR2;

### remove_property

This function removes any value previously established by `set_property.` The return value is null unless an error occurred, in which case an error message is returned.

    FUNCTION remove_property(name VARCHAR2) RETURN VARCHAR2;

### show_property

This function displays a message of the form `name = value` for the input name, or for all established property bindings, if name is null. The return value for this function is null on successful completion, otherwise it is an error message. The output is displayed to wherever you have currently directed your Java output.

    FUNCTION show_property(name VARCHAR2) RETURN VARCHAR2;

Before initializing the Java session, the values from this table are added to the set of default system property values already maintained by Oracle JVM. When you run a Java method by using the command-line interface, the values determined by the `-D` option, if present, override the values set in the table. As soon as you terminate the Java session, the values established by the `-D` option become obsolete and the keys are set to the original values as present in the table.

**Related Topics**

- [Two-Tier Duration for Java Session State](two-tier-Java-session-duration.md)
