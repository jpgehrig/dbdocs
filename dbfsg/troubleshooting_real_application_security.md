## D  Troubleshooting Oracle Database Real Application Security

This appendix contains:

- About Real Application Security Diagnostics

- About Event-Based Tracing of Real Application Security Components

- About Exception State Dump Information

- About Session Statistics

- Using Middle-Tier Tracing

### D.1 About Real Application Security Diagnostics

Real Application Security uses an integrated infrastructure that spans across back-end databases, application servers, and application instances. Real Application Security components include diagnostic capabilities that enable you to locate, diagnose, and resolve problems in a Real Application Security system.

Real Application Security diagnostics make use of the database Diagnostic Framework (DFW) available in Oracle Database 12c Release 1 (12.1) and later. Functionality diagnostics allow you to track, investigate, and resolve functionality failures. You can use exception state dumps, event-based tracing, or default tracing to study and resolve functionality issues. Performance diagnostics enable you to identify and resolve performance issues.

The following sections discuss functionality and performance diagnostic techniques used in Real Application Security systems:

- About Using Validation APIs

- How to Check Which ACLs Are Associated with a Row for the Current User

- How to Find If a Privilege Is Granted in an ACL to a User

- About Exception State Dumps

- About Event-Based Tracing

- About In-Memory Tracing

- About Statistics

#### D.1.1 About Using Validation APIs

You should always validate objects after they are created. This includes objects, such as principals, security classes, ACLs, data security policies, and namespaces. You can also validate all these objects that exist in a workspace in a single operation. The `XS_DIAG` package includes subprograms that you can use to diagnose potential problems in any of these created objects. See "[XS_DIAG Package](XS_DIAG-package.md)" for more information. These packages are briefly described in the following table with links to each validation subprogram where examples of their usage are shown.

Table D-1 Summary of XS_DIAG Subprograms

| Subprogram                                                 | Description                                                                                        |
|:-----------------------------------------------------------|:---------------------------------------------------------------------------------------------------|
| [VALIDATE_PRINCIPAL Function](XS_DIAG-package.md)          | Validates the principal.                                                                           |
| [VALIDATE_SECURITY_CLASS Function](XS_DIAG-package.md)     | Validates the security class.                                                                      |
| [VALIDATE_ACL Function](XS_DIAG-package.md)                | Validates the ACL.                                                                                 |
| [VALIDATE_DATA_SECURITY Function](XS_DIAG-package.md)      | Validates the data security policy or validates the data security policy against a specific table. |
| [VALIDATE_NAMESPACE_TEMPLATE Function](XS_DIAG-package.md) | Validates the namespace template.                                                                  |
| [VALIDATE_WORKSPACE Function](XS_DIAG-package.md)          | Validates an entire workspace.                                                                     |

#### D.1.2 How to Check Which ACLs Are Associated with a Row for the Current User

To find which ACLs are associated with a particular row for the current user, use the `ORA_GET_ACLIDS` function. The `ORA_GET_ACLIDS` function returns a list of ACL IDS associated with a row instance of data security policy enabled tables for the current application user. If access to the current row has been granted, this function captures all ACL identifiers that are associated with the matching data realm constraints. See "[ORA_GET_ACLIDS Function](real-application-security-sql-functions.md)" for reference information and "[About Checking ACLs for a Privilege](configuring-application-privileges-and-access-contol-lists.md)" for tutorial information.

#### D.1.3 How to Find If a Privilege Is Granted in an ACL to a User

To find if a privilege is granted in an ACL, use the `ORA_CHECK_ACL` function. The `ORA_CHECKACL` function checks whether an application user has the queried application privileges according to a list of ACLs. If the specified application privileges have been granted to the application user, `ORA_CHECKACL` returns `1`. If they are not granted to the application user, then it returns `0`. See "[ORA_CHECK_ACL Function](real-application-security-sql-functions.md)" for reference information and "[About Checking ACLs for a Privilege](configuring-application-privileges-and-access-contol-lists.md)" for tutorial information.

