## Firewall Exceptions for Oracle RAC Database

After installing the Oracle Real Application Clusters (Oracle RAC), you must add executable files to the Windows Firewall exception list.

For the Oracle RAC database, the executable file that require exceptions are:

- `Oracle_home``\bin\oracle.exe` - Oracle RAC database instance

- `Oracle_home``\jdk\bin\java.exe` - For the Oracle Enterprise Manager Database Console

In addition, the following ports should be added to the Windows Firewall exception list:

- Microsoft file sharing system management bus (SMB)

  - TCP ports from 135 through 139

- Direct-hosted SMB traffic without a network basic I/O system (NetBIOS)

  - port 445 (TCP)

**Parent topic:** [Configuring Exceptions for the Windows Firewall](configuring-exceptions-for-the-windows-firewall.md)
