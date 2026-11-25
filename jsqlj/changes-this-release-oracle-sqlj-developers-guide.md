### Deprecated Features

The following feature is deprecated in this release, and may be desupported in a later release:

oracle.sql.\* Package

Starting Oracle Database 12c Release 2 (12.2), the oracle.sql.\* package is deprecated.

### Desupported Features

The following features are no longer supported by Oracle:

Extended Datatype Support (EDS)

The Extended Datatype Support (EDS) feature is desupported in Oracle Database 19c. All Data types that the EDS feature supported are now supported natively by both Logical Standby and Oracle GoldenGate.

The Extended Datatype Support (EDS) feature provides a mechanism for logical standbys to support certain Oracle data types that lack native redo-based support. For example, EDS was used to replicate tables with a SDO_GEOMETRY column. However, starting with Oracle Database 12c Release 2 (12.2), there are no EDS-supported Oracle data types that are not supported natively, either by Logical standby, or by Oracle GoldenGate. This feature is desupported with Oracle Database 19c (19.1).

SQLJ in the Server

Starting with Oracle Database 12c Release 2 (12.2), Oracle does not support server-side SQLJ code.

Oracle supports using client-side SQLJ. However, Oracle does not support the use of server-side SQLJ, including running stored procedures, functions, and triggers in the database environment.

JPublisher

All Oracle JPublisher features are desupported and unavailable in Oracle Database 12c Release 2 (12.2.0.1). Oracle recommends that you use the alternatives listed here:

- To continue to use Web service callouts, Oracle recommends that you use the Oracle JVM Web Services Callout utility, which is a replacement for the Web Services Callout utility.

- To replace other JPublisher automation capabilities, including mapping user-defined SQL types or SQL types, wrapping PL/SQL packages and similar capabilities, Oracle recommends that developers use explicit steps, such as precompiling code with SQLJ precompiler, building Java STRUCT classes, or using other prestructured options.

**See Also:**

My Oracle Support Note 1937939.1 for more information about JDeveloper deprecation and desupport:

<https://support.oracle.com/CSP/main/article?cmd=show&type=NOT&id=1937939.1>

**See Also:**

[Oracle Database Upgrade Guide](../upgrd/oracle-database-changes-deprecations-desupports.md) to see a list of all desupported features in this release of Oracle Database
