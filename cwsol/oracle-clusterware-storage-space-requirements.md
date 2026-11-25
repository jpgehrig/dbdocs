Use this information to determine the minimum number of disks and the minimum disk space requirements based on the redundancy type, for installing Oracle Clusterware files for various Oracle Cluster deployments.

### Total Oracle Clusterware Available Storage Space Required by Oracle Cluster Deployment Type

During installation of an Oracle Standalone Cluster, if you create the `MGMT` disk group for Grid Infrastructure Management Repository (GIMR), then the installer requires that you use a disk group with at least 35 GB of available space.

**Note:**

Starting with Oracle Grid Infrastructure 19c, configuring GIMR is optional for Oracle Standalone Cluster deployments. When upgrading to Oracle Grid Infrastructure 19c, a new GIMR is created only if the source Grid home has a GIMR configured.

Based on the cluster configuration you want to install, the Oracle Clusterware space requirements vary for different redundancy levels. The following tables list the space requirements for each cluster configuration and redundancy level.

**Note:**

The `DATA` disk group stores OCR and voting files, and the `MGMT` disk group stores GIMR and Oracle Clusterware backup files.

Table 8-1 Minimum Available Space Requirements for Oracle Standalone Cluster With GIMR Configuration

| Redundancy Level   | DATA Disk Group | MGMT Disk Group                         | Oracle Fleet Patching and Provisioning | Total Storage |
|:-------------------|:----------------|:----------------------------------------|:---------------------------------------|:--------------|
| External           | 1 GB            | 28 GB<br>Each node beyond four:<br>5 GB | 1 GB                                   | 30 GB         |
| Normal             | 2 GB            | 56 GB<br>Each node beyond four:<br>5 GB | 2 GB                                   | 60 GB         |
| High/Flex/Extended | 3 GB            | 84 GB<br>Each node beyond four:<br>5 GB | 3 GB                                   | 90 GB         |

- Oracle recommends that you use a separate disk group, other than `DATA`, for GIMR and Oracle Clusterware backup files.

- The initial GIMR sizing for the Oracle Standalone Cluster is for up to four nodes. You must add additional storage space to the disk group containing the GIMR and Oracle Clusterware backup files for each new node added to the cluster.

- By default, all new Oracle Standalone Cluster deployments are configured with Oracle Fleet Patching and Provisioning for patching that cluster only. This deployment requires a minimal ACFS file system that is automatically configured in the same disk group as the GIMR.

Table 8-2 Minimum Available Space Requirements for Oracle Standalone Cluster Without GIMR Configuration

| Redundancy Level   | DATA Disk Group | Oracle Fleet Patching and Provisioning | Total Storage |
|:-------------------|:----------------|:---------------------------------------|:--------------|
| External           | 1 GB            | 1 GB                                   | 2 GB          |
| Normal             | 2 GB            | 2 GB                                   | 4 GB          |
| High/Flex/Extended | 3 GB            | 3 GB                                   | 6 GB          |

- Oracle recommends that you use a separate disk group, other than `DATA`, for Oracle Clusterware backup files.

- The initial sizing for the Oracle Standalone Cluster is for up to four nodes. You must add additional storage space to the disk group containing Oracle Clusterware backup files for each new node added to the cluster.

- By default, all new Oracle Standalone Cluster deployments are configured with Oracle Fleet Patching and Provisioning for patching that cluster only. This deployment requires a minimal ACFS file system that is automatically configured.

Table 8-3 Minimum Available Space Requirements for Oracle Member Cluster with Local ASM

| Redundancy Level   | DATA Disk Group | Oracle Clusterware Backup Files | Total Storage |
|:-------------------|:----------------|:--------------------------------|:--------------|
| External           | 1 GB            | 4 GB                            | 5 GB          |
| Normal             | 2 GB            | 8 GB                            | 10 GB         |
| High/Flex/Extended | 3 GB            | 12 GB                           | 15 GB         |

- For Oracle Member Cluster, the storage space for the GIMR is pre-allocated in the centralized GIMR on the Oracle Domain Services Cluster as described in Table 8–5.

- Oracle recommends that you use a separate disk group, other than `DATA`, for Oracle Clusterware backup files.

Table 8-4 Minimum Available Space Requirements for Oracle Domain Services Cluster

| Redundancy Level   | DATA Disk Group                              | MGMT Disk Group | Trace File Analyzer | Total Storage                                                 | Additional Oracle Member Cluster                                                                         |
|:-------------------|:---------------------------------------------|:----------------|:--------------------|:--------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------|
| External           | 1 GB and 1 GB for each Oracle Member Cluster | 140 GB          | 200 GB              | 345 GB<br>(excluding Oracle Fleet Patching and Provisioning)  | Oracle Fleet Patching and Provisioning: 100 GB<br>GIMR for each Oracle Member Cluster beyond four: 28 GB |
| Normal             | 2 GB and 2 GB for each Oracle Member Cluster | 280 GB          | 400 GB              | 690 GB<br>(excluding Oracle Fleet Patching and Provisioning)  | Oracle Fleet Patching and Provisioning: 200 GB<br>GIMR for each Oracle Member Cluster beyond four: 56 GB |
| High/Flex/Extended | 3 GB and 3 GB for each Oracle Member Cluster | 420 GB          | 600 GB              | 1035 GB<br>(excluding Oracle Fleet Patching and Provisioning) | Oracle Fleet Patching and Provisioning: 300 GB<br>GIMR for each Oracle Member Cluster beyond four: 84 GB |

- By default, the initial space allocation for the GIMR is for the Oracle Domain Services Cluster and four or fewer Oracle Member Clusters. You must add additional storage space for each Oracle Member Cluster beyond four.

- At the time of installation, TFA storage space requirements are evaluated to ensure the growth to the maximum sizing is possible. Only the minimum space is allocated for the ACFS file system, which extends automatically up to the maximum value, as required.

- Oracle recommends that you pre-allocate storage space for largest foreseeable configuration of the Oracle Domain Services Cluster according to the guidelines in the above table.

**Parent topic:** [Configuring Storage for Oracle Automatic Storage Management](configuring-storage-for-oracle-automatic-storage-management.md)
