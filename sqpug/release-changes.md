## Changes in This Release for SQL\*Plus

This preface lists changes in the SQL\*Plus User's Guide and Reference

### Changes in SQL\*Plus Release 19c

The following are changes in the SQL\*Plus User's Guide and Reference for SQL\*Plus Release 19c.

#### New Features

The following feature is new in this release:

The Easy Connect syntax, which is used by applications to connect to Oracle Database, has been enhanced and is called Easy Connect Plus.

See [About Easy Connect Plus](../netag/configuring-naming-methods.md)

#### Deprecated Features

The following feature is deprecated in this release:

##### 69821-28 Deprecation of RECOVER…SNAPSHOT TIME

The `RECOVER…SNAPSHOT TIME` method of recovering a database to a point in time using a particular snapshot is deprecated in Oracle Database 19c.

Instead of `RECOVER…SNAPSHOT TIME`, Oracle recommends that you use `ALTER DATABASE BEGIN/END BACKUP` before and after creating the storage snapshot of the data files and then use `RECOVER .. UNTIL TIME` to a specific timestamp or system change number (SCN) after the `END BACKUP` completion time. Oracle recommends that `ALTER DATABASE BEGIN/END BACKUP` always be used when performing snapshots on a running database to ensure data recovery integrity. Archived log redo logs must be separately backed up and restored for recovery operations.

#### Desupported Features

The following feature is no longer supported:

##### Desupport of PRODUCT_USER_PROFILE Table

Starting in Oracle Database 19c, the SQL\*Plus table PRODUCT_USER_PROFILE (PUP table) is desupported.

The SQL\*Plus product-level security feature is unavailable in Oracle Database 19c. Oracle recommends that you protect data by using Oracle Database settings, so that you ensure consistent security across all client applications.
