## Installing a Loopback Adapter

A loopback adapter is required if you are installing on a non-networked computer to connect the computer to a network after the installation.

When you install a loopback adapter, the loopback adapter assigns a local IP address for your computer. After the loopback adapter is installed, there are at least two network adapters on your computer: your own network adapter and the loopback adapter. To run Oracle Database on Windows, set the loopback adapter as the primary adapter.

You can change the bind order for the adapters without reinstalling the loopback adapter. The bind order of the adapters to the protocol indicates the order in which the adapters are used. When the loopback adapter is used first for the TCP/IP protocol, all programs that access TCP/IP first probe the loopback adapter. The local address is used for tools, such as Oracle Enterprise Manager. Applications that use a different Ethernet segment are routed to the network card.

- [Checking if a Loopback Adapter is Installed on Your Computer](checking-if-loopback-adapter-is-installed-on-computer.md)
  Review this section to verify if a loopback adapter is installed on your computer by running the `ipconfig /all` command.
- [Installing a Loopback Adapter](installing-loopback-adapter.md)
  Use this procedure to install a Loopback Adapter or a Microsoft KM-TEST Loopback Adapter on different Windows versions.
- [Removing a Loopback Adapter](removing-loopback-adapter.md)
  Use this procedure to remove a Loopback Adapter or a Microsoft KM-TEST Loopback Adapter on different Windows versions.

**Related Topics**

- [Installing Oracle Database on Nonnetworked Computers](installing-oracle-database-on-nonnetworked-computers.md)

**Parent topic:** [Configuring Networks for Oracle Database](configuring-networks-for-oracle-database.md)
