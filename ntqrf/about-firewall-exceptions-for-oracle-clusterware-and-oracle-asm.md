If you installed Oracle Grid Infrastructure on the nodes in your cluster, then you can enable the Windows Firewall only after adding the following executables and ports to the Firewall exception list.

The Firewall Exception list must be updated on each node.

- `Grid_home``\bin\gpnpd.exe` - Grid Plug and Play daemon

- `Grid_home``\bin\oracle.exe` - Oracle ASM executable (if using Oracle ASM for storage)

- `Grid_home``\bin\racgvip.exe` - Virtual Internet Protocol Configuration Assistant

- `Grid_home``\bin\evmd.exe` - OracleEVMService

- `Grid_home``\bin\crsd.exe `- OracleCRService

- `Grid_home``\bin\ocssd.exe` - OracleCSService

- `Grid_home``\bin\octssd.exe `- Cluster Time Synchronization Service daemon

- `Grid_home``\bin\mDNSResponder.exe` - multicast-DNS Responder Daemon

- `Grid_home``\bin\gipcd.exe` - Grid IPC daemon

- `Grid_home``\bin\gnsd.exe` - Grid Naming Service daemon

- `Grid_home``\bin\ohasd.exe` - OracleOHService

- `Grid_home``\bin\TNSLSNR.EXE` - SCAN listener and local listener for Oracle Database and Oracle ASM

- `Grid_home``\opmn\bin\ons.exe` - Oracle Notification Service

- `Grid_home``\jdk\jre\bin\java.exe` - Java Virtual Machine

**Parent topic:** [Overview of Different Executables Added to the Windows Firewall Exception List](overview-of-different-executables.md)
