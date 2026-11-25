## Configuring Exceptions for the Windows Firewall

To enable Oracle software to accept connection requests, you must configure the Windows Firewall by either opening up specific static transmission control protocol (TCP) ports in the firewall or by creating exceptions for specific executable files so they can receive connection requests on any ports they choose.

Review the list the Oracle Database executable files that listen on TCP ports on Windows, along with a brief description of the executable file. It is recommended to add these executable files (if in use and accepting connections from a remote, client computer) to the exceptions list for the Windows Firewall to ensure correct operation. In addition, if multiple Oracle homes are in use, firewall exceptions may have to be created for the same executable file, for example, `oracle.exe`, multiple times, once for each Oracle home from which that executable file loads.

- [About Configuring Exceptions for the Windows Firewall](about-configuring-exceptions-for-the-windows-firewall.md)
  You must configure exceptions for the Windows Firewall to allow successful incoming connections to the Oracle software.
- [Firewall Exceptions for Oracle Database](firewall-exceptions-for-oracle-database.md)
  For basic database operation and connectivity from remote clients, such as SQL\*Plus, Oracle Call Interface (OCI), Open Database Connectivity (ODBC), and so on, you must add executable files to the Windows Firewall exception list.
- [Firewall Exceptions for Oracle Database Examples (or the Companion CD)](firewall-exceptions-for-oracle-database-examples-or-companion-cd.md)
  After installing the Oracle Database Companion CD, you must add executable files to the Windows Firewall exception list.
- [Firewall Exceptions for Oracle Gateways](firewall-exceptions-for-oracle-gateways.md)
  If your Oracle database interacts with non-Oracle software through a gateway, then you must add the gateway executable file to the Windows Firewall exception list.
- [Firewall Exceptions for Oracle Clusterware and Oracle ASM](firewall-exceptions-for-oracle-clusterware-and-oracle-asm.md)
  If you installed the Oracle Grid Infrastructure software on the nodes in your cluster, then you can enable the Windows Firewall only after adding certain executable files and ports to the Firewall exception list.
- [Firewall Exceptions for Oracle RAC Database](firewall-exceptions-for-oracle-rac-database.md)
  After installing the Oracle Real Application Clusters (Oracle RAC), you must add executable files to the Windows Firewall exception list.
- [Firewall Exceptions for Other Oracle Products](firewall-exceptions-for-other-oracle-products.md)
  In additional to all the previously listed exceptions, if you use any of the Oracle software listed in, then you must create an exception for Windows Firewall for the associated executable file.
- [Troubleshooting Windows Firewall Exceptions](troubleshooting-windows-firewall-exceptions.md)
  If you cannot establish certain connections even after granting exceptions to the executable files, then follow these steps to troubleshoot the installation.

**Parent topic:** [Required Postinstallation Tasks](required-postinstallation-tasks.md)
