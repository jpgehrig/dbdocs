## Determining if an Oracle Home is Read-Only

You can use the Registry Editor to determine if your Oracle home is a read/write or read-only Oracle home.

Start Registry Editor and navigate to the `ORACLE_HOME_READONLY` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\KEY_``OracleHomeName` Windows Registry key.

The default value for the `ORACLE_HOME_READONLY` parameter appears as `N`. The `ORACLE_HOME_READONLY` parameter value appears as `Y` if your Oracle home is in a read-only mode. Do not modify this value.

**Parent topic:** [Configuring Read-Only Oracle Homes](configuring-read-only-oracle-homes1.md)
