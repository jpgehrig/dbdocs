## Enabling Intelligent Platform Management Interface (IPMI)

Intelligent Platform Management Interface (IPMI) provides a set of common interfaces to computer hardware and firmware that system administrators can use to monitor system health and manage the system.

Oracle Clusterware can integrate IPMI to provide failure isolation support and to ensure cluster integrity. You can configure node-termination with IPMI during installation by selecting IPMI from the Failure Isolation Support screen. You can also configure IPMI after installation with `crsctl` commands.

- [Requirements for Enabling IPMI](requirements-for-enabling-ipmi.md)
  You must have the following hardware and software configured to enable cluster nodes to be managed with IPMI:
- [Configuring the IPMI Management Network](configuring-the-ipmi-management-network.md)
  You can configure the BMC for DHCP, or for static IP addresses. Oracle recommends that you configure the BMC for dynamic IP address assignment using DHCP. To use this option, you must have a DHCP server configured to assign the BMC IP addresses.
- [Configuring the Open IPMI Driver](configuring-the-open-ipmi-driver.md)
  On Linux systems, the OpenIPMI driver is the supported driver for Oracle Clusterware deployments with IPMI. You can install and configure the driver dynamically by manually loading the required modules.
- [Configuring the BMC](configuring-the-bmc.md)
  Configure BMC on each node for remote control using LAN for IPMI-based node fencing to function properly.
- [Example of BMC Configuration Using IPMItool](example-of-bmc-configuration-using-ipmitool.md)
  The following is an example of configuring BMC using `ipmitool` (version 1.8.6).

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/oracle-clusterware-administration.md)

**Parent topic:** [Configuring Users, Groups and Environments for Oracle Grid Infrastructure and Oracle Database](configuring-users-groups-and-environments-for-oracle-grid-infrastructure-and-oracle-database.md)
