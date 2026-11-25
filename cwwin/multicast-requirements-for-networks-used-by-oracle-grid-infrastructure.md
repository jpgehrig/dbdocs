## Multicast Requirements for Networks Used by Oracle Grid Infrastructure

On each cluster member node the Oracle multicast DNS (mDNS) daemon uses multicasting on all network interfaces to communicate with other nodes in the cluster.

Multicasting is required on the private interconnect. For this reason, at a minimum, you must enable multicasting for the cluster for the following:

- Across the broadcast domain as defined for the private interconnect

- On the IP address subnet ranges 224.0.0.0/24 and 230.0.1.0/24

You do not need to enable multicast communications across routers.

**Parent topic:** [Configuring Networks for Oracle Grid Infrastructure and Oracle RAC](configuring-networks-for-oracle-grid-infrastructure-and-oracle-rac.md)
