Complete the following procedure to upgrade an existing HACMP and Oracle Clusterware installation.

1.  Back up all databases, and back up the Oracle Cluster Registry (OCR).
2.  Shut down on all nodes all Oracle RAC databases, all node applications, and Oracle Clusterware.
3.  Enter the following command to disable Oracle Clusterware from starting when nodes are restarted:
        # crsctl disable crs
4.  Shut down HACMP on all nodes.
5.  Install HACMP APAR IZ01809, following the directions in the README included with that APAR.
6.  Determine if the existing voting disk LVs are already on separate hard disks, and if each of these disks have sufficient space (at least 256 MB for the MNDHB LVs). If this is true, then create a MNDHB LV on each of the hard disks. If this is not true, then create new MNDHB LVs and new voting disk LVs, located on separate hard disks using the following command, responding to the sections in italics with the appropriate information for your system:
        # smitty cl_add_mndhb_lv
        - Select_resource_group
        * Physical Volume name Enter F4, then select disk for the MNDHB and Voting Disk pair
        Logical Volume Name []
        Logical Volume Label []
        Volume Group name ccvg
        Resource Group Name shared_storage
        Network Name [net_diskhbmulti_01]
7.  Verify and Synchronize HACMP configuration.
8.  Start HACMP on all nodes.
9.  If you added new LVs for voting disks in step 5, then replace each of the existing voting disks with the new ones.
10. Enter the following command to re-enable Oracle Clusterware:
        # crsctl enable crs
11. Start Oracle Clusterware on all nodes, and verify that all resources start correctly.

**Parent topic:** [Configuring HACMP Multinode Disk Heartbeat (MNDHB)](configuring-multi-node-disk-heartbeat.md)
