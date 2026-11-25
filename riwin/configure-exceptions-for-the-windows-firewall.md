## Configure Exceptions for the Windows Firewall

If the Windows Firewall feature is enabled on one or more nodes of your Oracle RAC cluster, then you must create exceptions for Oracle RAC applications and ports.

Enabling the Windows Firewall feature on one or more nodes in your cluster blocks virtually all TCP network ports to incoming connections. As a result, any Oracle product that listens for incoming connections on a TCP port does not receive any of those connection requests and the clients making those connection requests report errors.

Review the instructions in Oracle Grid Infrastructure Installation and Upgrade Guide for Microsoft Windows for details on how to configure exceptions for the Windows Firewall, if you have not done so already as part of the Oracle Grid Infrastructure installation.

**Related Topics**

- [Oracle Grid Infrastructure Installation and Upgrade Guide for Microsoft Windows](../cwwin/configuring-exceptions-for-the-windows-firewall.md)

**Parent topic:** [Required Postinstallation Tasks](required-postinstallation-tasks.md)
