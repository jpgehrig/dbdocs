## What Is Oracle Database Compatibility?

Before you upgrade, review compatibility between your earlier release Oracle Database and the new Oracle Database release as part of your upgrade plan.

- Understanding Oracle Database Compatibility
  If new features are incompatible with your earlier release, then updating database compatibility can cause issues.
- When to Set the COMPATIBLE Initialization Parameter in Oracle Database
  Oracle recommends increasing the `COMPATIBLE` parameter only after you have completed testing the upgraded database.
- The COMPATIBLE Initialization Parameter in Oracle Database
  Review to understand how to set the COMPATIBLE initialization parameter for non-CDB and multitenant architecture containers.
- Values for the COMPATIBLE Initialization Parameter in Oracle Database
  Review to find the default, minimum, and maximum values for the COMPATIBLE initialization parameter for Oracle Database 19c.
- About Downgrading and Compatibility for Upgrading Oracle Database
  Before upgrading to Oracle Database 19c, you must set the COMPATIBLE initialization parameter to at least `11.2.0`.
- How the COMPATIBLE Initialization Parameter Operates in Oracle Database
  The `COMPATIBLE` initialization parameter enables or disables Oracle Database features based on release compatibility
- Checking the Compatibility Level of Oracle Database
  Use this SQL query to find the COMPATIBLE initialization parameter value set for your database.

**Parent topic:** [Compatibility and Interoperability Between Oracle Database Releases](compatibility-interoperability-between-database-releases.md)

### Understanding Oracle Database Compatibility

If new features are incompatible with your earlier release, then updating database compatibility can cause issues.

Databases from different releases of Oracle Database software are compatible if they support the same features, and if those features perform the same way. When you upgrade to a new release of Oracle Database, certain new features can make your database incompatible with your earlier release.

Your upgraded database becomes incompatible with your earlier release under the following conditions:

- A new feature stores any data on disk (including data dictionary changes) that cannot be processed with your earlier release.
- An existing feature behaves differently in the new environment as compared to the old environment.

**Parent topic:** What Is Oracle Database Compatibility?

### When to Set the COMPATIBLE Initialization Parameter in Oracle Database

Oracle recommends increasing the `COMPATIBLE` parameter only after you have completed testing the upgraded database.

After the upgrade is complete, you can increase the setting of the `COMPATIBLE` initialization parameter to the maximum level for the new Oracle Database release. However, after you increase the `COMPATIBLE` parameter, you cannot subsequently downgrade the database.

**Parent topic:** What Is Oracle Database Compatibility?

### The COMPATIBLE Initialization Parameter in Oracle Database

Review to understand how to set the COMPATIBLE initialization parameter for non-CDB and multitenant architecture containers.

Oracle Database enables you to control the compatibility of your database with the COMPATIBLE initialization parameter.

#### Understanding the COMPATIBLE Initialization Parameter

In Oracle Database 19c, when the COMPATIBLE initialization parameter is not set in your parameter file, the `COMPATIBLE` parameter value defaults to `19.0.0` If you do not set the COMPATIBLE initialization parameter to `19.0.0`, then you cannot use the new Oracle Database 19c features, because your upgraded database is not running in the required COMPATIBILITY setting for Oracle Database 19c features.

Due to changes in internal SQL identifier and schema object name restrictions, you can experience an initial delay for any process where the database runs a Java stored procedure directly or indirectly in the database server after you increase the `COMPATIBLE` parameter setting. When you increase the Oracle Database `COMPATIBLE` parameter to 12.2.0 or later from a `COMPATIBLE` setting earlier than 12.2.0, and the database runs a Java stored procedure, the database performs a "name translation" operation. This operation can require a few minutes to complete. You should expect this delay the first time the database runs a Java stored procedure after you increase the compatibility parameter. This delay for the database to perform the name translation occurs only during the first Java process call.

**Note:**

- Before upgrading to Oracle Database 19c, you must set the `COMPATIBLE` initialization parameter to at least `11.2.0`, which is the minimum setting for Oracle Database 19c.

- The compatible parameter must be at least 3 decimal numbers, separated by periods. For example:

      SQL> ALTER SYSTEM SET COMPATIBLE = '19.0.0' SCOPE=SPFILE;

- Oracle recommends that you only raise the `COMPATIBLE` parameter after you have thoroughly tested the upgraded database.

- After you increase the `COMPATIBLE` parameter, you cannot downgrade the database, and you cannot flash back to restore points.

**Caution:**

