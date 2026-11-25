To configure a GNS client cluster, check to ensure all of the following requirements are completed.

- A GNS server instance must be running on your network, and it must be accessible (for example, not blocked by a firewall).

- All of the node names in the GNS domain must be unique; address ranges and cluster names must be unique for both GNS server and GNS client clusters.

- You must have a GNS client data file that you generated on the GNS server cluster, so that the GNS client cluster has the information needed to delegate its name resolution to the GNS server cluster, and you must have copied that file to the GNS client cluster member node on which you are running the Oracle Grid Infrastructure installation.

**Parent topic:** [IP Name and Address Requirements For Multi-Cluster GNS](ip-name-and-address-requirements-for-multi-cluster-gns.md)
