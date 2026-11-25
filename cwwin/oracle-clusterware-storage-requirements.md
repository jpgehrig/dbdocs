## Oracle Clusterware Storage Space Requirements

Use this information to determine the minimum number of disks and the minimum disk space requirements based on the redundancy type, for installing Oracle Clusterware files, and installing the starter database, for various Oracle Cluster deployments.

### Total Storage Space for Database Files Required by Redundancy Type

The following tables list the space requirements for Oracle RAC Database data files for multitenant and non-CDB deployments.

Table 7-1 Oracle ASM Disk Space Requirements for a Multitenant Container Database (CDB) with One Pluggable Database (PDB)

| Redundancy Level | Minimum number of disks | Data Files | Recovery Files | Both File Types |
|:-----------------|:------------------------|:-----------|:---------------|:----------------|
| External         | 1                       | 4.5 GB     | 12.9 GB        | 17.4 GB         |
| Normal           | 2                       | 8.6 GB     | 25.8 GB        | 34.4 GB         |
| High             | 3                       | 12.9 GB    | 38.7 GB        | 51.6 GB         |
| Flex             | 3                       | 12.9 GB    | 38.7 GB        | 51.6 GB         |

Table 7-2 Oracle ASM Disk Space Requirements for Oracle Database (non-CDB)

| Redundancy Level | Minimum number of disks | Data Files | Recovery Files | Both File Types |
|:-----------------|:------------------------|:-----------|:---------------|:----------------|
| External         | 1                       | 2.7 GB     | 7.8 GB         | 10.5 GB         |
| Normal           | 2                       | 5.2 GB     | 15.6 GB        | 20.8 GB         |
| High             | 3                       | 7.8 GB     | 23.4 GB        | 31.2 GB         |
| Flex             | 3                       | 7.8 GB     | 23.4 GB        | 31.2 GB         |

### Total Oracle Clusterware Available Storage Space Required by Oracle Cluster Deployment Type

If you create a disk group as part of the installation to install the OCR and voting files, then the installer requires that you create these files on a disk group with at least 2 GB of available space.

Based on the cluster configuration you want to install, the Oracle Clusterware space requirements vary for different redundancy levels. The following table lists the available storage space requirements for external redundancy level for each cluster configuration:

**Note:**

Starting with Oracle Grid Infrastructure 19c, configuring GIMR is optional for Oracle Standalone Cluster deployments. When upgrading to Oracle Grid Infrastructure 19c, a new GIMR is created only if the source Grid home has a GIMR configured.

Table 7-3 Minimum Available Space Requirements for Oracle Standalone Cluster With GIMR Configuration

| Redundancy Level   | DATA Disk Group | MGMT Disk Group                         | Oracle Fleet Patching and Provisioning | Total Storage |
|:-------------------|:----------------|:----------------------------------------|:---------------------------------------|:--------------|
| External           | 1 GB            | 28 GB<br>Each node beyond four:<br>5 GB | 1 GB                                   | 30 GB         |
| Normal             | 2 GB            | 56 GB<br>Each node beyond four:<br>5 GB | 2 GB                                   | 60 GB         |
| High/Flex/Extended | 3 GB            | 84 GB<br>Each node beyond four:<br>5 GB | 3 GB                                   | 90 GB         |

**Related Topics**

- [Storage Checklist for Oracle Grid Infrastructure](storage-checklist-for-oracle-grid-infrastructure.md)

**Parent topic:** [Configuring Storage for Oracle Automatic Storage Management](configuring-storage-for-oracle-asm.md)
