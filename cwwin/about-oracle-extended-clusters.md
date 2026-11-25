## About Oracle Extended Clusters

An Oracle Extended Cluster consists of nodes that are located in multiple locations called sites.

When you deploy an Oracle Standalone Cluster, you can also choose to configure the cluster as an Oracle Extended Cluster. You can extend an Oracle RAC cluster across two, or more, geographically separate sites, each equipped with its own storage. In the event that one of the sites fails, the other site acts as an active standby.

Both Oracle ASM and the Oracle Database stack, in general, are designed to use enterprise-class shared storage in a data center. Fibre Channel technology, however, enables you to distribute compute and storage resources across two or more data centers, and connect them through Ethernet cables and Fibre Channel, for compute and storage needs, respectively.

You can configure an Oracle Extended Cluster when you install Oracle Grid Infrastructure. You can also do so post installation using the `ConvertToExtended` script. You manage your Oracle Extended Cluster using CRSCTL.

You can assign nodes and failure groups to sites. Sites contain failure groups, and failure groups contain disks.

The following conditions apply when you select redundancy levels for Oracle Extended Clusters:

Table 9-2 Oracle ASM Disk Group Redundancy Levels for Oracle Extended Clusters with 2 Data Sites

| Redundancy Level    | Number of Failure Groups for OCR and Voting Files Disk Groups                           | Number of Failure Groups for OCR Backup and GIMR Disk Groups                            |
|:--------------------|:----------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------|
| Normal redundancy   | 1 failure group per data site, 1 quorum failure group                                   | 1 failure group per data site                                                           |
| Flex redundancy     | 1 failure group per data site, 1 quorum failure group                                   | 1 failure group per data site, 1 quorum failure group                                   |
| Extended redundancy | 3 failure groups each for 2 data sites, 1 quorum failure group outside the 2 data sites | 3 failure groups each for 2 data sites, 1 quorum failure group outside the 2 data sites |
| High redundancy     | Not supported                                                                           | Not supported                                                                           |

**Related Topics**

- [Identifying Storage Requirements for Using Oracle ASM for Shared Storage](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
- [Oracle Clusterware Administration and Deployment Guide](../cwadd/oracle-flex-clusters.md)

**Parent topic:** [Understanding Cluster Configuration Options](understanding-cluster-configuration-options.md)
