You can pass Java output to SQL statements to provide more extensive control over the destination of output from Oracle JVM. The PL/SQL package `DBMS_JAVA` has been enhanced by adding the following new functions, which provide extended functionality to what was previously available only with the `DBMS_JAVA.SET_OUTPUT` procedure:

- set_output_to_sql

- remove_output_to_sql

- enable_output_to_sql

- disable_output_to_sql

- query_output_to_sql

### set_output_to_sql

`set_output_to_sql` defines a named output specification that constitutes an instruction for executing a SQL statement, whenever output to the default `System.out` and `System.err` streams occurs. The specification is defined either for the duration of the current session, or till the `remove_output_to_sql` function is called with its ID. The SQL actions prescribed by the specification occur whenever there is Java output. This can be stopped and started by calling the `disable_output_to_sql` and `enable_output_to_sql` functions respectively. The return value of this function is null on success, otherwise an error message.

    FUNCTION set_output_to_sql (id VARCHAR2,
    stmt VARCHAR2,
    bindings VARCHAR2,
    no_newline_stmt VARCHAR2 default null,
    no_newline_bindings VARCHAR2 default null,
    newline_only_stmt VARCHAR2 default null,
    newline_only_bindings VARCHAR2 default null,
    maximum_line_segment_length NUMBER default 0,
    allow_replace NUMBER default 1,
    from_stdout NUMBER default 1,
    from_stderr NUMBER default 1,
    include_newlines NUMBER default 0,
    eager NUMBER default 0) return VARCHAR2;

Table 3-2 describes the arguments the `set_output_to_sql` function takes.

Table 3-2 set_output_to_sql Argument Summary

| Argument                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:----------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                          | The name of the specification. Multiple specifications may exist in the same session, but each must have a distinct ID. The ID is used to identify the specification in the functions `remove_output_to_sql, enable_output_to_sql, disable_output_to_sql, `and `query_output_to_sql.`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| stmt                        | The default SQL statement to execute when Java output occurs.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| bindings                    | A string containing tokens from the set ID, TEXT, LENGTH, LINENO, SEGNO, NL, and ERROUT. This string defines how the SQL statement `stmt` is bound. The position of a token in the bindings string corresponds to the bind position in the SQL statement. The meanings of the tokens are:<br>• ID is the ID of the specification. It is bound as a VARCHAR2.<br>• TEXT is the text being output. It is bound as a VARCHAR2.<br>• LENGTH is the length of the text. It is bound as a NUMBER.<br>• LINENO is the line number since the beginning of session output. It is bound as a NUMBER.<br>• SEGNO is the segment number within a line that is being output in more than one piece. It is bound as a NUMBER.<br>• NL is a boolean indicating whether the text is to be regarded as newline terminated. It is bound as a NUMBER. The newline may or may not actually be included in the text, depending on the value of the `include_newlines` argument.<br>• ERROUT is a boolean indicating whether the output came from `System.out` or `System.err.` It is bound as a NUMBER. The value is 0, if the output came from `System.out.` |
| no_newline_stmt             | An optional alternate SQL statement to execute, when the output is not newline terminated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| no_newline_bindings         | A string with the same syntax as for the bindings argument discussed previously, describing how the `no_newline_stmt` is bound.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| newline_only_stmt           | An optional alternate SQL statement to execute when the output is a single newline.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| newline_only_bindings       | A string with the same syntax as for the bindings argument discussed previously, describing how the `newline_only_stmt` is bound.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| maximum_line_segment_length | The maximum number of characters that is bound in a given execution of the SQL statement. Longer output sequences are broken up into separate calls with distinct SEGNO values. A value of 0 means `no maximum.`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| allow_replace               | Controls behavior when a previously defined specification with the same ID exists. A value of 1 means replacing the old specification. 0 means returning an error message without modifying the old specification.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| from_stdout                 | Controls whether output from `System.out` causes execution of the SQL statement prescribed by the specification. A value of 0 means that if the output came from `System.out,` then the statement is not executed, even if the specification is otherwise enabled.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| from_stderr                 | Controls whether output from `System.err` causes execution of the SQL statement prescribed by the specification. A value of 0 means that if the output came from `System.err,` then the statement is not executed, even if the specification is otherwise enabled.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| include_newlines            | Controls whether newline characters are left in the output when they are bound to text. A value of 0 means new lines are not included. But the presence of the newline is still indicated by the NL binding and the use of `no_newline_stmt`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| eager                       | Controls whether output not terminated by a newline causes execution of the SQL statement every time it is received, or accumulates such output until a newline is received. A value of 0 means that unterminated output is accumulated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |

