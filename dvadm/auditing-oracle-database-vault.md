You can audit activities in Oracle Database Vault, such as changes to policy configurations.

- About Auditing in Oracle Database Vault
  All activities in Oracle Database Vault can be audited, including Database Vault administrator activities.
- Protection of the Unified Audit Trail in an Oracle Database Vault Environment
  By default, `AUDSYS` schema, which contains the unified audit trail, is not protected by a realm.
- Oracle Database Vault Specific Audit Events
  Oracle Database Vault audit events track activities such as whether an action attempted on a realm was successful.
- Archiving and Purging the Oracle Database Vault Audit Trail
  If you have not migrated to unified auditing, you should periodically archive and purge the Oracle Database Vault audit trail.
- Oracle Database Audit Settings Created for Oracle Database Vault
  When you install Oracle Database Vault, it creates several `AUDIT` settings in the database.

### A.1 About Auditing in Oracle Database Vault

All activities in Oracle Database Vault can be audited, including Database Vault administrator activities.

Optionally, you can audit individual policies that you create for realms, rule sets, and factors. The audit indicates if the user's action succeeded (that is, the policy enabled the user to accomplish a task) or if the user's action failed (the policy was violated). These actions are written to audit logs, whose contents you can find either by querying the appropriate data dictionary views, or running the reports described in [Oracle Database Vault Reports](oracle-database-vault-reports.md).

All configuration changes made to Database Vault are mandatorily audited, including actions of unprivileged users who attempt to modify Database Vault policies.

When you install a new database and configure it to use Oracle Database Vault, then by default it uses a mixed-mode environment, that is, a mixture of unified auditing and pre-migrated auditing. If you have upgraded from previous release, then Database Vault uses the auditing that was available from that release.

Before you migrate to a full unified auditing environment, you can create audit policies as follows:

- Using the Database Vault APIs: That is, you use the `DBMS_MACADM` PL/SQL package or the Database Vault pages in Enterprise Manager. In this case, the audit records are written to the Database Vault audit trail, which is stored in the `DVSYS.AUDIT_TRAIL$` table. You can query the `DVSYS.DV$CONFIGURATION_AUDIT` and `DVSYS.DV$ENFORCEMENT_AUDIT` views for these audit records.

- Using the unified audit policy SQL statements: These statements are the `CREATE AUDIT POLICY`, `ALTER AUDIT POLICY`, `DROP AUDIT POLICY`, `AUDIT`, and `NO AUDIT` statements. They are written to the unified audit trail, which is captured by the `UNIFIED_AUDIT_TRAIL`, `AUDSYS.DV$CONFIGURATION_AUDIT`, and `AUDSYS.DV$ENFORCEMENT_AUDIT` data dictionary views.

When you migrate to unified auditing, then the auditing features in the Database Vault APIs are no longer effective. You should archive and purge these audit records, as described in Archiving and Purging the Oracle Database Vault Audit Trail. From then on, you can manage Database Vault audit policies through the unified audit policy PL/SQL statements.

Except where noted, the remaining sections of this chapter describe how Database Vault auditing works in a non-unified or mixed mode auditing environment.

**See Also:**

- [Oracle Database Security Guide](../dbseg/configuring-audit-policies.md) for information about how unified auditing works in Oracle Database Vault and how to create unified audit policies

- Oracle Database Vault Audit Trail Record Format

- The following data dictionary views, which are specific to Database Vault unified auditing:

  [DVSYS.DV\$CONFIGURATION_AUDIT View](oracle-database-vault-data-dictionary-views.md)

  [DVSYS.DV\$ENFORCEMENT_AUDIT View](oracle-database-vault-data-dictionary-views.md)

- [Oracle Database Upgrade Guide](../spucs/recommended-and-best-practices-complete-upgrading-oracle-database.md) to migrate your database to unified auditing

**Parent topic:** Auditing Oracle Database Vault

### A.2 Protection of the Unified Audit Trail in an Oracle Database Vault Environment

By default, `AUDSYS` schema, which contains the unified audit trail, is not protected by a realm.

To better protect the unified audit trail, Oracle recommends that you do the following:

