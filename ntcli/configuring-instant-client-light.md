## Configuring Instant Client Light

To configure Instant Client Light, you must make it the default instead of Instant Client.

To configure Instant Client Light:

1.  In the `ORACLE_BASE``\``ORACLE_CLIENT_HOME` directory, either rename or delete the `oraociei12.dll` file.
    The `oraociei12.dll` file is the main binary for Instant Client.
2.  From the `ORACLE_BASE``\``ORACLE_CLIENT_HOME``\install\instantclient\light` directory, copy the `oraociicus12.dll` file to the `ORACLE_BASE``\``ORACLE_CLIENT_HOME` directory. .
    The `oraociicus12.dll` file is the binary for Instant Client Light.
3.  Ensure that the PATH environment variable points to the `ORACLE_BASE``\``ORACLE_CLIENT_HOME` directory.
    **Note:**

    If the Instant Client `PATH` is not set, then the applications attempt to load the regular Instant Client libraries first. If the applications cannot find these, then they attempt to load the Instant Client Light library next.

**Parent topic:** [Recommended Postinstallation Tasks](recommended-postinstallation-tasks.md)
