## Server Configuration Checklist for Oracle Fleet Patching and Provisioning

Use this checklist to check minimum server configuration requirements for Oracle Fleet Patching and Provisioning (Oracle FPP).

Table 2-1 Server Configuration Checklist for Oracle Fleet Patching and Provisioning

| Check                                                   | Task                                                                                                                                                                                                                                                                                                             |
|:--------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Oracle Grid Infrastructure installation                 | Install Oracle Grid Infrastructure on a new cluster on which you want to configure Oracle FPP.<br>**Note:**<br>You can not configure Oracle FPP Server on an Oracle Restart server.                                                                                                                              |
| Operating System Kernel version                         | Install or upgrade the operating system kernel to a version for which an Oracle ACFS kernel module is already built.                                                                                                                                                                                             |
| Grid Infrastructure Management Repository configuration | Make sure that the Grid Infrastructure Management Repository (GIMR) is configured and running on your cluster. If GIMR was not configured as part of the Oracle Grid Infrastructure installation, then add a new GIMR to your cluster as described in Oracle Grid Infrastructure Installation and Upgrade Guide. |
| Oracle FPP server storage                               | Allocate a minimum of 100 GB additional disk space to the Oracle Automation Storage Management (Oracle ASM) disk group that is used by the Oracle FPP Server.                                                                                                                                                    |
| Oracle FPP server network                               | Create one Grid Naming Service Virtual IP Address (GNS VIP) without zone delegation.                                                                                                                                                                                                                             |
| Firewall                                                | Make sure that the ports used by Oracle FPP Server and Client are not filtered by firewalls. Please refer to Table 2-2 Fleet Patching and Provisioning Communication Ports                                                                                                                                       |

**Related Topics**

- [Oracle Grid Infrastructure Installation and Upgrade Guide for Linux](../cwlin/adding-gimr-to-existing-cluster.md)

**Parent topic:** [Configuring Oracle Fleet Patching and Provisioning Server](configuring-oracle-fpp-server.md)
