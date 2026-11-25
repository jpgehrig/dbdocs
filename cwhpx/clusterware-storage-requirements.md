Use this information to determine the minimum number of disks and the minimum disk space requirements based on the redundancy type, for installing Oracle Clusterware files for Oracle Standalone Cluster deployments.

### Total Oracle Clusterware Storage Space Required by Oracle Standalone Cluster

During installation of an Oracle Standalone Cluster, if you create the `MGMT` disk group for Grid Infrastructure Management Repository (GIMR), then the installer requires that you use a disk group with at least 35 GB of available space.

**Note:**

Starting with Oracle Grid Infrastructure 19c, configuring GIMR is optional for Oracle Standalone Cluster deployments. When upgrading to Oracle Grid Infrastructure 19c, a new GIMR is created only if the source Grid home has a GIMR configured.

Oracle Clusterware space requirements vary for different redundancy levels. The following tables list the space requirements for each redundancy level.

**Note:**

The `DATA` disk group stores OCR and voting files, and the `MGMT` disk group stores GIMR and Oracle Clusterware backup files.

Table 7-1 Minimum Available Space Requirements for Oracle Standalone Cluster With GIMR Configuration

| Redundancy Level | DATA Disk Group | MGMT Disk Group                         | Total Storage |
|:-----------------|:----------------|:----------------------------------------|:--------------|
| External         | 1 GB            | 28 GB<br>Each node beyond four:<br>5 GB | 29 GB         |
| Normal           | 2 GB            | 56 GB<br>Each node beyond four:<br>5 GB | 58 GB         |

- Oracle recommends that you use a separate disk group, other than `DATA`, for GIMR and Oracle Clusterware backup files.

- The initial GIMR sizing for the Oracle Standalone Cluster is for up to four nodes. You must add additional storage space to the disk group containing the GIMR and Oracle Clusterware backup files for each new node added to the cluster.

Table 7-2 Minimum Available Space Requirements for Oracle Standalone Cluster Without GIMR Configuration

| Redundancy Level   | DATA Disk Group | Total Storage |
|:-------------------|:----------------|:--------------|
| External           | 1 GB            | 1 GB          |
| Normal             | 2 GB            | 2 GB          |
| High/Flex/Extended | 3 GB            | 3 GB          |

- Oracle recommends that you use a separate disk group, other than `DATA`, for Oracle Clusterware backup files.

- The initial sizing for the Oracle Standalone Cluster is for up to four nodes. You must add additional storage space to the disk group containing Oracle Clusterware backup files for each new node added to the cluster.

**Parent topic:** [Configuring Storage for Oracle Automatic Storage Management](configuring-storage-for-oracle-automatic-storage-management.md)
