## Selecting a Database Name

The database name is comprised of various strings and must contain only permitted characters. Review the following guidelines when selecting a database name.

The database name input field sets the following Oracle initialization parameter values:

- DB_NAME

- DB_UNIQUE_NAME

- DB_DOMAIN

In Oracle RAC environments, the database name (DB_UNIQUE_NAME) portion is a string of no more than 30 characters that can contain alphanumeric, underscore (\_), dollar (\$), and pound (#) characters, but must begin with an alphabetic character. No other special characters are permitted in a database name. The DB_NAME parameter for a database is set to the first 8 characters of the database name.

The domain portion of the global database name (DB_DOMAIN) can be no more than 128 characters. Domain names using underscores (\_) are not allowed. The values for DB_UNIQUE_NAME.DB_DOMAIN in its entirety must be unique within the enterprise.

**Note:**

For Oracle Real Applications Cluster (Oracle RAC) databases, the pluggable database (PDB) name must be unique in the cluster.

### Database Name and ORACLE_SID

The Oracle Service Identifier (SID) prefix is the first 8 characters of the database name. The SID prefix can contain only the characters a-z, A-Z, and 0-9. The SID prefix cannot contain operating system special characters, so if you use special characters in the first 8 characters of the database name, then these special characters are omitted in the SID prefix. There is a single SID prefix for every database. The SID prefix for a database must be unique within the cluster.

For an Oracle RAC database, each instance has a unique identifier, `ORACLE_SID`, which consists of the SID prefix and an instance number. The `ORACLE_SID` prefix can contain up to 12 characters. The `ORACLE_SID` for Oracle RAC database instances is generated differently, depending on how you choose to manage the database. If you select a policy-managed database, then Oracle generates the SID in the format name\_#, where name is the first eight alphanumeric characters of DB_UNIQUE_NAME, and \# is the instance number. If you select an administator-managed database, then Oracle Database Configuration Assistant generates the default SID for the instance names, using the format name#, where name is the first eight alphanumeric characters of DB_UNIQUE_NAME, and \# is the instance number. However, during installation or database creation you can specify a nondefault value for the SID. The instance number is automatically added to the end of this string for each instance.

For an Oracle RAC One Node database, the instance name is ORACLE_SID_1, which consists of `_1` appended to the SID prefix. During online relocation, a second instance ORACLE_SID_2 is started, which becomes the only instance after the relocation completes. The next online relocation uses ORACLE_SID_1 for the new instance.

Example 3-1 Global Database Name and Related Initialization Parameters

If your database has a global database name of `orl$racprod2551.example.com` which you supplied during installation, then the following values are used for initialization parameters:

| Parameter      | Value             |
|:---------------|:------------------|
| DB_UNIQUE_NAME | `orl$racprod2551` |
| DB_DOMAIN      | `example.com`     |
| DB_NAME        | `orl$racp`        |

Example 3-2 DB_UNIQUE_NAME and Related ORACLE_SID Values

If the DB_UNIQUE_NAME for a database is `orl$racprod2551`, then the following SID values are used:

| Database or Instance Type                 | Value Used for ORACLE_SID |
|:------------------------------------------|:--------------------------|
| Single-instance Oracle database           | `orlracpr`                |
| Policy-managed Oracle RAC instance        | `orlracpr_1`              |
| Administrator-managed Oracle RAC instance | `orlracpr1`               |
| Oracle RAC One Node database instance     | `orlracpr_1`              |

**Parent topic:** [Selecting Installation Options for Oracle RAC](selecting-installation-options-for-oracle-rac.md)
