## Network Configuration Tasks for Windows Server Deployments

Microsoft Windows Server has many unique networking features. Some of these features require special configuration to enable Oracle software to run correctly on Windows Server.

- [Disabling Windows Media Sensing](disabling-windows-media-sensing.md)
  Windows Media Sensing must be disabled for the private network adapters.
- [Deconfigure DNS Registration for Public Network Adapter](deconfigure-dns-registration-for-public-network-adapter.md)
  To prevent Windows Server from potentially registering the wrong IP addresses for the node in DNS after a server restart, you must deconfigure the "Register this connection's addresses in DNS" option for the public network adapters.
- [Manually Configure Automatic Metric Values](manually-configure-automatic-metric-values.md)
  Automatic Metric feature automatically configures the metric for the local routes that are based on link speed. To prevent OUI from selecting the wrong network interface during installation, you must customize the metric values for the public and private network interfaces.
- [Setting UDP and TCP Dynamic Port Range for Oracle RAC Installations](setting-udp-and-tcp-dynamic-port-range-for-oracle-rac-installations.md)
  For certain configurations of Oracle RAC in high load environments it is possible for the system to exhaust the available number of sockets. To avoid this problem, expand the dynamic port range for both UDP and TCP.

**Parent topic:** [Configuring Networks for Oracle Grid Infrastructure and Oracle RAC](configuring-networks-for-oracle-grid-infrastructure-and-oracle-rac.md)
