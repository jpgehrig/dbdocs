The database name input field is used to set the DB_NAME, DB_UNIQUE_NAME, and DB_DOMAIN Oracle initialization parameter values.

The Oracle Database software identifies a database by its global database name. A global database name consists of the database name and database domain. Usually, the database domain is the same as the network domain, but it need not be. The global database name uniquely distinguishes a database from any other database in the same network. You specify the global database name when you create a database during the installation or using the Oracle Database Configuration Assistant.

For example:

    sales.us.example.com

Here:

- `sales.us` is the name of the database. The database name, DB_UNIQUE_NAME, portion is a string of no more than 30 characters that can contain alphanumeric characters, underscore (\_), dollar sign (\$), and pound sign (#) but must begin with an alphabetic character. No other special characters are permitted in a database name.

- `sales.us` is also the DB_NAME. The DB_NAME initialization parameter specifies a database identifier of up to eight characters.

- `example.com` is the database domain in which the database is located. In this example, the database domain equals the network domain. Together, the database name and the database domain make the global database name unique. The domain portion is a string of no more than 128 characters that can contain alphanumeric characters, underscore (\_), and pound sign (#). The DB_DOMAIN initialization parameter specifies the database domain name.

However, the DB_NAME parameter need not necessarily be the first eight characters of DB_UNIQUE_NAME.

The DB_NAME parameter and the DB_DOMAIN parameter combine to create the global database name value.

The system identifier (SID) identifies a specific database instance. The SID uniquely distinguishes the instance from any other instance on the same computer. Each database instance requires a unique SID and database name. In most cases, the SID equals the database name portion of the global database name.

**Related Topics**

- [Oracle Database Reference](../refrn/DB_UNIQUE_NAME.md)
- [Oracle Database Administrator's Guide](../admin/managing-a-distributed-database.md)

**Parent topic:** [Configuring Networks for Oracle Database](configuring-networks-for-oracle-database.md)
