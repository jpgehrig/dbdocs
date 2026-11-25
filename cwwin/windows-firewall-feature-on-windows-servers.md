## Windows Firewall Feature on Windows Servers

When installing Oracle Grid Infrastructure software or Oracle RAC software on Windows servers, it is mandatory to disable the Windows Firewall feature.

If the Windows Firewall is enabled, then remote copy and configuration assistants such as virtual IP configuration assistant (VIPCA), Network Configuration Assistant (NETCA), and Oracle Database Configuration Assistant (DBCA) will fail during Oracle RAC installation. Thus, you must disable the firewall on all the nodes of a cluster before performing an Oracle RAC installation.

**Note:**

The Windows Firewall should never be enabled on a NIC that is used as a cluster interconnect (private network interface) or for accessing an Oracle ASM network.

After the installation is successful, you can enable the Windows Firewall for the public connections. However, to ensure correct operation of the Oracle software, you must add certain executables and ports to the Firewall exception list on all the nodes of a cluster.

Additionally, the Windows Firewall must be disabled on all the nodes in the cluster before performing any clusterwide configuration changes, such as:

- Adding a node

- Deleting a node

- Upgrading to patch release

- Applying a patch bundle or an emergency patch

If you do not disable the Windows Firewall before performing these actions, then the changes might not be propagated correctly to all the nodes of the cluster.

**Related Topics**

- [Configuring Exceptions for the Windows Firewall](configuring-exceptions-for-the-windows-firewall.md)

**Parent topic:** [Configuring Operating Systems for Oracle Grid Infrastructure and Oracle RAC](configuring-operating-systems-for-oracle-grid-infrastructure-and-oracle-rac.md)
