## Deconfigure DNS Registration for Public Network Adapter

To prevent Windows Server from potentially registering the wrong IP addresses for the node in DNS after a server restart, you must deconfigure the "Register this connection's addresses in DNS" option for the public network adapters.

Due to a change in functionality in the Windows Server 2008 operating system, the DNS client service registers all of the network connections of a computer in DNS. In earlier versions of Windows Server, the DNS client service registered only the primary, or first, network adapter IP address in DNS.

1.  Start the Windows Server Manager application.
2.  Select View Network Connections.
3.  Right-click the network adapter that provides the Public network interface and select Properties.
4.  Select the Networking tab, and then select Internet Protocol Version 4 (TCP/IPv4).
    **Note:**

    If you configure this setting in IPv4, then Windows automatically configures the same setting for IPv6
5.  Click Properties.
6.  On the General tab, click Advanced.
7.  Select the DNS tab.
8.  Deselect Register this connection's addresses in DNS.

**Related Topics**

- [DNS Best Practices](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ff807401(v=ws.10))

**Parent topic:** [Network Configuration Tasks for Windows Server Deployments](network-configuration-tasks-for-windows-server-deployments.md)
