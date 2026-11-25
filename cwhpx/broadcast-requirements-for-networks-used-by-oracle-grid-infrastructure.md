Broadcast communications (ARP and UDP) must work properly across all the public and private interfaces configured for use by Oracle Grid Infrastructure.

The broadcast must work across any configured VLANs as used by the public or private interfaces.

When configuring public and private network interfaces for Oracle RAC, you must enable Address Resolution Protocol (ARP). Highly Available IP (HAIP) addresses do not require ARP on the public network, but for VIP failover, you need to enable ARP. Do not configure `NOARP`.

**Parent topic:** [Configuring Networks for Oracle Grid Infrastructure and Oracle RAC](configuring-networks-for-oracle-grid-infrastructure-and-oracle-rac.md)
