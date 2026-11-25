## Checking the SCAN Configuration

The SCAN is a name that provides service access for clients to the cluster. You can use the command `cluvfy comp scan` (located in `Grid_home``\bin`) to confirm that the DNS is correctly associating the SCAN with the addresses.

Because the SCAN is associated with the cluster as a whole, rather than to a particular node, the SCAN makes it possible to add or remove nodes from the cluster without needing to reconfigure clients. It also adds location independence for the databases, so that client configuration does not have to depend on which nodes run a particular database instance. Clients can continue to access the cluster in the same way as with earlier releases, but Oracle recommends that clients accessing the cluster use the SCAN.

After installation, when a client sends a request to the cluster, the Oracle Clusterware SCAN listeners redirect client requests to servers in the cluster.

- Confirm that the DNS is correctly associating the SCAN with the specified addresses.
      cluvfy comp scan

Example 10-1 Using CLUVFY to Confirm DNS is Correctly Associating the SCAN Addresses

This example shows the output from the `cluvfy comp scan` command for a cluster node named `node1.example.com`.

    C:\> cluvfy comp scan
    Verifying scan

    Checking Single Client Access Name (SCAN)...

    Checking TCP connectivity to SCAN Listeners...
    TCP connectivity to SCAN Listeners exists on all cluster nodes

    Checking name resolution setup for "node1.example.com"...

    Verification of SCAN VIP and Listener setup passed

    Verification of scan was successful.

**Parent topic:** [Recommended Postinstallation Tasks](recommended-postinstallation-tasks.md)