- Create a regular (not mandatory) realm around the `AUDSYS` schema so that only authorized users (that is, users who have been granted the `AUDIT_ADMIN` and `AUDIT_VIEWER` roles) can query the unified audit trail views and use the `DBMS_AUDIT_MGMT` PL/SQL package to manage the audit trail. This realm will prevent highly privileged users, including `SYS`, from performing these actions until they are added to that realm's authorization list.
- Create a command rule for the `CREATE AUDIT POLICY`, `ALTER AUDIT POLICY`, and `DROP AUDIT POLICY` SQL statements so that only authorized users can execute these statements.

**Related Topics**

- [Creating a Realm](configuring-realms.md)
- [Creating a Command Rule](configuring-command-rules.md)

**Parent topic:** Auditing Oracle Database Vault

### A.3 Oracle Database Vault Specific Audit Events

Oracle Database Vault audit events track activities such as whether an action attempted on a realm was successful.

- Oracle Database Vault Policy Audit Events
  Oracle Database Vault uses audit events to track configuration activities.
- Oracle Database Vault Audit Trail Record Format
  If you do not use unified auditing, then Oracle Database Vault writes audit records to the `DVSYS.AUDIT_TRAIL$` table.

**Parent topic:** Auditing Oracle Database Vault

#### A.3.1 Oracle Database Vault Policy Audit Events

Oracle Database Vault uses audit events to track configuration activities.

These activities are as follows:

- Realm Audit. You can audit both successful and failed actions, based on the auditing option that you set when you created the realm. The exception to this is actions performed by the schema owner.

- Rule Set Audit. Audits the rule set processing results. You can audit both successful and failed processing. Realm authorizations can be managed using rule sets. You can audit the rule set processing results. Factor assignments and secure application roles audits can be managed using a rule set.

- Factor Audit. You can audit both successful and failed factor processing. For failed factor processing, you can audit on all or any of the following events: Retrieval Error, Retrieval Null, Validation Error, Validation False, Trust Level Null, or Trust Level Less Than Zero.

- Oracle Label Security Session Initialization Failed. Audits instances where the Oracle Label Security session fails to initialize.

- Oracle Label Security Attempt to Upgrade Session Label Failed. Audits instances where the Oracle Label Security component prevents a session from setting a label that exceeds the maximum session label.

**Related Topics**

- [Setting Audit Options for a Factor](configuring-factors.md)
- [About Realm Authorization](configuring-realms.md)
- [Oracle Database Vault Reports](oracle-database-vault-reports.md)

**Parent topic:** Oracle Database Vault Specific Audit Events

#### A.3.2 Oracle Database Vault Audit Trail Record Format

If you do not use unified auditing, then Oracle Database Vault writes audit records to the `DVSYS.AUDIT_TRAIL$` table.

These audit records are not part of the Oracle Database audit trail, and how auditing is enabled in the database has no effect how Oracle Database Vault collects its audit data in the `DVSYS.AUDIT_TRAIL$` table. In fact, even if auditing has been disabled in Oracle Database, then the Oracle Database Vault audit functionality continues to write to the `DVSYS.AUDIT_TRAIL$` table.

Users who have been granted the `DV_OWNER`, `DV_ADMIN`, `DV_SECANALYST` or `DV_MONITOR` role can directly query the `DVYS.AUDIT_TRAIL$` table.

Table A-1 describes the format of the audit trail, which you must understand if you plan to create custom reports that use the `DVSYS.AUDIT_TRAIL$` table.

Table A-1 Oracle Database Vault Audit Trail Format

