## Oracle Flex Cluster DHCP-Assigned Virtual IP (VIP) Addresses

Configure cluster node VIP names for all the cluster nodes.

### Requirements for DHCP-Assigned VIP Addresses

If you want to configure DHCP-assigned VIPs, then during installation, configure cluster node VIP names as follows:

- Automatically Assigned Names: Select the Configure nodes Virtual IPs assigned by the Dynamic Networks option to allow the installer to assign names to VIP addresses generated through DHCP automatically. Addresses are assigned through DHCP, and resolved by GNS. Oracle Clusterware sends DHCP requests with `client ID nodename``-vip` and without a MAC address. You can verify the availability of DHCP addresses using the `cluvfy comp dhcp` command.

**Parent topic:** [Configuration Requirements for Oracle Flex Clusters](configuration-requirements-for-oracle-flex-clusters.md)
