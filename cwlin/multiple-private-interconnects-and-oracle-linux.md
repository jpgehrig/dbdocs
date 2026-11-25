## Multiple Private Interconnects and Oracle Linux

Review this information for settings for the `rp_filter` parameter for Oracle RAC systems that use multiple NICs for the private interconnect.

With Oracle Linux kernel 2.6.31, which also includes Oracle Unbreakable Enterprise Kernel 2.6.32, a bug has been fixed in the Reverse Path Filtering. As a consequence of this correction, Oracle RAC systems that use multiple NICs for the private interconnect now require specific settings for the `rp_filter` parameter. This requirement also applies to all Exadata systems that are running Linux kernel 2.6.32 and above. Without these `rp_filter` parameter settings systems, interconnect packets can be blocked or discarded.

The `rp_filter` values set the Reverse Path filter to no filtering (0), to strict filtering (1), or to loose filtering (2). Set the `rp_filter` value for the private interconnects to either 0 or 2. Setting the private interconnect NIC to 1 can cause connection issues on the private interconnect. It is not considered unsafe to disable or relax this filtering, because the private interconnect should be on a private and isolated network.

For example, where `eth1` and `eth2` are the private interconnect NICs, and `eth0` is the public network NIC, set the `rp_filter` of the private address to 2 (loose filtering), the public address to 1 (strict filtering), using the following entries in `/etc/sysctl.conf`:

    net.ipv4.conf.eth2.rp_filter = 2
    net.ipv4.conf.eth1.rp_filter = 2
    net.ipv4.conf.eth0.rp_filter = 1

**See Also:**

<https://support.oracle.com/rs?type=doc&id=1286796.1> for more information about `rp_filter` for multiple private interconnects and Linux Kernel 2.6.32+

**Parent topic:** [Configuring Networks for Oracle Grid Infrastructure and Oracle RAC](configuring-networks-for-oracle-grid-infrastructure-and-oracle-rac.md)
