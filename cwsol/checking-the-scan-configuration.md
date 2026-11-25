The Single Client Access Name (SCAN) is a name that is used to provide service access for clients to the cluster. Because the SCAN is associated with the cluster as a whole, rather than to a particular node, the SCAN makes it possible to add or remove nodes from the cluster without needing to reconfigure clients.

The Single Client Access Name (SCAN) also adds location independence for the databases, so that client configuration does not have to depend on which nodes are running a particular database instance. Clients can continue to access the cluster in the same way as with previous releases, but Oracle recommends that clients accessing the cluster use the SCAN.

You can use the command `cluvfy comp scan` (located in Grid home`/bin`) to confirm that the DNS is correctly associating the SCAN with the addresses. For example:

    $cluvfy comp scan

    Verifying Single Client Access Name (SCAN) ...
      Verifying DNS/NIS name service 'rws127064-clu-scan.rws127064-clu.rws12706410644.example.com' ...
        Verifying Name Service Switch Configuration File Integrity ...PASSED
      Verifying DNS/NIS name service 'rws127064-clu-scan.rws127064-clu.rws12706410644.example.com' ...PASSED
    Verifying Single Client Access Name (SCAN) ...PASSED

    Verification of SCAN was successful.

    CVU operation performed: SCAN
    Date: Jul 29, 2016 1:42:41 AM
    CVU home: /u01/crshome/
    User: crsusr

After installation, when a client sends a request to the cluster, the Oracle Clusterware SCAN listeners redirect client requests to servers in the cluster.

**See Also:**

[Oracle Clusterware Administration and Deployment Guide](../cwadd/cluster-verification-utility-reference.md) for more information about system checks and configurations

**Parent topic:** [Recommended Postinstallation Tasks](recommended-postinstallation-tasks.md)
