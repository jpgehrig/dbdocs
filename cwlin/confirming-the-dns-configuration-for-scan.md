## Confirming the DNS Configuration for SCAN

Use the `nslookup` command to confirm that the DNS is correctly associating the SCAN with the addresses.

**Note:**

All name servers in the DNS configuration for a cluster must resolve to all host names used in the cluster, such as cluster node host name, VIP host name, and SCAN host name.

The following example shows how to use the `nslookup` command to confirm that the DNS is correctly associating the SCAN with the addresses:

    root@node1]$ nslookup mycluster-scan
    Server:         dns.example.com
    Address:        192.0.2.001

    Name:   mycluster-scan.example.com
    Address: 192.0.2.201
    Name:   mycluster-scan.example.com
    Address: 192.0.2.202
    Name:   mycluster-scan.example.com
    Address: 192.0.2.203

After installation, when a client sends a request to the cluster, the Oracle Clusterware SCAN listeners redirect client requests to servers in the cluster.

Oracle strongly recommends that you do not configure SCAN VIP addresses in the hosts file. Use DNS resolution for SCAN VIPs. If you use the hosts file to resolve SCANs, then the SCAN can resolve to one IP address only.

Configuring SCANs in a DNS or a hosts file is the only supported configuration. Configuring SCANs in a Network Information Service (NIS) is not supported.

**Parent topic:** [Oracle Grid Infrastructure IP Name and Address Requirements](oracle-grid-infrastructure-ip-name-and-address-requirements.md)