### remove_output_to_sql

`remove_output_to_sql` deletes a specification created by `set_output_to_sql.` If no such specification exists, an error message is returned.

    FUNCTION remove_output_to_sql (id VARCHAR2) return VARCHAR2;

### enable_output_to_sql

`enable_output_to_sql` reenables a specification created by `set_output_to_sql` and subsequently disabled by `disable_output_to_sql.` If no such specification exists, an error message is returned. If the specification is not currently disabled, there is no change.

    FUNCTION enable_output_to_sql (id VARCHAR2) return VARCHAR2;

### disable_output_to_sql

`disable_output_to_sql` disables a specification created by `set_output_to_sql.` You can enable the specification by calling `enable_output_to_sql`. While disabled, the SQL statement prescribed by the specification is not executed. If no such specification exists, an error message is returned. If the specification is already disabled, there is no change.

    FUNCTION disable_output_to_sql (id VARCHAR2) return VARCHAR2;

### query_output_to_sql

`query_output_to_sql` returns a message describing a specification created by `set_output_to_sql.` If no such specification exists, then an error message is returned. Passing `null` to this function causes all existing specifications to be displayed.

    FUNCTION query_output_to_sql (id VARCHAR2) return VARCHAR2;

Another way of achieving control over the destination of output from Oracle JVM is to pass your Java output to an autonomous Java session. This provides a very general mechanism for propagating the output to various kinds of targets, such as disk files, sockets, and URLS. But, you must keep in mind that the Java session that processes the output is logically distinct from the main session, so that there are no other, unwanted interactions between them. To do this, PL/SQL package `DBMS_JAVA` provides the following functions:

- set_output_to_java

- remove_output_to_java

- enable_output_to_java

- disable_output_to_java

- query_output_to_java

- set_output_to_file

- remove_output_to_file

- enable_output_to_file

- disable_output_to_file

- query_output_to_file

### set_output_to_java

`set_output_to_java` defines a named output specification that gives an instruction for executing a Java method whenever output to the default `System.out` and `System.err` streams occurs. The Java method prescribed by the specification is executed in a separate VM context with separate Java session state from the rest of the session.

    FUNCTION set_output_to_java (id VARCHAR2,
    class_name VARCHAR2,
    class_schema VARCHAR2,
    method VARCHAR2,
    bindings VARCHAR2,
    no_newline_method VARCHAR2 default null,
    no_newline_bindings VARCHAR2 default null,
    newline_only_method VARCHAR2 default null,
    newline_only_bindings VARCHAR2 default null,
    maximum_line_segment_length NUMBER default 0,
    allow_replace NUMBER default 1,
    from_stdout NUMBER default 1,
    from_stderr NUMBER default 1,
    include_newlines NUMBER default 0,
    eager NUMBER default 0,
    initialization_statement VARCHAR2 default null,
    finalization_statement VARCHAR2 default null)return VARCHAR2;

Table 3-3 describes the arguments the `set_output_to_java` method takes.

Table 3-3 set_output_to_java Argument Summary

| Argument                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:-------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| class_name               | The name of the class defining one or more methods.                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| class_schema             | The schema in which the class is defined. A null value means the class is defined in the current schema, or PUBLIC.                                                                                                                                                                                                                                                                                                                                                                                          |
| method                   | The name of the method.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| bindings                 | A string that defines how the arguments to the method are bound. This is a string of tokens with the same syntax as `set_output_to_sql.` The position of a token in the string determines the position of the argument it describes. All arguments must be of type INT, except for those corresponding to the tokens ID or TEXT, which must be of type `java.lang.String`.                                                                                                                                   |
| no_newline_method        | An optional alternate method to execute when the output is not newline terminated.                                                                                                                                                                                                                                                                                                                                                                                                                           |
| newline_only_method      | An optional alternate method to execute when the output is a single newline.                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| initialization_statement | An optional SQL statement that is executed once per Java session prior to the first time the methods that receive output are executed. This statement is executed in same Java VM context as the output methods are executed. Typically such a statement is used to run a Java stored procedure that initializes conditions in the separate VM context so that the methods that receive output can function as intended. For example, such a procedure might open a stream that the output methods write to. |
| finalization_statement   | An optional SQL statement that is executed once when the output specification is about to be removed or the session is ending. Like the `initialization_statement,` this runs in the same JVM context as the methods that receive output. It runs only if the initialization method has run, or if there is no initialization method.                                                                                                                                                                        |

