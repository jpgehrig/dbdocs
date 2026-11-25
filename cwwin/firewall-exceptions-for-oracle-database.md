## Firewall Exceptions for Oracle Database

For basic database operation and connectivity from remote clients, such as SQL\*Plus, Oracle Call Interface (OCI), Open Database Connectivity (ODBC), and so on, you must add executable files to the Windows Firewall exception list.

The following executable files must be added to the Windows Firewall exception list:

- `Oracle_home``\bin\oracle.exe` - Oracle Database executable

- `Oracle_home``\bin\tnslsnr.exe` - Oracle Listener

If you use remote monitoring capabilities for your database, the following executable file must be added to the Windows Firewall exception list:

`Oracle_home``\jdk\bin\java.exe` - Java Virtual Machine (JVM) for Oracle Enterprise Manager

**Parent topic:** [Configuring Exceptions for the Windows Firewall](configuring-exceptions-for-the-windows-firewall.md)