To list the ACLIDs associated with each row of a table, for example, the `EMPLOYEE` table, the user can use the following query:

    select ORA_GET_ACLIDS(emp) from EMPLOYEE emp;

To list the result if a privilege, for example `SELECT`, is granted for each row of the `EMPLOYEE` table, the user can perform the following query:

    select ORA_CHECK_ACL(ORA_GET_ACLIDS(emp), 'SELECT') from EMPLOYEE emp;

#### D.1.4 About Exception State Dumps

When an exception occurs, the state information for Real Application Security components is dumped into trace files. Exception state dumps are analogous to crash site evidence for a plane crash.

A failure, like an internal error or server crash, causes a Diagnostic Data Extraction (DDE) routine to be invoked for each component. This dumps the current system, session, and process state information into trace files. You can later analyze the cause of failure using the state information dumped into trace files.

#### D.1.5 About Event-Based Tracing

Event-based tracing can be used to track events related to specific Real Application Security components. Event-based tracing helps in tracing the events that led up to a failure. For example, event number 46148 is used to trace application session events, such as `createSession` and `attachSession`.

#### D.1.6 About In-Memory Tracing

In-memory tracing is a proactive tracing mechanism that is used do diagnose intermittent and hard to replicate errors. The in-memory tracing mechanism records component state changes and events in memory buffers. This is dumped to a trace file when a failure occurs. In-memory tracing is analogous to black box data that is used for plane crash investigation.

#### D.1.7 About Statistics

Real Application Security component statistics help identify performance issues in a Real Application Security system. Statistics include key data like the number of session create operations, principal invalidations, role-enabling operations, and so on.

### D.2 About Event-Based Tracing of Real Application Security Components

Event-based tracing can be used to track events related to specific Real Application Security components. Table D-2 lists the events assigned to Real Application Security components.

Table D-2 Real Application Security Components and Events