### remove_output_to_java

`remove_output_to_java` deletes a specification created by `set_output_to_java`. If no such specification exists, an error message is returned

    FUNCTION remove_output_to_java (id VARCHAR2) return VARCHAR2;

### enable_output_to_java

`enable_output_to_java` reenables a specification created by `set_output_to_java` and subsequently disabled by `disable_output_to_java.` If no such specification exists, an error message is returned. If the specification is not currently disabled, there is no change.

    FUNCTION enable_output_to_java (id VARCHAR2) return VARCHAR2;

### disable_output_to_java

`disable_output_to_java` disables a specification created by `set_output_to_java`. The specification may be reenabled by `enable_output_to_java.` While disabled, the SQL statement prescribed by the specification is not executed. If no such specification exists, an error message is returned. If the specification is already disabled, there is no change.

    FUNCTION disable_output_to_java (id VARCHAR2) return VARCHAR2;

### query_output_to_java

`query_output_to_java` returns a message describing a specification created by `set_output_to_java.` If no such specification exists, an error message is returned. Passing `null` to this function causes all existing specifications to be displayed.

    FUNCTION query_output_to_java (id VARCHAR2) return VARCHAR2;

### set_output_to_file

`set_output_to_file` defines a named output specification that constitutes an instruction to capture any output sent to the default `System.out` and `System.err` streams and append it to a specified file. This is implemented using a special case of `set_output_to_java.` The argument `file_path` specifies the path to the file to which to append the output. The arguments `allow_replace, from_stdout,` and `from_stderr` are all analogous to the arguments having the same name as in `set_output_to_sql.`

    FUNCTION set_output_to_file (id VARCHAR2,
    file_path VARCHAR2,
    allow_replace NUMBER default 1,
    from_stdout NUMBER default 1,
    from_stderr NUMBER default 1) return VARCHAR2;

### remove_output_to_file

This function is analogous to `remove_output_to_java`.

    FUNCTION remove_output_to_file (id VARCHAR2) return VARCHAR2;

### enable_output_to_file

This function is analogous to `enable_output_to_java.`

    FUNCTION enable_output_to_file (id VARCHAR2) return VARCHAR2;

### disable_output_to_file

This function is analogous to `disable_output_to_java.`

    FUNCTION disable_output_to_file (id VARCHAR2) return VARCHAR2;

### query_output_to_file

This function is analogous to `query_output_to_java.`

    FUNCTION query_output_to_file (id VARCHAR2) return VARCHAR2;

The following `DBMS_JAVA` functions control whether Java output appears in the `.trc` file:

- `PROCEDURE enable_output_to_trc;`

- `PROCEDURE disable_output_to_trc;`

- `FUNCTION query_output_to_trc return VARCHAR2;`

**Note:**

Prior to 11g release 1 (11.1), the fact that Java output appeared in the `.trc` file was not modifiable.

### Redirecting the output to SQL\*Plus Text Buffer

As in previous releases, you can use the `DBMS_JAVA` package procedure `SET_OUTPUT` to redirect output to the SQL\*Plus text buffer:

    SQL> SET SERVEROUTPUT ON
    SQL> CALL dbms_java.set_output(2000);

The minimum and default buffer size is 2,000 bytes and the maximum size is 1,000,000 bytes. In the following example, the buffer size is increased to 5,000 bytes:

    SQL> SET SERVEROUTPUT ON SIZE 5000
    SQL> CALL dbms_java.set_output(5000);

The output is displayed at the end of the call.
