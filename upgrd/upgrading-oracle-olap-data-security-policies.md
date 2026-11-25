## About Upgrading Oracle OLAP Data Security Policies

Security policies are stored differently starting with Oracle Database 12c. If your existing Oracle Database is 11g Release 11.2, then delete security roles.

In Oracle Database 12c, Oracle OLAP uses Oracle Real Application Security (ORAS) to store OLAP data security policies instead of Extensible Data Security (XDS), which it used in Oracle Database 11g releases.

When you upgrade Oracle Database from release 11g to new Oracle Database releases, any XDS data security policies are automatically converted to ORAS.

**Note:**

Data security roles defined in a release 11g Oracle Database instance are not automatically converted to ORAS. Before you upgrade Oracle Database Release 11g to a current Oracle Database release, you must delete any data security roles that are defined in the 11g database. After the upgrade, you can use the new release Oracle Database Analytic Workspace Manager to define the data security roles again.

If you upgrade an 11g database without deleting the 11g data security roles, then any data security policies that include a data security role are invalid in the later Oracle Database releases.

**Related Topics**

- [Oracle OLAP User’s Guide](../olaug/overview.md)

**Parent topic:** [Compatibility and Interoperability Between Oracle Database Releases](compatibility-interoperability-between-database-releases.md)
