## Intended Use of Network Adapters

During installation, you are asked to identify the planned use for each network adapter (or network interface) that Oracle Universal Installer (OUI) detects on your cluster node.

Each NIC performs only one of the following roles:

- Public
- Private
- ASM
- ASM and Private
- Do Not Use

You must use the same private adapters for both Oracle Clusterware and Oracle RAC. The precise configuration you choose for your network depends on the size and use of the cluster you want to configure, and the level of availability you require. Network interfaces must be at least 1 GbE, with 10 GbE recommended.

For network adapters that you plan to use for other purposes, for example, an adapter dedicated to a non-Oracle network file system, you must identify those network adapters as "do not use" adapters so that Oracle Clusterware ignores them.

If certified Network Attached Storage (NAS) is used for Oracle RAC and this storage is connected through Ethernet-based networks, then you must have a third network interface for NAS I/O. Failing to provide three separate interfaces in this case can cause performance and stability problems under load.

Oracle Flex ASM can use either the same private networks as Oracle Clusterware, or use its own dedicated private networks. If you plan to have other clusters (Oracle ASM client clusters) access the storage in an Oracle Flex ASM cluster, then you should configure a separate ASM network as a private network that connects the client clusters to the Oracle Flex ASM cluster.

If you require high availability or load balancing for public adapters, then use a third-party solution. Typically, bonding, trunking or similar technologies can be used for this purpose.

**Parent topic:** [Configuring Networks for Oracle Grid Infrastructure and Oracle RAC](configuring-networks-for-oracle-grid-infrastructure-and-oracle-rac.md)
