## Enabling Intelligent Platform Management Interface (IPMI)

Intelligent Platform Management Interface (IPMI) provides a set of common interfaces to computer hardware and firmware that system administrators can use to monitor system health and manage the system.

Oracle Clusterware can integrate IPMI to provide failure isolation support and to ensure cluster integrity. You can configure node-termination with IPMI during installation by selecting a node-termination protocol, such as IPMI. You can also configure IPMI after installation with `crsctl` commands.

- [Requirements for Enabling IPMI](requirements-for-enabling-ipmi.md)
  Review these hardware and software requirements for enabling cluster nodes to be managed with Intelligent Platform Management Interface (IPMI).
- [Configuring the IPMI Management Network](configuring-the-ipmi-management-network.md)
  You can configure the Baseboard Management Controller (BMC) for Dynamic Host Configuration Protocol (DHCP), or for static IP addresses.
- [Configuring the IPMI Driver](configuring-the-ipmi-driver.md)
  For Oracle Clusterware to communicate with the BMC, the IPMI driver must be installed permanently on each node, so that it is available on system restarts.

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/oracle-clusterware-administration.md)

**Parent topic:** [Configuring Users, Groups and Environments for Oracle Grid Infrastructure and Oracle RAC](configuring-users-groups-and-environments-for-oracle-grid-infrastructure-and-oracle-rac.md)
