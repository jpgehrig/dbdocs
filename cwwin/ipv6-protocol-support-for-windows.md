## IPv6 Protocol Support for Windows

Oracle Grid Infrastructure and Oracle RAC support the standard IPv6 address notations specified by RFC 2732 and global and site-local IPv6 addresses as defined by RFC 4193.

Cluster member node interfaces can be configured to use IPv4, IPv6, or both types of Internet protocol addresses. However, be aware of the following:

- Configuring public VIPs: During installation, you can configure VIPs for a given public network as IPv4 or IPv6 types of addresses. You can configure an IPv6 cluster by selecting VIP and SCAN names that resolve to addresses in an IPv6 subnet for the cluster, and selecting that subnet as public during installation. After installation, you can also configure cluster member nodes with a mixture of IPv4 and IPv6 addresses.

  If you install using static virtual IP (VIP) addresses in an IPv4 cluster, then the VIP names you supply during installation should resolve only to IPv4 addresses. If you install using static IPv6 addresses, then the VIP names you supply during installation should resolve only to IPv6 addresses.

  During installation, you cannot configure the cluster with VIP and SCAN names that resolve to both IPv4 and IPv6 addresses. For example, you cannot configure VIPs and SCANS on some cluster member nodes to resolve to IPv4 addresses, and VIPs and SCANs on other cluster member nodes to resolve to IPv6 addresses. Oracle does not support this configuration.

- Configuring private IP interfaces (interconnects): You can configure a network interface to use either the IPv4 protocol, or the IPv6 protocol on a given network

- Redundant network interfaces: If you configure redundant network interfaces for a public or VIP node name, then configure both interfaces of a redundant pair to the same address protocol. Also ensure that private IP interfaces use the same IP protocol. Oracle does not support configuring one interface to support IPv4 addresses and the other to support IPv6 addresses. You must configure both network interfaces of a redundant pair with the same IP protocol.

  GNS or Multi-cluster addresses: Oracle Grid Infrastructure supports IPv4 DHCP addresses, and IPv6 addresses configured with the Stateless Address Autoconfiguration protocol, as described in RFC 2462. Run the `srvctl config network` command to determine if DHCP or stateless address autoconfiguration is being used.

**Note:**

Link-local and site-local IPv6 addresses as defined in RFC 1884 are not supported

**See Also:**

- [RFC 2732](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/cwwin&id=ietf_rfc_2732) for information about IPv6 notational representation

- [RFC 3513](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/cwwin&id=ietf_rfc_3513) for information about proper IPv6 addressing

- [RFC 2462](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/cwwin&id=ietf_rfc_2462) for information about IPv6 Stateless Address Autoconfiguration protocol

- [Oracle Database Net Services Administrator's Guide](../netag/understanding-communication-layers.md) for more information about network communication and IP address protocol options

**Parent topic:** [Network Interface Hardware Requirements](network-interface-hardware-requirements.md)
