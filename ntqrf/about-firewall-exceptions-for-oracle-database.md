For a basic database operation and connectivity from remote clients (SQL\*Plus, OCI, ODBC, OLE DB applications, and so on), add the following executables to the Windows Firewall exception list:

- `Oracle_home``\bin\oracle.exe` - Oracle Database executable

- `Oracle_home``\bin\tnslsnr.exe` - Oracle Listener

For remote monitoring capabilities to be available for a database running on Windows, the following executables must be added to the Windows Firewall exception list:

- `Oracle_home``\bin\emagent.exe` - Oracle Database Control

- `Oracle_home``\jdk\bin\java.exe- `Java Virtual Machine

**Parent topic:** [Overview of Different Executables Added to the Windows Firewall Exception List](overview-of-different-executables.md)
