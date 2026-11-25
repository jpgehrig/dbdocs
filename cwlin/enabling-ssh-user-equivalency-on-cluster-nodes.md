## Enabling SSH User Equivalency on Cluster Nodes

After you have copied the `authorized_keys` file that contains all keys to each node in the cluster, complete the following procedure.

In this example, the Oracle Grid Infrastructure software owner is named `grid`.

Do the following:

1.  On the system where you want to run OUI, log in as the `grid` user.
2.  Use the following command syntax, where `hostname1`, `hostname2`, and so on (without domain name and in lowercase), are the public host names of nodes in the cluster to run SSH from the local node to each node, including from the local node to itself, and from each node to each other node:
        [grid@nodename]$ ssh hostname1 date
        [grid@nodename]$ ssh hostname2 date     .     .     .

    At the end of this process, the public host name for each member node should be registered in the `known_hosts` file for all other cluster nodes. If you are using a remote client to connect to the local node, and you see a message similar to "`Warning: No xauth data; using fake authentication data for X11 forwarding`," then this means that your authorized keys file is configured correctly, but your SSH configuration has X11 forwarding enabled. To correct this issue, see [Setting Remote Display and X11 Forwarding Configuration](setting-remote-display-and-x11-forwarding-configuration.md).
3.  Repeat step 2 on each cluster node member.

If you have configured SSH correctly, then you can now use the `ssh` or `sftp` commands without being prompted for a password. For example:

    [grid@node1 ~]$ ssh node2 date
    Mon Feb 26 23:34:42 UTC 2009
    [grid@node1 ~]$ ssh node1 date
    Mon Feb 26 23:34:48 UTC 2009

If any node prompts for a password, then verify that the `~/.ssh/authorized_keys` file on that node contains the correct public keys, and that you have created an Oracle software owner with identical group membership and IDs.

**Parent topic:** [Configuring SSH Manually on All Cluster Nodes](configuring-ssh-manually-on-all-cluster-nodes.md)
