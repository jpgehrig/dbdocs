## Configuring GNS Client Clusters

Review these requirements to configure GNS client clusters.

- To configure a GNS Client cluster, check to ensure all of the following requirements are completed:
  - A GNS Server instance must be running on your network, and it must be accessible (for example, not blocked by a firewall)

  - All of the node names in the GNS domain must be unique; address ranges and cluster names must be unique for both GNS Server and GNS Client clusters.

  - You must have a GNS Client data file that you generated on the GNS Server cluster, so that the GNS Client cluster has the information needed to delegate its name resolution to the GNS Server cluster, and you must have copied that file to the GNS Client cluster member node on which you run the Oracle Grid Infrastructure installation.

**Parent topic:** [IP Name and Address Requirements For Multi-Cluster GNS](ip-name-and-address-requirements-for-multi-cluster-gns.md)
