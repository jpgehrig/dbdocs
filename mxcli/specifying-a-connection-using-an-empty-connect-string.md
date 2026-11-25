You can set the connect string to an empty connect string (""), and then set the `TWO_TASK` environment variable to one of the following values:

- A direct address, as described under "[Specifying a Connection by Using the Easy Connect Naming Method](specifying-a-connection-by-using-the-easy-connect-naming-method.md)"

- Oracle Net keyword-value pair

- A `tnsnames.ora` entry and `TNS_ADMIN` is set to the location of `tnsnames.ora`

This method allows the applications to specify internally a connection string if the application code itself uses an empty connection string. The benefit of an empty connect string is that the application itself does not have to specify the `tnsnames.ora` entry. Instead, when a user starts the application, the location of the database is determined by a script or the environment, depending on where you have set the `TWO_TASK` environment variable. The disadvantage of using empty strings is that you must configure this additional information in order for the application to connect to the database.

**Parent topic:** [Connecting Instant Client or Instant Client Light to an Oracle Database](connecting-instant-client-or-instant-client-light.md)