| Column               | Datatype                      | Null       | Description                                                                                                                                                                                                                              |
|:---------------------|:------------------------------|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ID#`                | `NUMBER`                      | `NOT NULL` | Numeric identifier for the audit record                                                                                                                                                                                                  |
| `OS_USERNAME`        | `VARCHAR2(255)`               | `NULL`     | Operating system login user name of the user whose actions were audited                                                                                                                                                                  |
| `USERNAME`           | `VARCHAR2(30)`                | `NULL`     | Name of the database user whose actions were audited                                                                                                                                                                                     |
| `USERHOST`           | `VARCHAR2(128)`               | `NULL`     | Client computer name                                                                                                                                                                                                                     |
| `TERMINAL`           | `VARCHAR2(255)`               | `NULL`     | Identifier for the user's terminal                                                                                                                                                                                                       |
| `TIMESTAMP`          | `DATE`                        | `NULL`     | Date and time of creation of the audit trail entry (in the local database session time zone)                                                                                                                                             |
| `OWNER`              | `VARCHAR2(30)`                | `NULL`     | Creator of the object affected by the action, always `DVSYS` (because `DVSYS` is where objects are created)                                                                                                                              |
| `OBJ_NAME`           | `VARCHAR2(128)`               | `NULL`     | Name of the object affected by the action. Expected values are:<br>• `ROLE$`<br>• `REALM$`<br>• `CODE$`<br>• `FACTOR$`                                                                                                                   |
| `ACTION`             | `NUMBER`                      | `NOT NULL` | Numeric action type code. The corresponding name of the action type is in the `ACTION_NAME` column. See [Table 24-3](oracle-database-vault-data-dictionary-views.md) for a list of the expected `ACTION` and `ACTION_NAME` values.       |
| `ACTION_NAME`        | `VARCHAR2(128)`               | `NULL`     | Name of the action type corresponding to the numeric code in the `ACTION` column                                                                                                                                                         |
| `ACTION_OBJECT_ID`   | `NUMBER`                      | `NULL`     | The unique identifier of the record in the table specified under `OBJ_NAME`. For realms, this field contains a list of comma-separated values of all realm IDs that have the Audit on Failure audit option.                              |
| `ACTION_OBJECT_NAME` | `VARCHAR2(128)`               | `NULL`     | The unique name or natural key of the record in the table specified under `OBJ_NAME`. For realms, this field contains a list of comma-separated values of all realm names that have the Audit on Failure audit option.                   |
| `ACTION_COMMAND`     | `VARCHAR2(4000)`              | `NULL`     | The SQL text of the command procedure that was executed that resulted in the audit event being triggered                                                                                                                                 |
| `AUDIT_OPTION`       | `VARCHAR2(4000)`              | `NULL`     | The labels for all audit options specified in the record that resulted in the audit event being triggered. For example, a factor set operation that is supposed to audit on get failure and get `NULL` would indicate these two options. |
| `RULE_SET_ID`        | `NUMBER`                      | `NULL`     | The unique identifier of the rule set that was executing and caused the audit event to trigger                                                                                                                                           |
| `RULE_SET_NAME`      | `VARCHAR2(30)`                | `NULL`     | The unique name of the rule set that was executing and caused the audit event to trigger                                                                                                                                                 |
| `RULE_ID`            | `NUMBER`                      | `NULL`     | Not used                                                                                                                                                                                                                                 |
| `RULE_NAME`          | `VARCHAR2(30)`                | `NULL`     | Not used                                                                                                                                                                                                                                 |
| `FACTOR_CONTEXT`     | `VARCHAR2(4000)`              | `NULL`     | An XML document that contains all of the factor identifiers for the current session at the point when the audit event was triggered                                                                                                      |
| `COMMENT_TEXT`       | `VARCHAR2(4000)`              | `NULL`     | Text comment on the audit trail entry, providing more information about the statement audited                                                                                                                                            |
| `SESSIONID`          | `NUMBER`                      | `NOT NULL` | Numeric identifier for each Oracle session                                                                                                                                                                                               |
| `ENTRYID`            | `NUMBER`                      | `NOT NULL` | Same as the value in the `ID#` column                                                                                                                                                                                                    |
| `STATEMENTID`        | `NUMBER`                      | `NOT NULL` | Numeric identifier for the statement invoked that caused the audit event to be generated. This is empty for most Oracle Database Vault events.                                                                                           |
| `RETURNCODE`         | `NUMBER`                      | `NOT NULL` | Oracle error code generated by the action. The error code for a statement or procedure invoked that caused the audit event to be generated. This is empty for most Oracle Database Vault events.                                         |
| `EXTENDED_TIMESTAMP` | `TIMESTAMP(6) WITH TIME ZONE` | `NULL`     | Time stamp of creation of the audit trail entry (time stamp of user login for entries) in UTC (Coordinated Universal Time) time zone                                                                                                     |
| `PROXY_SESSIONID`    | `NUMBER`                      | `NULL`     | Proxy session serial number, if an enterprise user has logged in through the proxy mechanism                                                                                                                                             |
| `GLOBAL_UID`         | `VARCHAR2(32)`                | `NULL`     | Global user identifier for the user, if the user has logged in as an enterprise user                                                                                                                                                     |
| `INSTANCE_NUMBER`    | `NUMBER`                      | `NULL`     | Instance number as specified by the `INSTANCE_NUMBER` initialization parameter                                                                                                                                                           |
| `OS_PROCESS`         | `VARCHAR2(16)`                | `NULL`     | Operating system process identifier of the Oracle process                                                                                                                                                                                |
| `CREATED_BY`         | `VARCHAR2(30)`                | `NULL`     | Database login user name of the user whose actions were audited                                                                                                                                                                          |
| `CREATE_DATE`        | `DATE`                        | `NULL`     | Date on which the action occurred, based on the `SYSDATE` date                                                                                                                                                                           |
| `UPDATED_BY`         | `VARCHAR2(30)`                | `NULL`     | Same as `CREATED_BY` column value                                                                                                                                                                                                        |
| `UPDATE_DATE`        | `DATE`                        | `NULL`     | Same as `UPDATED_BY` column value                                                                                                                                                                                                        |

