## Storage Checklist for Oracle Database Client Installation

Use this checklist to review storage minimum requirements and assist with configuration planning.

Table 1-5 Storage Checklist for Oracle Database Client Installation

| Check                                                | Task                                                                                                                                                                                                                                                                                                                                                              |
|:-----------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Minimum local disk storage space for Oracle software | At least 350 MB for an Instant Client installation<br>At least 1536 MB for Administrator installation<br>At least 1024 MB for Runtime installation<br>At least 180 MB for Custom installation                                                                                                                                                                     |
| Recommended file system                              | Ensure that you have one of the following storage options available:<br>• Oracle ASM Cluster File System (Oracle ACFS)<br>• Oracle Automatic Storage Management (Oracle ASM)<br>• NTFS File System or Resilient File System (ReFS)<br>The database files must be placed on Oracle ASM if you are using Oracle ACFS; otherwise they can be placed on NTFS or ReFS. |

**Parent topic:** [Oracle Database Client Installation Checklist](oracle-database-client-installation-checklist.md)
