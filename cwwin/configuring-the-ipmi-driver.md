## Configuring the IPMI Driver

For Oracle Clusterware to communicate with the BMC, the IPMI driver must be installed permanently on each node, so that it is available on system restarts.

On Windows systems, the implementation assumes the Microsoft IPMI driver (`ipmidrv.sys`) is installed, which is included with the Windows Server 2012 and later versions of the Windows operating system. The driver is included as part of the Hardware Management feature, which includes the driver and the Windows Management Interface (WMI).

**Note:**

An alternate driver (`imbdrv.sys`) is available from Intel as part of Intel Server Control, but this driver has not been tested with Oracle Clusterware.

- [Configuring the Hardware Management Component](configuring-the-hardware-management-component.md)
  Hardware management is installed using the Add/Remove Windows Components Wizard.

**Parent topic:** [Enabling Intelligent Platform Management Interface (IPMI)](enabling-intelligent-platform-management-interface-ipmi.md)