| Real Application Security Components      | Event (Oracle Error \#) |
|:------------------------------------------|:------------------------|
| Application Sessions<br>(`XSSESSION)`     | 46148                   |
| Application Principals<br>(`XSPRINCIPAL`) | 46150                   |
| Security Classes<br>(`XSSECCLASS`)        | 46149                   |
| ACLs<br>`(XSACL)`                         | 46110                   |
| Data Security<br>(`XSXDS`)                | 46049                   |
| Mid-Tier Caches<br>(`XS_MIDTIER`)         | 46151                   |
| Data Security VPD Rewrite<br>(`XSVPD`)    | 10730                   |

The following sections describe event-based tracing for individual Real Application Security components:

- About Application Sessions (XSSESSION) Event-Based Tracing

- About Application Principals (XSPRINCIPAL) Event-Based Tracing

- About Security Classes (XSSECCLASS) Event-Based Tracing

- About ACL (XSACL) Event-Based Tracing

- About Data Security (XSXDS and XSVPD) Event-Based Tracing

#### D.2.1 About Application Sessions (XSSESSION) Event-Based Tracing

Use the following `SQL` statement to enable event-based tracing for the `XSSESSION` component:

    ALTER SESSION SET EVENTS '46148 trace name context forever, level="1", level="2", level="3"';

Here, `46148` is the Oracle Database error number associated with `XSSESSION` events. You can set a trace level of `1` (`low`), `2` (`medium`), or `3` (`high`). Table D-3 describes the trace levels.

Alternatively, you can use the following statement:

    ALTER SESSION SET EVENTS 'TRACE [XSSESSION] disk=[low, medium, high]'

You can find the location of this trace file by using the following SQL statement:

    SHOW PARAMETER USER_DUMP_DEST;

Table D-3 shows the `XSSESSION` trace contents for each trace level.

Table D-3 XSSESSION Trace Contents

| Event             | Trace Level 1 (Low)                                                                                                                         | Trace Level 2 (Medium)                                                                                                                                                                             | Trace Level 3 (High)                                                                                              |
|:------------------|:--------------------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------|
| `createSession`   | Includes the following:<br>• User name<br>• Session Id for the session                                                                      | Includes the following in addition to trace level 1 items:<br>• User GUID<br>• Session attributes such as create time, last authentication time, global variable namespace, and cookie information | Same as level 2                                                                                                   |
| `attachSession`   | Includes the following:<br>• User name<br>• Session Id for the session                                                                      | Includes the following in addition to trace level 1 items:<br>• Roles                                                                                                                              | Includes the following in addition to trace level 1 and 2 items:<br>• Application namespace with attribute values |
| `detachSession`   | Includes the following:<br>• User name<br>• Session Id for the session before detaching                                                     | Same as level 1                                                                                                                                                                                    | Same as levels 1 and 2                                                                                            |
| `createNamespace` | Includes the following:<br>• User name<br>• Session Id<br>• Application namespace with attribute values                                     | Includes the following in addition to trace level 1 items:<br>• Session attributes such as create time, last authentication time, global variable namespace, and cookie information                | Includes the following in addition to trace level 1 and 2 items:<br>• Namespace handler                           |
| `switchUser`      | Includes the following:<br>• User name<br>• Session Id for the session                                                                      | Includes the following in addition to trace level 1 items:<br>• Roles                                                                                                                              | Includes the following in addition to trace level 1 and 2 items:<br>• Application namespace with attribute values |
| `assignUser`      | Includes the following:<br>• User name<br>• Session Id for the session                                                                      | Includes the following in addition to trace level 1 items:<br>• Roles                                                                                                                              | Includes the following in addition to trace level 1 and 2 items:<br>• Application namespace with attribute values |
| `setAttribute`    | Includes the following:<br>• Namespace name<br>• Name and value of the given attribute before and after the `setAttribute` operation        | Same as level 1                                                                                                                                                                                    | Same as levels 1 and 2                                                                                            |
| `deleteAttribute` | Includes the following:<br>• Namespace name and<br>• Name and value of the given attribute before and after the `deleteAttribute` operation | Same as level 1                                                                                                                                                                                    | Same as levels 1 and 2                                                                                            |

In addition to the preceding event, you can use the named event, `xs_session_state` to dump the current state of application sessions. Use the following SQL statement to enable tracing for the `xs_session_state` event:

    ALTER SESSION SET EVENTS 'immediate eventdump(xs_session_state)';

The event dump contains information on all session attributes in the User Global Area (UGA) memory, such as session Id, user name, create time, last authentication time, global variable namespace, and so on. The dump does not contain information on secure items such as passwords.

#### D.2.2 About Application Principals (XSPRINCIPAL) Event-Based Tracing

Use the following `SQL` statement to enable event-based tracing for the `XSPRINCIPAL` component:

    ALTER SESSION SET EVENTS '46150 trace name context forever, level="1", level="2", level="3"';

Here, `46150` is the Oracle Database error number associated with `XSPRINCIPAL` events. You can set a trace level of `1` (`low`), `2` (`medium`), or `3` (`high`). Table D-4 describes the trace levels.

Alternatively, you can use the following statement:

    ALTER SESSION SET EVENTS 'TRACE [XSPRINCIPAL] disk=[low, medium, high]';

You can find the location of this trace file by using the following SQL statement:

    SHOW PARAMETER USER_DUMP_DEST;

Table D-4 shows the `XSPRINCIPAL` trace contents for each trace level.

Table D-4 XSPRINCIPAL Trace Contents

| Event               | Trace Level 1 (Low)                                                                           | Trace Level 2 (Medium)                                                                                                                                                                                                                 | Trace Level 3 (High)   |
|:--------------------|:----------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------|
| Enable Role         | Includes the following:<br>• User name<br>• Session Id for the session                        | Includes the following in addition to trace level 1 items:<br>• If the Enable Role operation fails, then the cause is logged. For example, the operation may fail if the role does not exist or the user has not been granted the role | Same as levels 1 and 2 |
| Disable Role        | Includes the following:<br>• All user enabled roles in the session after the role is disabled | Includes the following in addition to trace level 1 items:<br>• If the Disable Role operation fails, then the cause is logged.                                                                                                         | Same as levels 1 and 2 |
| Role Graph Traverse | Includes the following:<br>• User name<br>• Session Id for the session                        | Same as level 1                                                                                                                                                                                                                        | Same as levels 1 and 2 |

#### D.2.3 About Security Classes (XSSECCLASS) Event-Based Tracing

Use the following `SQL` statement to enable event-based tracing for the `XSSECCLASS` component:

    ALTER SESSION SET EVENTS '46149 trace name context forever, level="1", level="2", level="3"';

Here, `46149` is the Oracle Database error number associated with `XSSECCLASS` events. You can set a trace level of `1` (`low`), `2` (`medium`), or `3` (`high`).

Alternatively, you can use the following statement:

    ALTER SESSION SET EVENTS 'TRACE [XSSECCLASS] disk=[low, medium, high]';

You can find the location of this trace file by using the following SQL statement:

    SHOW PARAMETER USER_DUMP_DEST;

The trace information includes the following:

- Content from the Security Class document, such as parent classes, child classes, privileges, and aggregate privileges

- For security class deletions, it includes information on parent classes that require invalidation from the cache

- Exception related information, such as security class validation errors

#### D.2.4 About ACL (XSACL) Event-Based Tracing

Use the following `SQL` statement to enable event-based tracing for the `XSACL` component:

    ALTER SESSION SET EVENTS '46110 trace name context forever, level="1", level="2", level="3"';

Here, `46110` is the Oracle Database error number associated with `XSACL` events. You can set a trace level of `1` (`low`), `2` (`medium`), or `3` (`high`).

Alternatively, you can use the following statement:

    ALTER SESSION SET EVENTS 'TRACE [XSACL] disk=[low, medium, high]';

You can find the location of this trace file by using the following SQL statement:

    SHOW PARAMETER USER_DUMP_DEST;

Table D-5 shows the `XSACL` trace contents for each trace level.

Table D-5 XSACL Trace Contents

| Event                        | Trace Level 1 (Low)                                            | Trace Level 2 (Medium)                                                                               | Trace Level 3 (High)   |
|:-----------------------------|:---------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------|:-----------------------|
| Check privilege against ACLs | Includes the following:<br>• ACL results during cursor sharing | Includes the following in addition to trace level 1 items:<br>• ACL evaluation including ACL loading | Same as levels 1 and 2 |

#### D.2.5 About Data Security (XSXDS and XSVPD) Event-Based Tracing

Use the following `SQL` statement to enable event-based tracing for the `XSXDS` component:

    ALTER SESSION SET EVENTS '46049 trace name context forever, level="1", level="2", level="3"';

Here, `46049` is the Oracle Database error number associated with `XSXDS` events. You can set a trace level of `1` (`low`), `2` (`medium`), or `3` (`high`). Table D-6 describes the trace levels.

Alternatively, you can use the following statement:

    ALTER SESSION SET EVENTS 'TRACE [XSXDS] disk=[low, medium, high]';

You can find the location of this trace file by using the following SQL statement:

    SHOW PARAMETER USER_DUMP_DEST;

Table D-6 shows the `XSXDS` trace contents for each trace level.

Table D-6 XSXDS Trace Contents

| Event                                                             | Trace Level 1 (Low)                                                                              | Trace Level 2 (Medium)                                                                                | Trace Level 3 (High)   |
|:------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------|:-----------------------|
| Data Security Document (DSD) loaded into System Global Area (SGA) | Includes the following:<br>• Security data realm constraint rules with resolved parameter values | Includes the following in addition to trace level 1 items:<br>• Access Control List (ACL) identifiers | Same as levels 1 and 2 |

Use the following `SQL` statement to enable event-based tracing for the `XSVPD` component:

    ALTER SESSION SET EVENTS '10730 trace name context forever level [1, 2, 3]';

Here, 10730 is the Oracle Database error number associated with `XSVPD` events. You can set a trace level of `1` (`low`), `2` (`medium`), or `3` (`high`). Table D-6 describes the trace levels.

Alternatively, you can use the following statement:

    ALTER SESSION SET EVENTS 'TRACE [XSVPD] disk=[low, medium, high]';

Table D-6 shows the `XSVPD` trace contents for each trace level.

Table D-7 XSVPD Trace Contents

| Event                                                                                                                                         | Trace Level 1 (Low)                                                                                                                                                                                                                     | Trace Level 2 (Medium)                                                                                                                                          | Trace Level 3 (High)                                                                                                                                                                        |
|:----------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| • Data Security Document (DSD) loaded into System Global Area (SGA)<br>• All subsequent SQL statements issued in the current database session | Includes the following:<br>• VPD view of XDS enabled objects during hard-parse, soft-parse, or SQL statement parsing<br>• Data realm constraint rules with resolved parameter values, their corresponding ACL paths and ACL identifiers | Includes the following in addition to trace level 1 items:<br>• Current application session user name and enabled roles when the SQL statement is parsed or run | Includes the following in addition to trace level 1 items:<br>• Contents of all ACLs associated with data realm constraints, which are associated with the XDS enabled objects in the query |

### D.3 About Exception State Dump Information

When an exception occurs, the state information for Real Application Security components is dumped into trace files. Table D-8 describes the information dumped for individual Real Application Security components:

Table D-8 Real Application Security Components and First-Failure Dump Information

| Real Application Security Component | Exception Related Information                                                                                                                                                                                                                                                |
|:------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `XSSESSION`                         | • Application session state information                                                                                                                                                                                                                                      |
| `XSPRINCIPAL`                       | • Application session role lists (all roles, enabled roles, disabled roles, and database roles of the application session)<br>• Role Graph hash table of the system<br>• User hash table with direct roles granted to the users in the system<br>• Principal row cache state |

### D.4 About Session Statistics

Real Application Security component statistics help identify performance issues in a Real Application Security system. Table D-9 describes the statistics collected for individual Real Application Security components.

Table D-9 Real Application Security Components and Performance Statistics

| Real Application Security Component | Performance Statistics Collected                                                                                                                                            |
|:------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `XSSESSION`                         | • Number of application sessions created<br>• Number of application sessions attached and detached<br>• Number of namespaces created<br>• Number of user callbacks executed |
| `XSPRINCIPAL`                       | • Number of roles enabled/disabled<br>• Number of principal cache misses<br>• Number of principal invalidations                                                             |
| Mid-tier caches                     | • Number of session cache synchronizations<br>• Number of principal cache synchronizations<br>• Number of security class cache synchronizations                             |

### D.5 Using Middle-Tier Tracing

Middle-tier tracing uses the package `oracle.security.xs`. It can be done as follows:

1.  Specify logging options in a property file. For example,
        handlers= java.util.logging.ConsoleHandler
        .level= SEVERE
        java.util.logging.ConsoleHandler.level = FINEST
        java.util.logging.ConsoleHandler.formatter = java.util.logging.SimpleFormatter
        oracle.security.xs.level = FINEST
2.  Apply the preceding configuration during JVM start up.
        java -Djava.util.logging.config.file=logging.properties

    The log output will be generated to the handlers (file, console) specified in the configuration.

Real Application Security user can use mid-tier java API for authentication, authorization, session management, and so forth. In case the user needs to debug on interfacing with mid-tier API, trace can be turned on. The trace can show basic call stacks, function involved, time used, parameters passed, returning value, and so forth.
