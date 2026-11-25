## Domain Delegation to Grid Naming Service

If you are configuring Grid Naming Service (GNS) for a standard cluster, then before installing Oracle Grid Infrastructure you must configure DNS to send to GNS any name resolution requests for the subdomain served by GNS.

The subdomain that GNS serves represents the cluster member nodes.

- [Choosing a Subdomain Name for Use with Grid Naming Service](choosing-a-subdomain-name-for-use-with-grid-naming-service.md)
  To implement GNS, your network administrator must configure the DNS to set up a domain for the cluster, and delegate resolution of that domain to the GNS VIP.
- [Configuring DNS for Cluster Domain Delegation to Grid Naming Service](configuring-dns-for-cluster-domain-delegation-to-grid-naming-service.md)
  If you plan to use Grid Naming Service (GNS) with a delegated domain, then before Oracle Grid Infrastructure installation, configure your domain name server (DNS) to send to GNS name resolution requests for the subdomain GNS serves, which are the cluster member nodes.

**Parent topic:** [Configuring Networks for Oracle Grid Infrastructure and Oracle RAC](configuring-networks-for-oracle-grid-infrastructure-and-oracle-rac.md)