**Parent topic:** Oracle Database Vault Specific Audit Events

### A.4 Archiving and Purging the Oracle Database Vault Audit Trail

If you have not migrated to unified auditing, you should periodically archive and purge the Oracle Database Vault audit trail.

- About Archiving and Purging the Oracle Database Vault Audit Trail
  In a non-unified auditing environment, you can archive the Oracle Database Vault audit trail by exporting the `DVSYS.AUDIT_TRAIL$` table to a dump file.
- Archiving the Oracle Database Vault Audit Trail
  You can use SQL\*Plus and Oracle Data Pump to archive the Oracle Database Vault audit trail.
- Purging the Oracle Database Vault Audit Trail
  You can purge the Oracle Database Vault audit trail in SQL\*Plus.

**Parent topic:** Auditing Oracle Database Vault

#### A.4.1 About Archiving and Purging the Oracle Database Vault Audit Trail

In a non-unified auditing environment, you can archive the Oracle Database Vault audit trail by exporting the `DVSYS.AUDIT_TRAIL$` table to a dump file.

You should periodically archive and then purge the audit trail to prevent it from growing too large.

If you choose to migrate to unified auditing, then use this procedure to archive and purge the Database Vault audit trail records after you complete the migration. When unified auditing begins to collect records, then the new records will be available for viewing from the `UNIFIED_AUDIT_TRAIL`, `AUDSYS.DV$CONFIGURATION_AUDIT`, and `AUDSYS.DV$ENFORCEMENT_AUDIT` data dictionary views.

**Parent topic:** Archiving and Purging the Oracle Database Vault Audit Trail

#### A.4.2 Archiving the Oracle Database Vault Audit Trail

You can use SQL\*Plus and Oracle Data Pump to archive the Oracle Database Vault audit trail.

1.  Log into the database instance as user `SYS` with the `SYSDBA` administrative privilege.

        sqlplus sys as sysdba
        Enter password: password

2.  Ensure that the user who will perform archiving has the appropriate privileges.

    For example:

        GRANT CREATE ANY DIRECTORY, EXP_FULL_DATABASE, UNLIMITED TABLESPACE TO psmith;

3.  Connect as a user who has been granted the `DV_OWNER` or `DV_AUDIT_CLEANUP` role.

    For example:

        connect ebrown
        Enter password: password

4.  Archive the Oracle Database Vault audit trail into a new table in an appropriate schema.

    For example:

        CREATE TABLE psmith.dv_audit_trail nologging \
        AS SELECT * FROM DVSYS.AUDIT_TRAIL$;

