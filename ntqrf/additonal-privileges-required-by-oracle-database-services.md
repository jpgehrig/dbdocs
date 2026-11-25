Certain functions performed by the Oracle Database service require additional privileges.

Oracle Universal Installer and other Oracle tools automatically grant the following privileges to the Windows services `SID` of the respective services during the creation of these services:

- `SeIncreaseBasePriorityPrivilege`: A process requires this privilege to change the priority of its threads. This privilege is granted to Windows service `SID`s of Oracle Automatic Storage Management (Oracle ASM) or Oracle Database services.

- `SeBackupPrivilege`: This privilege is required to perform backup operations. It is granted to the Windows service `SID`s of Oracle VSS Writer service.

- `SeBatchLogonRight`: This privilege is required for an account to log on using the batch logon type. It is granted to the Windows service `SID`s of Oracle Scheduler service.

To enable Oracle Database to use Large Pages or working set features, the following additional operating system privileges must be manually granted by the operating system administrator to either the Oracle Home User or to the Windows service `SID`s of the specified Oracle Database service during the creation of these services.

Oracle recommends granting privileges to the Windows service `SID` of Oracle Database service instead of the Oracle Home User. The Windows service `SID` of the database service follows this syntax, `NT AUTHORITY\OracleService``SID`.

- `SeLockMemoryPrivilege`: This privilege is required to lock pages in memory. Oracle Database requires this privilege to use Large Pages.

- `SeIncreaseQuotaPrivilege`: This privilege is required to change the memory quota for a process. This is needed while setting the `max` and `min` working set sizes for the database.

**Related Topics**

- [Overview of Large Page Support](overview-of-large-page-support.md)

**Parent topic:** [About Windows Services for Oracle Database](about-windows-services-for-oracle-database.md)
