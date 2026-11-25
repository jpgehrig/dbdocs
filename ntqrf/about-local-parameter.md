You can use the parameter `LOCAL` to connect to Oracle Database without specifying a connect identifier in the connect string.

The value of the parameter `LOCAL` is any connect identifier, such as a net service name. For example, if the parameter `LOCAL` is specified as `finance`, you can connect to a database from SQL\*Plus with:

    SQL> CONNECT SMITH
    Enter password: password

rather than

    SQL> CONNECT SMITH@finance
    Enter password: password

Oracle Net checks if `LOCAL` is defined as an environment variable or as a parameter in the registry, and uses `finance` as the service name. If it exists, then Oracle Net connects.

**Parent topic:** [Overview of Optional Configuration Parameters](overview-of-optional-configuration-parameters.md)