5.  If the schema is already protected by a realm, then ensure that you or the user performing the export operation has been granted the appropriate authorization to use Oracle Data Pump in a Database Vault environment.

    For example, to authorize user `psmith` to perform Data Pump operations on his own schema:

        EXEC DBMS_MACADM.AUTHORIZE_DATAPUMP_USER('PSMITH', 'PSMITH');

6.  Connect as the Data Pump user.

    For example:

        CONNECT psmith
        Enter password: password

7.  Create a directory for the Database Vault audit trail.

        CREATE DIRECTORY dv_audit_dir AS 'dv_audit_trail_directory';

8.  Exit SQL\*Plus.

        EXIT

9.  Using Data Pump, export the Database Vault audit trail into the directory object that you just created.

        expdp psmith directory=dv_audit_dir tables=psmith.dv_audit_trail \
        dumpfile=dv_audit.dmp log=dv_audit_exp.log

10. Connect to SQL\*Plus as a user who has been granted the `DV_OWNER` role.

        sqlplus ebrown
        Enter password: password

11. If you have not done so, then create a realm around the schema that now contains the Database Vault audit trail.

    1.  Create the realm. For example:

            BEGIN
             DBMS_MACADM.CREATE_REALM(
              realm_name    => 'DV Audit Trail Realm',
              description   => 'Realm to protect the DV audit trail',
              enabled       => DBMS_MACUTL.G_YES,
              audit_options => DBMS_MACUTL.G_REALM_AUDIT_FAIL + DBMS_MACUTL.G_REALM_AUDIT_SUCCESS,
              realm_type    => 1);
            END;
            /

    2.  Add the schema that contains to audit trail to this realm. For example:

            BEGIN
             DBMS_MACADM.ADD_OBJECT_TO_REALM(
              realm_name   => 'DV Audit Trail Realm',
              object_owner => 'psmith',
              object_name  => '%',
              object_type  => '%');
            END;
            /

    3.  Authorize a trusted user for this realm.

            BEGIN
             DBMS_MACADM.ADD_AUTH_TO_REALM(
              realm_name  => 'DV Audit Trail Realm',
              grantee     => 'PSMITH',
              auth_options => DBMS_MACUTL.G_REALM_AUTH_OWNER);
            END;
            /

**See Also:**

- [Using Oracle Data Pump with Oracle Database Vault](dba-operations-in-an-oracle-database-vault-environment.md) for more information about granting users Oracle Data Pump privileges in a Database Vault environment

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-DIRECTORY.md) for information about the `CREATE DIRECTORY` statement

- [Oracle Database Utilities](../sutil/oracle-data-pump-export-utility.md) for information about the Oracle Data Pump `expdp` utility

- [Oracle Database Vault Realm APIs](oracle-database-vault-realm-apis.md), for information about the realm-related `DBMS_MACADM` procedures

**Parent topic:** Archiving and Purging the Oracle Database Vault Audit Trail

#### A.4.3 Purging the Oracle Database Vault Audit Trail

You can purge the Oracle Database Vault audit trail in SQL\*Plus.

1.  Log into the database instance as a user who has been granted the `DV_OWNER` role or the `DV_AUDIT_CLEANUP` role.
    For example:

        sqlplus psmith
        Enter password: password

    Note that the `DV_OWNER` and `DV_AUDIT_CLEANUP` roles do not allow their grantees to truncate the `DVSYS.AUDIT_TRAIL$` system table.

    You can query the `DBA_ROLE_PRIVS` data dictionary view to find the roles that have been granted to a user.
2.  Purge the Database Vault audit trail.
        DELETE FROM DVSYS.AUDIT_TRAIL$;

**Related Topics**

- [DV_AUDIT_CLEANUP Audit Trail Cleanup Role](oracle-database-vault-schemas-roles-and-accounts.md)

**Parent topic:** Archiving and Purging the Oracle Database Vault Audit Trail

### A.5 Oracle Database Audit Settings Created for Oracle Database Vault

When you install Oracle Database Vault, it creates several `AUDIT` settings in the database.

