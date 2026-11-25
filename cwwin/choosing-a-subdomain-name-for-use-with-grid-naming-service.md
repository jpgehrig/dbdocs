## Choosing a Subdomain Name for Use with Grid Naming Service

To implement GNS, your network administrator must configure the DNS to set up a domain for the cluster, and delegate resolution of that domain to the GNS VIP.

The subdomain name, can be any supported DNS name such as `sales-cluster.rac.com`. You can use a separate domain, or you can create a subdomain of an existing domain for the cluster.

Oracle recommends that the subdomain name be distinct from your corporate domain. For example, if your corporate domain is `mycorp.example.com`, the subdomain for GNS might be `rac-gns.com`.

If the subdomain is not distinct, then it should be for the exclusive use of GNS. For example, if you delegate the subdomain `mydomain.example.com` to GNS, then there should be no other domains that share it such as `lab1.mydomain.example.com`.

[Oracle Clusterware Administration and Deployment Guide](../cwadd/oracle-clusterware-administration.md)

[Cluster Name and SCAN Requirements](cluster-name-and-scan-requirements.md)

**Parent topic:** [Domain Delegation to Grid Naming Service](domain-delegation-to-grid-naming-service.md)
