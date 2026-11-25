## Confirming the DNS Configuration for SCAN

You can use the `nslookup` command to confirm that the DNS is correctly associating the SCAN with the addresses.

After installation, when a client sends a request to the cluster, the Oracle Clusterware SCAN listeners redirect client requests to servers in the cluster.

- At a command prompt, use the `nslookup` command and specify the name of the SCAN for your cluster.
  For example:
      C:\> nslookup mycluster-scan
      Server:         dns3.example.com
      Address:        192.0.2.001

      Name:   mycluster-scan.example.com
      Address: 192.0.2.201
      Name:   mycluster-scan.example.com
      Address: 192.0.2.202
      Name:   mycluster-scan.example.com
      Address: 192.0.2.203

**Parent topic:** [Oracle Grid Infrastructure IP Name and Address Requirements](oracle-grid-infrastructure-ip-name-and-address-requirements.md)
