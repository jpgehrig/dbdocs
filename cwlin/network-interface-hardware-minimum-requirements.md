## Network Interface Hardware Minimum Requirements

Review these requirements to ensure that you have the minimum network hardware technology for Oracle Grid Infrastructure clusters.

### Public Network for Each Node

Public networks provide access to clients for database services. Public networks must meet these minimum requirements:

- Adapters: Each node must have at least one public network adapter or network interface cards (NIC).

  Oracle supports the use of link aggregations, bonded, trunked or teamed networks for improved bandwidth and high availability.
  **Note:**

  Refer to the My Oracle Support Note 2646289.1 for a list of supported bonding modes.

- Protocol: Each public interface must support TCP/IP.

### Private Network for Each Node

Private networks (also called interconnects) are networks that only cluster member nodes can access. They use switches for connections. Private networks must meet these minimum requirements:

- Adapters: Each node must have at least one private network adapter or network interface cards (NIC).

  Oracle recommends that you configure interconnects using Redundant Interconnect Usage, in which multiple network adapters are configured with addresses in the link-local range to provide highly available IP (HAIP) addresses for the interconnect. You can configure Redundant Interconnect Usage either during installation, or after installation by using Oracle Interface Configuration Tool (OIFCFG), to provide improved bandwidth and high availability.

  Oracle also supports the use of link aggregations, bonded, trunked or teamed networks for improved bandwidth and high availability.

- Protocol: User datagram protocol (UDP) using high-speed network adapters and switches that support TCP/IP, or Reliable Datagram Sockets (RDS) with Infiniband.

  Switches: You must use switches for interconnects that support TCP/IP. Oracle recommends that you use dedicated switches. The minimum switch speed is 1 Gigabit Ethernet.

  Oracle recommends that you configure Jumbo Frames with an MTU size of 9000 (MTU=9000) on your private network.
  **Note:**

  When configuring Jumbo Frames, ensure that all the components of the private network including host adapters, network drivers, and switches support using Jumbo Frames.

### Local Area Network Technology

Oracle does not support token-rings or crossover cables for the interconnect. Oracle supports Jumbo Frames and Infiniband. When you use Infiniband on the interconnect, Oracle supports using the RDS protocol.

If you have a shared Ethernet VLAN deployment, with shared physical adapter, ensure that you apply standard Ethernet design, deployment, and monitoring best practices to protect against cluster outages and performance degradation due to common shared Ethernet switch network events.

### Storage Networks

Oracle Automatic Storage Management and Oracle Real Application Clusters require network-attached storage.

Oracle Automatic Storage Management (Oracle ASM): The network interfaces used for Oracle Clusterware files are also used for Oracle ASM.

Third-party storage: Oracle recommends that you configure additional interfaces for storage.

**Related Topics**

- [My Oracle Support Note 2646289.1](https://support.oracle.com/rs?type=doc&id=2646289.1)

**Parent topic:** [Configuring Networks for Oracle Grid Infrastructure and Oracle RAC](configuring-networks-for-oracle-grid-infrastructure-and-oracle-rac.md)
