Intelligent Platform Management Interface (IPMI) provides a set of common interfaces to computer hardware and firmware that system administrators can use to monitor system health and manage the system.

Oracle Clusterware can integrate IPMI to provide failure isolation support and to ensure cluster integrity. You can configure node-termination with IPMI during installation by selecting IPMI from the Failure Isolation Support screen. You can also configure IPMI after installation with `crsctl` commands.

- [Requirements for Enabling IPMI](requirements-for-enabling-ipmi.md)
  You must have the following hardware and software configured to enable cluster nodes to be managed with IPMI:
- [Configuring the IPMI Management Network](configuring-the-ipmi-management-network.md)
  For Oracle Clusterware, you must configure the ILOM/BMC for static IP addresses.
- [Configuring the BMC](configuring-the-bmc.md)

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/oracle-clusterware-administration.md)

**Parent topic:** [Configuring Users, Groups and Environments for Oracle Grid Infrastructure and Oracle Database](configuring-users-groups-and-environments-for-oracle-grid-infrastructure-and-oracle-database.md)
