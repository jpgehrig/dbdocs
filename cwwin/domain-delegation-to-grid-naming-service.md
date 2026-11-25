## Domain Delegation to Grid Naming Service

If you are configuring Grid Naming Service (GNS) for a standard cluster, then before installing Oracle Grid Infrastructure you must configure DNS to send to GNS any name resolution requests for the subdomain served by GNS.

The subdomain that GNS serves represents the cluster member nodes.

- [Choosing a Subdomain Name for Use with Grid Naming Service](choosing-a-subdomain-name-for-use-with-grid-naming-service.md)
  To implement GNS, your network administrator must configure the DNS to set up a domain for the cluster, and delegate resolution of that domain to the GNS VIP.
- [Configuring DNS for Domain Delegation to Grid Naming Service](configuring-dns-for-domain-delegation-to-grid-naming-service.md)
  You must configure the DNS to send GNS name resolution requests using DNS forwarders.

**Parent topic:** [Oracle Grid Infrastructure IP Name and Address Requirements](oracle-grid-infrastructure-ip-name-and-address-requirements.md)
