## 17 Security Considerations for Oracle Data Redaction

Oracle provides guidelines for using Oracle Data Redaction.

- Oracle Data Redaction General Security Guidelines
  It is important to understand general security guidelines for using Oracle Data Redaction.
- Restriction of Administrative Access to Oracle Data Redaction Policies
  You can restrict the list of users who can create, view and edit Data Redaction policies.
- How Oracle Data Redaction Affects the SYS, SYSTEM, and Default Schemas
  Both users `SYS` and `SYSTEM` automatically have the `EXEMPT REDACTION POLICY` system privilege.
- Policy Expressions That Use SYS_CONTEXT Attributes
  Be careful when writing a policy expression that depends on a `SYS_CONTEXT` attribute that is populated by an application.
- Oracle Data Redaction Policies on Materialized Views
  You can create Oracle Data Redaction policies on materialized views and on their base tables.
- REDACTION_COLUMNS Data Dictionary View Behavior When a View Is Invalid
  When an Oracle Data Redaction policy exists on a column of a view, and the view becomes invalid, the Data Redaction policy remains visible in the `REDACTION_COLUMNS` data dictionary view.
- Dropped Oracle Data Redaction Policies When the Recycle Bin Is Enabled
  You should check if the recycle bin is enabled before you drop Oracle Data Redaction policies.

**Parent topic:** [Using Oracle Data Redaction](asopart2.md)

### 17.1 Oracle Data Redaction General Security Guidelines

It is important to understand general security guidelines for using Oracle Data Redaction.

- Oracle Data Redaction is not intended to protect against attacks by regular and privileged database users who run ad hoc queries directly against the database. If the user can issue arbitrary SQL or PL/SQL statements, then they will be able to access the actual value.

- Oracle Data Redaction is not intended to protect against users who run ad hoc SQL queries that attempt to determine the actual values by inference. Inference refers to query that is designed to find data by repeatedly trying queries. For example, to find the users who earn the highest salaries, an intruder could use the following query:

      SELECT FIRST_NAME, LAST_NAME, SALARY
      FROM HR.EMPLOYEES
      WHERE SALARY > 16000
      ORDER BY SALARY DESC;

      FIRST_NAME           LAST_NAME                     SALARY
      -------------------- ------------------------- ----------
      Steven               King                           24000
      Neena                Kochhar                        17000
      Lex                  De Haan                        17000

- Oracle Data Redaction relies on the database and application context values. For applications, it is the responsibility of the application to properly initialize the context value.

- Oracle Data Redaction is not enforced for users who are logged in using the `SYSDBA` administrative privilege.

- Certain DDL statements that attempt to copy the actual data out from under the control of a data redaction policy (that is, `CREATE TABLE AS SELECT`, `INSERT AS SELECT`) are blocked by default, but you can disable this behavior by granting the user the `EXEMPT REDACTION POLICY` system privilege.

- Oracle Data Redaction does not affect day-to-day database operations, such as backup and recovery, Oracle Data Pump exports and imports, Oracle Data Guard operations, and replication.

**Parent topic:** Security Considerations for Oracle Data Redaction

### 17.2 Restriction of Administrative Access to Oracle Data Redaction Policies

You can restrict the list of users who can create, view and edit Data Redaction policies.

To accomplish this, you can limit who has the `EXECUTE` privilege on the `DBMS_REDACT` package and by limiting who has the `SELECT` privilege on the `REDACTION_POLICIES` and `REDACTION_COLUMNS` views.

You also can restrict who is exempted from redaction by limiting the `EXEMPT REDACTION POLICY` privilege. If you use Oracle Database Vault to restrict privileged user access, then you can use realms to restrict granting of `EXEMPT REDACTION POLICY`.

**Related Topics**

- [Oracle Data Redaction and Oracle Database Vault](oracle-data-redaction-use-with-oracle-database-features.md)
- [Exemption of Users from Oracle Data Redaction Policies](configuring-oracle-data-redaction-policies.md)
- [Introduction to Oracle Database Vault](../dvadm/introduction-to-oracle-database-vault.md)

**Parent topic:** Security Considerations for Oracle Data Redaction

### 17.3 How Oracle Data Redaction Affects the SYS, SYSTEM, and Default Schemas

Both users `SYS` and `SYSTEM` automatically have the `EXEMPT REDACTION POLICY` system privilege.

`SYSTEM` has the `EXP_FULL_DATABASE` role, which includes the `EXEMPT REDACTION POLICY` system privilege.

This means that the `SYS` and `SYSTEM` users can always bypass any existing Oracle Data Redaction policies, and will always be able to view data from tables (or views) that have Data Redaction policies defined on them.

