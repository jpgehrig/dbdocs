Prior to 11g release 1 (11.1), Java session state was single-tier, which included all values associated with running Java, such as System property values and static variable values, the set of classes loaded during the session and so on. The duration of this state used to start with the first invocation of a Java method in the RDBMS session and it used to last till JVM exited, either due to a call to `java.lang.System.exit` or similar `OracleRuntime` methods, an uncaught exception, a fatal error, or the end of the RDBMS session. This required modifying Java code and also failed to fully complete the termination of the session before the end of the RDBMS call. This made it impossible to start a new Java session within the same call.

Starting with 11g release 1 (11.1), Java session state is split into two tiers. One tier has a longer duration and it encompasses the duration of the other tier. The duration of the shorter tier is the same as before, that is, it starts when a Java method is invoked and ends when JVM exits. The duration of the longer tier starts when a Java method is invoked in the RDBMS session for the first time. This session lasts until the RDBMS session ends or the session is explicitly terminated by a call to the function `dbms_java.endsession_and_related_state`. This is addressed by the addition of the following two PL/SQL functions to the `DBMS_JAVA` package, which account for the two kinds of Java session duration:

- `FUNCTION endsession RETURN VARCHAR2;`

  This function clears any Java session state remaining from previous execution of Java in the current RDBMS session. The return value is a message indicating the action taken.

- `FUNCTION endsession_and_related_state RETURN VARCHAR2;`

  This function clears any Java session state remaining from previous execution of Java in the current RDBMS session and all supporting data related to running Java, such as property settings and output specifications. The return value is a message indicating the action taken.

Most of the values associated with running Java remain in the shorter tier. The values that can be useful for multiple invocations of JVM have been moved to the longer tier. For example, the system property values established by `dbms_java.set_property` and the output redirection specifications.

**Related Topics**

- [About Setting System Properties](setting-system-properties.md)
- [About Redirecting Output on the Server](redirecting-server-output.md)
