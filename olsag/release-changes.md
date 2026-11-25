This preface contains:

- Changes in Oracle Database 18c

### Changes in Oracle Database 18c

The following are changes in Oracle Label Security Administrator’s Guide for Oracle Database 18c.

- LBACSYS User Created by Default as a Schema-Only Account
  Starting with this release, the `LBACSYS` user account is create as a schema-only account.
- Deprecated Columns in Oracle Label Security Views
  Starting in this release, four Oracle Label Security data dictionary views have deprecated columns.

**Parent topic:** Changes in This Release for Oracle Label Security Administrator's Guide

#### LBACSYS User Created by Default as a Schema-Only Account

Starting with this release, the `LBACSYS` user account is create as a schema-only account.

Users cannot login to a schema-only account until an authentication method is configured for the account by using the `ALTER USER` statement. `LBACSYS` is only used as a login account initially to provision named Oracle Label Security administrators. Because users do not need to log in to this account (except for initial provisioning), `LBACSYS` should remain a schema-only account so that default passwords do not need to be changed or rotated.

This feature meets requirements for users who must be able to create schemas for object ownership without actually allowing the schema owner to log in to the database. Examples of environments that have this need include some Oracle schemas as well as some customer schemas.

**Related Topics**

- [Security Guideline for Managing the LBACSYS User and the LBAC_DBA Role](getting-started-with-oracle-label-security.md)
- [Oracle Database Security Guide](../dbseg/configuring-authentication.md)

**Parent topic:** Changes in Oracle Database 18c

#### Deprecated Columns in Oracle Label Security Views

Starting in this release, four Oracle Label Security data dictionary views have deprecated columns.

| Data Dictionary View | Deprecated Column |
|:---------------------|:------------------|
| `ALL_SA_USER_LABELS` | `LABELS`          |
| `ALL_SA_USERS`       | `USER_LABELS`     |
| `DBA_SA_USER_LABELS` | `LABELS`          |
| `DBA_SA_USERS`       | `USER_LABELS`     |

The information in the `LABELS` and `USER_LABELS` columns is redundant. This information is displayed in other columns in these data dictionary views.

**Related Topics**

- [Oracle Label Security Data Dictionary Views](oracle-label-security-reference.md)

**Parent topic:** Changes in Oracle Database 18c
