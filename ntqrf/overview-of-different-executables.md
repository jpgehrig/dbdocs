Lists the executables that listen on TCP ports on Windows, along with a brief description of the executable.

Oracle recommends that these executables (if in use and accepting connections from a remote, client computer) be added to the exceptions list for the Windows Firewall to ensure correct operation. In addition, if multiple Oracle homes are in use, then create firewall exceptions for the same executable, for example, `oracle.exe`, multiple times, once for each Oracle home from which that executable loads.

- [About Firewall Exceptions for Oracle Database](about-firewall-exceptions-for-oracle-database.md)
  For a basic database operation and connectivity from remote clients (SQL\*Plus, OCI, ODBC, OLE DB applications, and so on), add the following executables to the Windows Firewall exception list:
- [About Firewall Exceptions for Oracle Database Examples](about-firewall-exceptions-for-oracle-database-examples.md)
  After installing Oracle Database Examples, add the following executables to the Windows Firewall exception list:
- [About Firewall Exceptions for Oracle Gateways](about-firewall-exceptions-for-oracle-gateways.md)
  If your Oracle database interacts with non-Oracle software through a gateway, then you must add the gateway executable to the Windows Firewall exception list.
- [About Firewall Exceptions for Oracle Clusterware and Oracle ASM](about-firewall-exceptions-for-oracle-clusterware-and-oracle-asm.md)
  If you installed Oracle Grid Infrastructure on the nodes in your cluster, then you can enable the Windows Firewall only after adding the following executables and ports to the Firewall exception list.
- [About Firewall Exceptions for Other Oracle Products](about-firewall-exceptions-for-other-oracle-products.md)
  In addition to all the previously listed exceptions, if you use any of the Oracle software listed, then you must create an exception for Windows Firewall for the associated executable.

**Parent topic:** [About Oracle Executables Requiring Windows Firewall Exceptions](about-oracle-executables-requiring-windows-firewall-exceptions.md)
