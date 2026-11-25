You can use Oracle Label Security auditing if you have not configured your database to use unified auditing.

- About Oracle Label Security Auditing
  Oracle Label Security auditing supplements standard Oracle Database auditing by tracking use of its own administrative operations and policy privileges.
- Systemwide Auditing: AUDIT_TRAIL Initialization Parameter
  If you have not yet enabled unified auditing, for Oracle Label Security to generate audit records, you must first enable system-wide auditing.
- How Oracle Label Security Auditing Is Enabled or Disabled
  After you have enabled systemwide auditing, you can enable or disable Oracle Label Security auditing.
- Oracle Label Security and Unified Auditing
  Oracle Database uses the unified audit trail to capture information from various audit sources, including Oracle Label Security.
- Oracle Label Security Auditing Tips
  Oracle provides a set of tips for auditing Oracle Label Security.

**Parent topic:** [Administering an Oracle Label Security Application](part3.md)

### 13.1 About Oracle Label Security Auditing

Oracle Label Security auditing supplements standard Oracle Database auditing by tracking use of its own administrative operations and policy privileges.

You can use either the `SA_AUDIT_ADMIN` package or Oracle Enterprise Manager to set and change the auditing options for an Oracle Label Security policy.

When you create a new policy, a label column for that policy is added to the database audit trail. The label column is created regardless of whether auditing is enabled or disabled, and independent of whether database auditing or operating system auditing is used. Whenever a record is written to the audit table, each policy provides a label for that record to indicate the session label. The administrator can create audit views to display these labels. Note that in the audit table, the label does not control access to the row, instead it only records the sensitivity of the row.

The auditing options that you specify apply only to subsequent sessions, not to the current session. You can specify audit options even if auditing is disabled. No overhead is created by making only these specifications. When you do enable Oracle Label Security auditing, the options come into effect, and overhead is created beyond that created by standard Oracle Database auditing.

Note that Oracle Label Security does not provide labels for audit data written to the operating system audit trial. All Oracle Label Security audit records are written directly to the database audit trail, even if operating system auditing is enabled. If auditing is disabled, then no Oracle Label Security audit records are generated.

If you are using traditional auditing (not unified auditing), then the traditional audit trail lists only the action numbers. To find the corresponding audit action names, you can query the `LABACSYS.OLS$AUDIT_ACTIONS` system table. You must have the `AUDIT_VIEWER`, `AUDIT_ADMIN`, or `policy``_DBA` role to query this table.

**Parent topic:** Auditing Under Oracle Label Security

### 13.2 Systemwide Auditing: AUDIT_TRAIL Initialization Parameter

If you have not yet enabled unified auditing, for Oracle Label Security to generate audit records, you must first enable system-wide auditing.

To enable system-wide auditing, you can set the Oracle Database `AUDIT_TRAIL` initialization parameter in the database's parameter file.

You can set the `AUDIT_TRAIL` parameter to one of the following values:

Table 13-1 AUDIT_TRAIL Parameter Settings

