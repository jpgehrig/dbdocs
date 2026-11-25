## Oracle ASM Disk Space Requirements

Determine the total amount of Oracle Automatic Storage Management (Oracle ASM) disk space that you require for the database files and recovery files.

Table 6-1 Oracle ASM Disk Number and Minimum Space Requirements for an Oracle database (non-CDB)

| Redundancy Level                      | Minimum Number of Disks | Data Files | Recovery Files | Both File Types |
|:--------------------------------------|:------------------------|:-----------|:---------------|:----------------|
| External                              | 1                       | 2.7 GB     | 8.1 GB         | 10.8 GB         |
| Normal or Flex with two-way mirroring | 2                       | 5.2 GB     | 15.6 GB        | 20.8 GB         |
| High or Flex with three-way mirroring | 3                       | 7.8 GB     | 23.4 GB        | 31.2 GB         |

Table 6-2 Oracle ASM Disk Number and Minimum Space Requirements for a multitenant container database (CDB) with one pluggable database (PDB)

| Redundancy Level                      | Minimum Number of Disks | Data Files | Recovery Files | Both File Types |
|:--------------------------------------|:------------------------|:-----------|:---------------|:----------------|
| External                              | 1                       | 4.4 GB     | 13.2 GB        | 17.6 GB         |
| Normal or Flex with two-way mirroring | 2                       | 8.6 GB     | 25.8 GB        | 34.4 GB         |
| High or Flex with three-way mirroring | 3                       | 12.9 GB    | 38.7 GB        | 51.6 GB         |

**Note:**

- If an Oracle ASM instance is running on the system, then you can use an existing disk group to meet these storage requirements. If necessary, you can add disks to an existing disk group during the database installation.

- The disk devices must be owned by the user performing the grid installation.

  Check with your system administrator to determine if the disks used by Oracle ASM are mirrored at the storage level. If so, select External for the redundancy. If the disks are not mirrored at the storage level, then select Normal for the redundancy.

- Every Oracle ASM disk is divided into allocation units (AU). An allocation unit is the fundamental unit of allocation within a disk group. You can select the AU Size value from 1, 2, 4, 8, 16, 32 or 64 MB, depending on the specific disk group compatibility level. The default value is 4 MB for flex disk group and 1 MB for all other disk group types. On engineered systems, the default value is 4 MB.

**Parent topic:** [Configuring Storage for Oracle Automatic Storage Management](configuring-storage-for-oracle-automatic-storage-management.md)