Follow these guidelines:

- Do not create Data Redaction policies on the default Oracle Database schemas, including the `SYS` and `SYSTEM` schemas.

- Be aware that granting the `EXEMPT REDACTION POLICY` system privilege to additional roles may enable users to bypass Oracle Data Redaction, because the grantee role may have been granted to additional roles.

- Do not revoke the `EXEMPT REDACTION POLICY` system privilege from the roles that it was granted to by default.

**Parent topic:** Security Considerations for Oracle Data Redaction

### 17.4 Policy Expressions That Use SYS_CONTEXT Attributes

Be careful when writing a policy expression that depends on a `SYS_CONTEXT` attribute that is populated by an application.

The application might not always populate that attribute.

If the user somehow connects directly (rather than through the application), then the `SYS_CONTEXT` attribute would not have been populated. If you do not handle this `NULL` scenario in your policy expression, you could unintentionally reveal [actual data](glossary.md) to the querying user.

For example, suppose you wanted to create a policy expression that intends to redact the query results for everyone except users who have the client identifier value of `SUPERVISOR`. The following expression unintentionally enables querying users who have `NULL` as the value for their `CLIENT_IDENTIFIER` to see the real data:

    SYS_CONTEXT('USERENV', 'CLIENT_IDENTIFIER') IS NOT 'SUPERVISOR'

A more rigorous policy expression redacts the result of the query if the client identifier is not set, that is, it has a `NULL` value.

    SYS_CONTEXT('USERENV', 'CLIENT_IDENTIFIER') IS NOT 'SUPERVISOR' OR IS NULL

Remember that in SQL, comparisons with `NULL` are undefined, and are thus `FALSE`, but redaction only takes place when the policy expression evaluates to `TRUE`.

**Parent topic:** Security Considerations for Oracle Data Redaction

### 17.5 Oracle Data Redaction Policies on Materialized Views

You can create Oracle Data Redaction policies on materialized views and on their base tables.

However, ensure that the creator of the materialized view, or the user who performs the refresh of the materialized view, is not blocked by any Data Redaction policies. In other words, the user performing the materialized view creation or refresh operations should be exempt from the Data Redaction policy. As a best practice, when you create a new materalized view, treat it as a copy of the actual table, and then create a separate Data Redaction policy to protect it.

**Parent topic:** Security Considerations for Oracle Data Redaction

### 17.6 REDACTION_COLUMNS Data Dictionary View Behavior When a View Is Invalid

When an Oracle Data Redaction policy exists on a column of a view, and the view becomes invalid, the Data Redaction policy remains visible in the `REDACTION_COLUMNS` data dictionary view.

For example, a view can become invalid if one of its columns refers to a column that was dropped from a table upon which the view depends.

The column continues to be visible in the `REDACTION_COLUMNS` data dictionary view because the Data Redaction policy is not automatically dropped when the view becomes invalid.

Instead, the decision on whether to drop the Data Redaction policy is taken when the view is subsequently altered.

This approach was chosen in preference to automatically dropping the Data Redaction policy when the view becomes invalid because it is less error-prone and presents less risk of accidentally displaying actual data from the underlying table.

By deferring the decision to when the view is being altered, it allows the view to be recompiled after the column is restored to the table. After the column is restored to the table and the view is recompiled, then the view becomes valid and still has its Data Redaction policy in place.

On the other hand, if the invalid view definition was subsequently replaced with a valid view definition which no longer contains the column that the Data Redaction policy was previously defined on, it is at that point that the Data Redaction policy is automatically dropped. The `REDACTION_COLUMNS` data dictionary view is then updated to no longer show the column (since it is no longer part of the new view's definition).

**Parent topic:** Security Considerations for Oracle Data Redaction

### 17.7 Dropped Oracle Data Redaction Policies When the Recycle Bin Is Enabled

You should check if the recycle bin is enabled before you drop Oracle Data Redaction policies.

If you drop a table or view that has an Oracle Data Redaction policy defined on it when the recycle bin feature is enabled, and if you query the `REDACTION_COLUMNS` or `REDACTION_POLICIES` data dictionary views before you purge the recycle bin, then you will see object names such as `BIN$...` (for example, `BIN$1Xu5PSW5VaPgQxGS5AoAEA==$0`).

This is normal behavior. These policies are removed when you purge the recycle bin.

To find if the recycle bin is enabled, you can run the `SHOW PARAMETER RECYCLEBIN` command in SQL\*Plus.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/managing-tables.md) for information about purging objects from the recycle bin

**Parent topic:** Security Considerations for Oracle Data Redaction