| Setting          | Explanation                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:-----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DB`             | Enables database auditing and directs all audit records to the database audit trail. This approach is recommended by Oracle.<br>Note that even with `AUDIT_TRAIL` set to `DB`, some records are always sent to the operating system audit trail. These include `STARTUP` and `SHUTDOWN` statements, as well as `CONNECT` `AS` `SYSOPER` or `SYSDBA`.                                                                                                                                                                                                                                   |
| `DB`, `EXTENDED` | Does all actions of `AUDIT_TRAIL=DB` and also populates the `SqlBind` and `SqlText` `CLOB`-type columns of the` AUD$` table.                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `OS`             | Enables operating system auditing. This directs most of your Oracle Database audit records to the operating system, rather than to the database; the records will not contain Oracle Label Security labels. By contrast, any Oracle Label Security auditing will go to the database, with labels.<br>If you set `AUDIT_TRAIL` to `OS`, then the Oracle Label Security-specific audit records are written to the database audit trail and the other Oracle Database audit records are written to the operating system audit trail (with no policy column in the operating system data). |
| `NONE`           | Disables auditing. This is the default.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |

After you have edited the parameter file, restart the database instance to enable or disable database auditing as specified.

Set the `AUDIT_TRAIL` parameter before you set audit options. If you do not set this parameter, then you are still able to set audit options. However, audit records are not written to the database until the parameter is set and the database instance is restarted.

**See Also:**

- [Oracle Database Security Guide](../dbseg/part_6.md) for information about enabling and disabling systemwide auditing, setting audit options, and managing the audit trail

- [Oracle Database Reference](../refrn/initialization-parameters.md) or information about editing initialization parameter

- [Oracle Database SQL Language Reference](../sqlrf/AUDIT-Traditional-Auditing.md) for details about systemwide `AUDIT` and `NOAUDIT` functioning

**Parent topic:** Auditing Under Oracle Label Security

### 13.3 How Oracle Label Security Auditing Is Enabled or Disabled

After you have enabled systemwide auditing, you can enable or disable Oracle Label Security auditing.

To use Oracle Label Security auditing, you must have the `policy``_DBA` role and use the `SA_AUDIT_ADMIN` PL/SQL package procedures.

**Related Topics**

- [SA_AUDIT_ADMIN Oracle Label Security Auditing PL/SQL Package](oracle-label-security-pl-sql-packages.md)

**Parent topic:** Auditing Under Oracle Label Security

### 13.4 Oracle Label Security and Unified Auditing

Oracle Database uses the unified audit trail to capture information from various audit sources, including Oracle Label Security.

You can configure OLS auditing using audit policies. Oracle Label Security auditing in Oracle Database 12c release 1 (12.1) enables you to audit additional events such as enabling and disabling of OLS policies.

If you have upgraded your database to Oracle Database 12c release 1 (12.1), but have not configured it to use unified auditing, then you must use the pre-12c OLS auditing described in this chapter.

The Oracle Database audit facility lets you hold database users accountable for the operations they perform. It can track specific database objects, operations, users, and privileges. Oracle Label Security supplements this by tracking use of its own administrative operations and policy privileges. It provides the `SA_AUDIT_ADMIN` package to set and change the policy auditing options.

**See Also:**

[Oracle Database Security Guide](../spucs/recommended-and-best-practices-complete-upgrading-oracle-database.md) for instructions on configuring your upgraded database to use unified auditing. After migration, you can find the OLS unified audit information at [Oracle Database Security Guide](../dbseg/configuring-audit-policies.md)

**Parent topic:** Auditing Under Oracle Label Security

### 13.5 Oracle Label Security Auditing Tips

Oracle provides a set of tips for auditing Oracle Label Security.

- Strategy for Setting SA_AUDIT_ADMIN Options
  Before setting any audit options, you must devise an auditing strategy that monitors events of interest, without recording extraneous events.
- Auditing of Privileged Operations
  Consider auditing any operations that require Oracle Label Security privileges.

**Parent topic:** Auditing Under Oracle Label Security

#### 13.5.1 Strategy for Setting SA_AUDIT_ADMIN Options

Before setting any audit options, you must devise an auditing strategy that monitors events of interest, without recording extraneous events.

You should periodically review this strategy, because applications, user base, configurations, and other external factors can change.

The Oracle Label Security options, and those provided by the Oracle Database audit facility, might not directly address all of your specific or application-dependent auditing requirements. However, through use of database triggers, you can audit specific events and record specific information that you cannot audit and record using the more generic audit facility.

**See Also:**

[Oracle Database Concepts](../cncpt/server-side-programming.md) for more information about using triggers for auditing

**Parent topic:** Oracle Label Security Auditing Tips

#### 13.5.2 Auditing of Privileged Operations

Consider auditing any operations that require Oracle Label Security privileges.

Because these privileges perform sensitive operations, and because their abuse could jeopardize security, you should closely monitor their dissemination and use.

**Parent topic:** Oracle Label Security Auditing Tips