In a non-unified auditing environment, in order for these audit settings to take place, auditing must be enabled in this database. You can check if auditing is enabled by using the `SHOW PARAMETER` command to find the value of the `AUDIT_TRAIL` initialization parameter. By default, auditing is enabled in Oracle Database.

Table A-2 lists the `AUDIT` settings that Oracle Database Vault adds to the database.

Table A-2 Audit Policy Settings Oracle Database Vault Adds to Oracle Database

| Audit Setting Type                                                                                                                                                                                                                                                                                                                                                                                                                   | Audited Statements (BY ACCESS and on Success or Failure Unless Otherwise Noted)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| User Audit Settings for `DVSYS`/`DVF`<br>User Audit Settings for `LBACSYS`<br>See [Table 13-1](oracle-database-vault-schemas-roles-and-accounts.md) for more information about these accounts.<br>See also these sections for detailed information on the `DVSYS` and `DVF` schemas:<br>• [DVSYS Schema](oracle-database-vault-schemas-roles-and-accounts.md)<br>• [DVF Schema](oracle-database-vault-schemas-roles-and-accounts.md) | `ADMINISTER DATABASE TRIGGER`<br>`ALTER` `object`<br>`AUDIT SYSTEM`<br>`BECOME USER`<br>`CLUSTER`<br>`COMMENT`<br>`CONTEXT`<br>`CREATE` `object`<br>`DATABASE LINK`<br>`DEBUG`<br>`DIRECTORY`<br>`DROP` `object`<br>`EXECUTE LIBRARY` (`WHENEVER NOT SUCCESSFUL`)<br>`EXECUTE PROCEDURE` (`WHENEVER NOT SUCCESSFUL`)<br>`EXEMPT ACCESS POLICY`<br>`EXPORT FULL DATABASE`<br>`GRANT` `object`<br>`IMPORT FULL DATABASE`<br>`INDEX`<br>`MANAGE SCHEDULER`<br>`MANAGE TABLESPACE`<br>`MATERIALIZED VIEW` (audits both accessing and creating materialized views)<br>`SELECT SEQUENCE` (`WHENEVER NOT SUCCESSFUL`)<br>`SELECT TABLE` (`WHENEVER NOT SUCCESSFUL`) |
| Object Audit Settings for `DVF`                                                                                                                                                                                                                                                                                                                                                                                                      | `AUDIT PACKAGE/PROCEDURE/FUNCTION/SEQUENCE/TABLE`<br>`COMMENT TABLE/VIEW`<br>`DELETE TABLE/VIEW`<br>`EXECUTE PACKAGE/PROCEDURE/FUNCTION` (`WHENEVER NOT SUCCESSFUL`)<br>`GRANT PACKAGE/PROCEDURE/FUNCTION/SEQUENCE/TABLE`<br>`RENAME PACKAGE/PROCEDURE/FUNCTION/SEQUENCE/VIEW/TABLE`<br>`SELECT SEQUENCE/TABLE/VIEW` (`WHENEVER NOT SUCCESSFUL`)                                                                                                                                                                                                                                                                                                             |
| Object Audit Settings for `DVSYS`<br>Object Audit Settings for `LBACSYS`                                                                                                                                                                                                                                                                                                                                                             | `AUDIT PACKAGE/PROCEDURE/FUNCTION/SEQUENCE/TABLE`<br>`COMMENT TABLE/VIEW`<br>`DELETE TABLE/VIEW`<br>`EXECUTE PACKAGE/PROCEDURE/FUNCTION` (`WHENEVER NOT SUCCESSFUL`)<br>`GRANT PACKAGE/PROCEDURE/FUNCTION/SEQUENCE/TABLE`<br>`INSERT TABLE/VIEW`<br>`RENAME PACKAGE/PROCEDURE/FUNCTION/SEQUENCE/VIEW/TABLE`<br>`SELECT SEQUENCE/TABLE/VIEW` (`WHENEVER NOT SUCCESSFUL`)<br>`UPDATE TABLE/VIEW`                                                                                                                                                                                                                                                               |

**Parent topic:** Auditing Oracle Database Vault