If you are upgrading from Oracle Database release 11.2, then you must set the compatible value to at least 11.2.0. You must do this at the time of the upgrade. Do not make this change until you are ready to upgrade, because a downgrade back to an earlier compatibility level is not possible after you raise the COMPATIBLE initialization parameter value.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/creating-and-configuring-an-oracle-database.md) for information about managing initialization parameters

#### Rules for COMPATIBLE Parameter Settings in Multitenant Architecture

The COMPATIBLE parameter of the container database (CDB) affects the COMPATIBLE parameter settings of pluggable databases (PDBs) plugged into that container database. Review the following scenarios that occur when you plug in a PDB to a CDB:

- PDB COMPATIBLE equal to `CDB$ROOT` COMPATIBLE parameter setting.

  Result: No change to the PDB COMPATIBLE parameter setting.

- PDB COMPATIBLE is lower than `CDB$ROOT` COMPATIBLE parameter setting.

  Result: The PDB COMPATIBLE parameter is increased automatically to the same COMPATIBLE parameter setting as `CDB$ROOT`. After you plug in the PDB, you cannot downgrade the PDB to an earlier release.

- PDB COMPATIBLE is higher than `CDB$ROOT` COMPATIBLE parameter setting.

  Result: The PDB cannot be plugged in. Only PDBs with a COMPATIBLE parameter setting equal to or lower than `CDB$ROOT` can be plugged in to the CDB.

**Parent topic:** What Is Oracle Database Compatibility?

### Values for the COMPATIBLE Initialization Parameter in Oracle Database

Review to find the default, minimum, and maximum values for the COMPATIBLE initialization parameter for Oracle Database 19c.

#### Default and Minimum COMPATIBLE Parameter Values

The COMPATIBLE parameter should not be changed for an RU or an RUR, either for CDB or Non-CDB instances. The following table lists the default and minimum values for the COMPATIBLE parameter in Oracle Database 19c, compared to earlier releases supported for direct upgrade:

Table 1-2 The COMPATIBLE Initialization Parameter

| Oracle Database Release              | Default Value | Minimum Value |
|:-------------------------------------|:--------------|:--------------|
| Oracle Database 19c                  | `19.0.0`      | `11.2.0`      |
| Oracle Database 12c Release 2 (12.2) | `12.2.0`      | `11.2.0`      |
| Oracle Database 12c Release 1 (12.1) | `12.0.0`      | `11.0.0`      |
| Oracle Database 11g Release 2 (11.2) | `11.2.0`      | `10.0.0`      |

**Parent topic:** What Is Oracle Database Compatibility?

### About Downgrading and Compatibility for Upgrading Oracle Database

Before upgrading to Oracle Database 19c, you must set the COMPATIBLE initialization parameter to at least `11.2.0`.

After upgrading to Oracle Database 18c, you can set the COMPATIBLE initialization parameter to match the release number of the new release. Doing so enables you to use all features of the new release, but prevents you from downgrading to your earlier release. Only a subset of Oracle Database 18c features are available while the `COMPATIBLE` initialization parameter is set to a lower value.

**Caution:**

After you increase the COMPATIBLE parameter, the database cannot be downgraded.

**Related Topics**

- [Downgrading Oracle Database to an Earlier Release](downgrading-oracle-db-after-upgrade.md)

**Parent topic:** What Is Oracle Database Compatibility?

### How the COMPATIBLE Initialization Parameter Operates in Oracle Database

The `COMPATIBLE` initialization parameter enables or disables Oracle Database features based on release compatibility

The `COMPATIBLE` initialization parameter operates in the following way:

- The `COMPATIBLE` initialization parameter enables or disables the use of features, to help protect your existing application use of data.

  If you run an Oracle Database 12c database with the `COMPATIBLE` initialization parameter set to `11.2.0`, then the database software generates database structures on disk that are compatible with Oracle Database Release 11g release 2 (11.2). If you try to use features that are part of a later release of Oracle Database, and make the database incompatible with the `COMPATIBLE` initialization parameter, then an error occurs. However, new features are enabled that do not create changes on disk that are incompatible with Oracle Database Release 11g release 2.

- If you make changes to the database that make the database incompatible with the `COMPATIBLE` initialization parameter setting you want to use, then the database does not start, and initialization terminates in an error. If this happens, then you must set the `COMPATIBLE` initialization parameter to an appropriate value for the database.

**See Also:**

[Oracle Database Concepts](../cncpt/introduction-to-oracle-database.md) for more information about database structures

**Parent topic:** What Is Oracle Database Compatibility?

### Checking the Compatibility Level of Oracle Database

Use this SQL query to find the COMPATIBLE initialization parameter value set for your database.

    SQL> SELECT name, value FROM v$parameter
             WHERE name = 'compatible';

**Parent topic:** What Is Oracle Database Compatibility?
