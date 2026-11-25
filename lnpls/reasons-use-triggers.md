## 9.2 Reasons to Use Triggers

Triggers let you customize your database management system.

For example, you can use triggers to:

- Automatically generate virtual column values

- Log events

- Gather statistics on table access

- Modify table data when DML statements are issued against views

- Enforce referential integrity when child and parent tables are on different nodes of a distributed database

- Publish information about database events, user events, and SQL statements to subscribing applications

- Prevent DML operations on a table after regular business hours

- Prevent invalid transactions

- Enforce complex business or referential integrity rules that you cannot define with constraints (see "How Triggers and Constraints Differ")

**Caution:**

Triggers are not reliable security mechanisms, because they are programmatic and easy to disable. For high-assurance security, use Oracle Database Vault, described in [Oracle Database Vault Administrator's Guide](../dvadm/configuring-realms.md).

### How Triggers and Constraints Differ

Both triggers and constraints can constrain data input, but they differ significantly.

A trigger always applies to new data only. For example, a trigger can prevent a DML statement from inserting a `NULL` value into a database column, but the column might contain `NULL` values that were inserted into the column before the trigger was defined or while the trigger was disabled.

A constraint can apply either to new data only (like a trigger) or to both new and existing data. Constraint behavior depends on constraint state, as explained in [Oracle Database SQL Language Reference](../sqlrf/constraint.md).

Constraints are easier to write and less error-prone than triggers that enforce the same rules. However, triggers can enforce some complex business rules that constraints cannot. Oracle strongly recommends that you use triggers to constrain data input only in these situations:

- To enforce referential integrity when child and parent tables are on different nodes of a distributed database

- To enforce complex business or referential integrity rules that you cannot define with constraints

**See Also:**

- [Oracle Database Development Guide](../adfns/data-integrity.md) for information about using constraints to enforce business rules and prevent the entry of invalid information into tables

- "[Triggers for Ensuring Referential Integrity](dml-triggers.md)" for information about using triggers and constraints to maintain referential integrity between parent and child tables
