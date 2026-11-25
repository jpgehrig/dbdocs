## Manually Configure Automatic Metric Values

Automatic Metric feature automatically configures the metric for the local routes that are based on link speed. To prevent OUI from selecting the wrong network interface during installation, you must customize the metric values for the public and private network interfaces.

The Automatic Metric feature is enabled by default, and it can also be manually configured to assign a specific metric. The public and private network interface for IPv4 use the Automatic Metric feature of Windows. When the Automatic Metric feature is enabled and using the default values, it can sometimes cause OUI to select the private network interface as the default public host name for the server when installing Oracle Grid Infrastructure.

1.  In Control Panel, double-click Network Connections.
2.  Right-click a network interface, and then click Properties.
3.  Click Internet Protocol (TCP/IP), and then click Properties.
4.  On the General tab, click Advanced.
5.  To specify a metric, on the IP Settings tab, click to clear the Automatic metric check box.
6.  In the Interface Metric field, set the public network interface metric to a lower value than the private network interface. This assigns a higher priority to public network in the binding order.
    For example, if you set the public network interface metric to 100 and the private network interface metric to 300, then the public network is assigned a higher priority than the private network.

**Parent topic:** [Network Configuration Tasks for Windows Server Deployments](network-configuration-tasks-for-windows-server-deployments.md)
