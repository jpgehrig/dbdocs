A key part of migrating non-Oracle database applications to an Oracle Database requires converting non-Oracle SQL statements to SQL statements that can be processed by an Oracle Database. SQL conversion is generally a manual and laborious process. To minimize the effort, Oracle Database 12c introduces SQL Translation Framework which takes non-Oracle SQL statements from client applications and then translates them at run-time for the Oracle Database to execute.

The SQL Translation Framework can be used to map non-Oracle stored procedure to Oracle stored procedures to ensure successful execution of those stored procedures when migrating to Oracle Database.

Currently, SQL Translation Framework is available for Sybase Adaptive Server Enterprise and Microsoft SQL Server. There is limited support for IBM DB2.

**Note:**

SQL Translation Framework is only supported by ODP.NET, Unmanaged Driver. ODP.NET, Managed Driver and ODP.NET Core do not support this feature.

### The SQL Translation Profile

The SQL Translation Profile is a database object that contains the set of captured non-Oracle SQL statements, and their translations or translation errors. The SQL Translation Profile is used to review, approve, and modify translations. A profile is associated to a single translator. However, a translator can be used in one or more SQL Translation Profiles. Typically, there is one SQL Translation Profile per application, otherwise applications can share translated queries. You can export profiles among various databases.

1.  Configuring the SQL Translation Profile Name

    The default translation profile name for SQL Translation Framework can be configured through the `app/web/machine` .NET configuration file. If configured, connections, by default will automatically be set to the specified profile when the connection is initially created.

2.  Changing the SQL Translation Profile Name

    ODP.NET supports setting the profile name through the .NET config file, logon trigger, or database service. ODP.NET does not support using `ALTER SESSION` from an application to set the profile name.

3.  Forcing Translation

    Applications are strictly prohibited to execute the following SQL which forces translation of all SQL's on the database:

        ALTER SESSION SET events = '10601 trace name context forever, level 32'

4.  Connection Related Error Mapping

    Connection Related Error Mapping can be configured through the .NET configuration file. Please note that this error mapping strictly applies to errors which could be thrown before the connection is successfully established. Once the database connection is established successfully, then these error mapping will be completely ignored and further error translation will be provided through the error mapping configured in the database.

    The rules to choose an error mapping section in the configuration file are as follows:

    1.  ODP.NET uses the error mapping section which matches the configured `userId`, `dataSource`, and profile, where `userId` and `dataSource` matches the corresponding values in the connection string and profile matches the `defaultProfile` configuration setting.

    2.  If no error mapping section is found from 4.a.), then ODP.NET uses the error mapping section which matches the `userId`, `dataSource`, and profile similar to 4.a.), but with the profile that matches with the `defaultErrorMappingProfile` configuration setting.

    3.  If still no error mapping section is found, then ODP.NET uses the global mapping, that is, `<ErrorMapping profile="*">`, if configured.

5.  Stored Procedure Mapping.

    Application must map their native stored procedure names to the corresponding Oracle stored procedure names on the translation profile in the database. The following procedure can be used to setup the mapping in the database.

        DBMS_SQL_TRANSLATOR.REGISTER_SQL_TRANSLATION(
            PROFILE_NAME    VARCHAR2    IN
            SQL_TEXT        CLOB        IN
            TRANSLATED_TEXT CLOB        IN     DEFAULT
            ENABLE          BOOLEAN     IN     DEFAULT)

    Example of stored procedure mapping:

        DBMS_SQL_TRANSLATOR.REGISTER_SQL_TRANSLATION('profile_name',
         'native_sp_name',
         'oracle_sp_name');

**See Also:**

Chapter 2, SQL Translation Framework Overview and Architecture, of the [Oracle Database Migration Guide](../drdaa/SQL-translation-framework-overview.md) for more information.
