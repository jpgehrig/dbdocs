## Firewall Exceptions for Oracle Clusterware and Oracle ASM

If you installed the Oracle Grid Infrastructure software on the nodes in your cluster, then you can enable the Windows Firewall only after adding certain executable files and ports to the Firewall exception list.

The Firewall exception list must be updated on each node.

- `Grid_home``\bin\gpnpd.exe` - Grid Plug and Play daemon

- `Grid_home``\bin\oracle.exe` - Oracle Automatic Storage Management (Oracle ASM) executable file (if using Oracle ASM for storage)

- `Grid_home``\bin\racgvip.exe` - Virtual Internet Protocol Configuration Assistant

- `Grid_home``\bin\evmd.exe` - OracleEVMService

- `Grid_home``\bin\crsd.exe` - OracleCRService

- `Grid_home``\bin\ocssd.exe` - OracleCSService

- `Grid_home``\bin\octssd.exe` - Cluster Time Synchronization Service daemon

- `Grid_home``\bin\mDNSResponder.exe` - multicast-domain name system (DNS) Responder Daemon

- `Grid_home``\bin\gipcd.exe` - Grid inter-process communication (IPC) daemon

- `Grid_home``\bin\gnsd.exe` - Grid Naming Service (GNS) daemon

- `Grid_home``\bin\ohasd.exe` - OracleOHService

- `Grid_home``\bin\TNSLSNR.EXE` - single client access name (SCAN) listener and local listener for Oracle RAC database and Oracle ASM

- `Grid_home``\opmn\bin\ons.exe` - Oracle Notification Service (ONS)

- `Grid_home``\jdk\jre\bin\java.exe` - JVM

- `Grid_home``\bin\oraagent.exe` - Oracle Agent

- `Grid_home``\bin\evmlogger.exe`

- `Grid_home``\bin\cssdagent.exe`

- `Grid_home``\bin\cssdmonitor.exe`

- `Grid_home``\bin\osysmond.exe` - System Monitor Service

- `Grid_home``\bin\orarootagent.exe` - Oracle Root Agent

- `Grid_home``\bin\ologgerd.exe` - Cluster Logger Service

**Parent topic:** [Configuring Exceptions for the Windows Firewall](configuring-exceptions-for-the-windows-firewall.md)
