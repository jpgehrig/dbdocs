## Verifying Privileges for Copying Files in the Cluster

During installation, OUI copies the software from the local node to the remote nodes in the cluster. The installation user must have privileges on the other nodes in the cluster to copy the files.

1.  Verify that you have Administrator privileges on the other nodes in the cluster by running the following command on each node, where nodename is the name of the remote node:
        net use \\nodename\C$
2.  After installation, if your system does not use the net share shown in the above example, then you can remove the unused net share using the following command:
        net use \\nodename\C$ /delete

**Parent topic:** [Configuring Operating Systems for Oracle Grid Infrastructure and Oracle RAC](configuring-operating-systems-for-oracle-grid-infrastructure-and-oracle-rac.md)
