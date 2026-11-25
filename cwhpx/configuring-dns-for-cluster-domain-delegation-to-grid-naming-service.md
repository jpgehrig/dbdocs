If you plan to use Grid Naming Service (GNS) with a delegated domain, then before Oracle Grid Infrastructure installation, configure your domain name server (DNS) to send to GNS name resolution requests for the subdomain GNS serves, which are the cluster member nodes.

GNS domain delegation is mandatory with dynamic public networks (DHCP, autoconfiguration). GNS domain delegation is not required with static public networks (static addresses, manual configuration).

The following is an overview of the steps to be performed for domain delegation. Your actual procedure may be different from this example.

Configure the DNS to send GNS name resolution requests using delegation:

1.  In the DNS, create an entry for the GNS virtual IP address, where the address uses the form `gns-server.clustername.domainname`. For example, where the cluster name is `mycluster`, and the domain name is example.com, and the IP address is `192.0.2.1`, create an entry similar to the following:

        mycluster-gns-vip.example.com  A  192.0.2.1

    The address you provide must be routable.

2.  Set up forwarding of the GNS subdomain to the GNS virtual IP address, so that GNS resolves addresses to the GNS subdomain. To do this, create a `BIND` configuration entry similar to the following for the delegated domain, where `cluster01.example.com` is the subdomain you want to delegate:

        cluster01.example.com  NS  mycluster-gns-vip.example.com

3.  When using GNS, you must configure `resolve.conf` on the nodes in the cluster (or the file on your system that provides resolution information) to contain name server entries that are resolvable to corporate DNS servers. The total timeout period configured—a combination of options attempts (retries) and options timeout (exponential backoff)—should be less than 30 seconds. For example, where `xxx.xxx.xxx.42` and `xxx.xxx.xxx.15` are valid name server addresses in your network, provide an entry similar to the following in `/etc/resolv.conf`:

        options attempts: 2
        options timeout: 1

        search cluster01.example.com example.com
        nameserver xxx.xxx.xxx.42
        nameserver xxx.xxx.xxx.15

    `/etc/nsswitch.conf` controls name service lookup order. In some system configurations, the Network Information System (NIS) can cause problems with SCAN address resolution. Oracle recommends that you place the NIS entry at the end of the search list. For example:

        /etc/nsswitch.conf
             hosts:    files   dns   nis

Be aware that use of NIS is a frequent source of problems when doing cable pull tests, as host name and user name resolution can fail.

**Parent topic:** [Domain Delegation to Grid Naming Service](domain-delegation-to-grid-naming-service.md)
