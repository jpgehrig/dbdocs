## 6 Configuring Networks for Oracle Database

If you install Oracle Databases on servers with multiple Oracle homes, multiple aliases, or without a static IP address, then review these network configuration topics.

If you are installing Oracle Database on a server with a static host name and IP address and at least one network interface, then no special network configuration is required.

**Note:**

If you have a firewall running, ensure that all the required ports are open. See, [Oracle Database Component Port Numbers and Protocols](oracle-database-component-port-numbers-and-protocols.md) for a list of port numbers and protocols configured for Oracle Database components.

- [About Oracle Database Network Configuration Options](about-oracle-database-network-configuration-options.md)
  You can enable database clients to connect to servers associated with multiple IP addresses, and you can install Oracle Database on servers with no network connections, and set up database services after installation.
- [About Assigning Global Database Names During Installation](about-assigning-global-database-names-during-installation.md)
  The database name input field is used to set the DB_NAME, DB_UNIQUE_NAME, and DB_DOMAIN Oracle initialization parameter values.
- [Network Configuration for Computers Completed After Installation](network-configuration-for-computers-completed-after-installation.md)
  You must confirm that a non-networked computer can connect to itself to ensure that you can configure client network resolution after installation. A non-networked computer is a computer that does not have a fixed network address, such as a computer using DHCP.
- [Network Configuration for Multihome Computers](network-configuration-for-multihome-computers.md)
  You must set the `ORACLE_HOSTNAME` environment variable to install Oracle Database on a multihomed computer. A multihomed computer is associated with multiple IP addresses.
- [Setting the ORACLE_HOSTNAME Environment Variable](setting-the-oracle_hostname-environment-variable.md)
  Run the commands shown in this example as the Oracle user account to set the `ORACLE_HOSTNAME` environment variable.
- [Network Configuration for Computers with Multiple Aliases](network-configuration-for-computers-with-multiple-aliases.md)
  You must set the `ORACLE_HOSTNAME` environment variable to install Oracle Database on a multialias computer. A multialias computer is one to which multiple aliases resolve.
