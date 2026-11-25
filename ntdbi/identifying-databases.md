## Identifying Databases

The Oracle Database software identifies a database by its global database name.

A global database name consists of the database name and database domain. Usually, the database domain is the same as the network domain, but it need not be. The global database name uniquely distinguishes a database from any other database in the same network. You specify the global database name when you create a database during the installation, or when using Oracle Database Configuration Assistant.

The database name input field is used to set the `DB_NAME`, `DB_UNIQUE_NAME`, and `DB_DOMAIN` Oracle initialization parameter values.

For example:

`sales_world.example.com`

In this example:

- `sales_world` is the name of the database. The database name (`DB_UNIQUE_NAME`) portion is a string of no more than 30 characters that can contain ASCII alphanumeric, underscore (\_), dollar (\$), and pound (#) characters but must begin with an alphabetic character. No other special characters are permitted in a database name.

- `sales_wo` is the `DB_NAME`. The `DB_NAME` initialization parameter specifies a database identifier of up to eight characters.

- `example.com` is the network domain in which the database is located. Together, the database name and the network domain make the global database name unique. The domain portion is a string of no more than 128 characters that can contain alphanumeric, underscore (\_), and pound (#) characters. The `DB_DOMAIN` initialization parameter specifies the domain name.

However, the `DB_NAME` parameter need not necessarily be the first eight characters of `DB_UNIQUE_NAME`.

The `DB_UNIQUE_NAME` parameter and the `DB_DOMAIN` name parameter combine to create the global database name value assigned to the `SERVICE_NAMES` parameter in the initialization parameter file.

The System Identifier (SID) identifies a specific database instance. The SID uniquely distinguishes the instance from any other instance on the same computer. Each database instance requires a unique SID and database name.

For example, if the SID and database name for an Oracle database are `ORCL`, then each database file is located in the `ORACLE_BASE``\oradata\``orcl` directory, and the initialization response file is located in the `ORACLE_BASE``\admin\``orcl``\pfile` directory.

**See Also:**

[Oracle Database Reference](../refrn/DB_UNIQUE_NAME.md)

**Parent topic:** [Getting Started with Oracle Database](getting-started-with-oracle-database.md)
