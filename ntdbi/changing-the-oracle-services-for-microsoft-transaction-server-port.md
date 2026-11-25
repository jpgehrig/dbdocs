## Changing the Oracle Services for Microsoft Transaction Server Port

In most cases, you need not reconfigure the port number.

If you must, then you can use the Registry Editor to edit its value in the `HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\OracleMTSRecoveryService\Protid_0` Registry Editor key to any available port within the range `1024 to 65535`.

During installation, Oracle Universal Installer takes the value for the port from the key, if it exists. Otherwise, a free port ranging from `49152 to 65535` is chosen.

**Parent topic:** [Managing Oracle Database Port Numbers](managing-oracle-database-port-numbers.md)
