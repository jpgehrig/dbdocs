## Disabling Write Caching

You must disable write caching on all disks that will be used to share data between the nodes in your cluster.

1.  Click Start, then select Administrative Tools, then Computer Management, then Device Manager, and then Disk drives.
2.  Expand the Disk drives and double-click the first drive that will be used by Oracle software.
3.  Under the Policies tab for the selected drive, uncheck the option that enables write caching.
4.  Double-click each of the other drives that will be used by Oracle Clusterware and Oracle RAC and disable write caching as described in Step 3.

**Note:**

Any disks that you use to store files, including database files, that will be shared between nodes, must have write caching disabled.

**Parent topic:** [Preliminary Shared Disk Preparation](preliminary-shared-disk-preparation.md)
