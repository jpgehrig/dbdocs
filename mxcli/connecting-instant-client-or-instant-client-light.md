Use one of the following methods to specify the database connection information for the instant client application:

- For OCI and OCCI programs, use the following connection string format:

  `host[:port][/service_name][:server][/instance_name]`

- Set the `TNS_ADMIN` environment variable to specify the location of the `tnsnames.ora` file and specify a service name from that file.

- Set the `TNS_ADMIN ` and the `TWO_TASK` environment variables to specify a service name from the `tnsnames.ora` file.

  **Note:**

  You do not need to specify the `ORACLE_HOME` variable.

After checking the environment variable, you can use any of the following methods to specify Oracle Database connection information for client applications:

- [Specifying a Connection by Using the Easy Connect Naming Method](specifying-a-connection-by-using-the-easy-connect-naming-method.md)
- [Specifying a Connection Using an Empty Connect String and TWO_TASK](specifying-a-connection-using-an-empty-connect-string.md)

**Parent topic:** [Recommended Postinstallation Tasks](recommended-post-installation-tasks.md)
