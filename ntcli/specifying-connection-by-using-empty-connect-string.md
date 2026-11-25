## Specifying a Connection by Using an Empty Connect String and the LOCAL Variable

Describes how to specify a connection to an empty connect string and set the LOCAL environment variable.

You can set the connect string to an empty connect string (""), and then set the LOCAL environment variable to one of the following values:

- A direct address

- Oracle Net keyword-value pair

- A `tnsnames.ora` entry and `TNS_ADMIN` is set to the location of tnsnames.ora

- A tnsnames.ora entry and the following:

  - `tnsnames.ora` file located in` ``ORACLE_HOME``/network/admin`

  - The `ORACLE_HOME` environment variable set to this Oracle home

    This method allows your applications to specify internally a connection string if the application code uses an empty connection string. The benefit of an empty connect string is that the application does not need to specify the `tnsnames.ora` entry. Instead, when a user invokes the application, the location of the database is determined by a script or the environment, depending on where you have set the `LOCAL` environment variable. The disadvantage of using empty strings is that you must configure this additional information for your application to connect to the database.

**Related Topics**

- [Specifying a Connection by Using the Easy Connect Naming Method](specifying-a-connection-by-using-the-easy-connect-naming-method.md)

**Parent topic:** [Connecting Instant Client or Instant Client Light to an Oracle Database](connecting-instant-client-to-an-oracle-db.md)
