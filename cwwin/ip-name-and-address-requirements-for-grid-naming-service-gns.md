## IP Name and Address Requirements For Grid Naming Service (GNS)

The network administration must configure the domain name server (DNS) to delegate resolution requests for cluster names (any names in the subdomain delegated to the cluster) to the GNS.

If you enable Grid Naming Service (GNS), then name resolution requests to the cluster are delegated to the GNS, which listens on the GNS VIP address. When a request comes to the domain, GNS processes the requests and responds with the appropriate addresses for the name requested. To use GNS, you must specify a static IP address for the GNS VIP address.

**Note:**

You cannot use GNS with another multicast DNS. To use GNS, disable any third-party mDNS daemons on your system.

**Related Topics**

- [Configuring DNS for Domain Delegation to Grid Naming Service](configuring-dns-for-domain-delegation-to-grid-naming-service.md)

**Parent topic:** [Oracle Grid Infrastructure IP Name and Address Requirements](oracle-grid-infrastructure-ip-name-and-address-requirements.md)
