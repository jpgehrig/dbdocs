This preface contains:

- Changes in Oracle Database Vault 19c

### Changes in Oracle Database Vault 19c

The following are changes in Oracle Database Vault Administrator's Guide for Oracle Database 19c.

- Command Rule Support for Unified Audit Policies
  You now can create Oracle Database Vault command rules for unified audit policies.
- Database Vault Operations Control for Infrastructure Database Administrators
  In a multitenant database, you now can use Oracle Database Vault to block common users (infrastructure DBAs, for example) from accessing local data in pluggable databases (PDBs) in autonomous, regular Cloud, or on-premises environments.
- Privilege Analysis Documentation Moved to Oracle Database Security Guide
  The documentation for privilege analysis has moved from Oracle Database Vault Administrator’s Guide to Oracle Database Security Guide.

**Parent topic:** Changes in This Release for Oracle Database Vault Administrator's Guide

#### Command Rule Support for Unified Audit Policies

You now can create Oracle Database Vault command rules for unified audit policies.

You can now use command rules to enable and disable individual unified audit policies. This enhancement provides fine-grain control over how each policy is managed, instead of having to manage all the unified audit policies in the same way through a single command rule. For example, an HR auditor can have control over his or her HR unified audit policy, but not the CRM unified audit policy. This new feature extends the `AUDIT` and `NOAUDIT` use for command rules, but when you specify unified audit policy for the command rule, you must specify `AUDIT POLICY` or `NOAUDIT POLICY`.

**Related Topics**

- [SQL Statements That Can Be Protected by Command Rules](configuring-command-rules.md)
- [Creating a Command Rule](configuring-command-rules.md)
- [CREATE_COMMAND_RULE Procedure](oracle-database-vault-command-rule-apis.md)

**Parent topic:** Changes in Oracle Database Vault 19c

#### Database Vault Operations Control for Infrastructure Database Administrators

In a multitenant database, you now can use Oracle Database Vault to block common users (infrastructure DBAs, for example) from accessing local data in pluggable databases (PDBs) in autonomous, regular Cloud, or on-premises environments.

This enhancement prevents common users from accessing local data that resides on a PDB. It enables you to store sensitive data for your business applications and allow operations to manage the database infrastructure without having to access sensitive customer data.

**Related Topics**

- [Using Database Vault Operations Control to Restrict Multitenant Common User Access to Local PDB Data](dba-operations-in-an-oracle-database-vault-environment.md)

**Parent topic:** Changes in Oracle Database Vault 19c

#### Privilege Analysis Documentation Moved to Oracle Database Security Guide

The documentation for privilege analysis has moved from Oracle Database Vault Administrator’s Guide to Oracle Database Security Guide.

See Oracle Database Licensing Information User Manual for privilege analysis licensing information.

**Related Topics**

- [Oracle Database Security Guide](../dbseg/release-changes.md)
- [Oracle Database Licensing Information User Manual](../dblic/Licensing-Information.md)

**Parent topic:** Changes in Oracle Database Vault 19c
