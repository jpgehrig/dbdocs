On x86 (64-bit) platforms running Oracle Solaris, if you install Oracle Solaris Cluster in addition to Oracle Clusterware, then complete the following task.

1.  Switch user to `root`:
        $ su - root
2.  Complete one of the following steps, depending on the location of the installation:
    - If the installation files are on an installation media, then enter a command similar to the following, where mountpoint is the disk mount point directory or the path of the database directory on the installation media:

          # mountpoint/grid/rootpre.sh

    - If the installation files are on the hard disk, change directory to the directory /Disk1 and enter the following command:

          # ./rootpre.sh
3.  Exit from the `root` account:
        # exit
4.  Repeat steps 1 through 3 on all nodes of the cluster.

**Parent topic:** [Configuring Oracle Solaris Operating Systems for Oracle Grid Infrastructure](configuring-operating-systems-for-oracle-grid-infrastructure-on-oracle-solaris.md)
