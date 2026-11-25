## Changing the Oracle Services for Microsoft Transaction Server Port

In most cases, you are not required to reconfigure the port number for the Oracle Services for Microsoft Transaction Server.

- If you must change the port number, then you can use the Registry Editor to edit its value in the `HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\OracleMTSRecoveryService\Protid_0` Windows Registry key to any available port within the range 1024 to 65535.
  During installation, Oracle Universal Installer takes the value for the port from the key, if it exists. Otherwise, a free port ranging from 49152 to 65535 is chosen automatically.

**Parent topic:** [Managing Oracle Database Port Numbers](managing-oracle-database-port-numbers.md)
