## Upgrading Operating System for an Oracle Grid Infrastructure Server

Complete this procedure on each Oracle Grid Infrastructure node to upgrade the operating system for an Oracle Grid Infrastructure server.

Note: Oracle Database 19c continues to be supported on Oracle Linux 7 and Red Hat Enterprise Linux 7, however, Oracle strongly recommends that you upgrade your operating system to Oracle Linux 8 or Red Hat Enterprise Linux 8 or later.

1.  As the `root` user, relocate all Oracle Database services running from the current node to another node.
        # cd Grid_home/bin
        # srvctl relocate service -drain_timeout
2.  Disable the automatic startup of Oracle High Availability Services, when the server reboots, on the first node.
        # cd Grid_home/bin
        # ./crsctl disable crs
3.  Shut down the Oracle Clusterware stack on the first node.
        # ./crsctl stop crs
4.  Update the operating system to a version that is supported for your Oracle Grid Infrastructure release.
    Refer to your operating system documentation for more information about upgrading the operating system.
    **Note:**

    For an operating system upgrade that results in a new root file system, you must remove the node from the cluster and add it back into the cluster.
5.  Reboot your Oracle Grid Infrastructure server after the operating system upgrade is complete.
6.  Update the Oracle Clusterware operating system files.
        # Grid_home/crs/install/rootcrs.sh -updateosfiles
7.  As the `root` user, enable the automatic startup of Oracle High Availability Services, when the server reboots, on the first node.
        # cd Grid_home/bin
        # ./crsctl enable crs
8.  Start the Oracle Clusterware stack on the first node.
        # ./crsctl start crs
9.  Repeat steps 1 through 8 on all the Oracle Clusterware nodes.

**Parent topic:** [Reviewing Operating System and Software Upgrade Best Practices](reviewing-operating-system-and-software-upgrade-best-practices.md)
