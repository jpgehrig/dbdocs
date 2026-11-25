VSS is an infrastructure on Windows server platforms that enables applications to create shadow copies.

A shadow copy is a consistent snapshot of the data held on a volume or component at a well-defined point in time. A shadow copy set is a collection of shadow copies that are all taken at the same time. VSS identifies each shadow copy and shadow copy set by a persistent Global Unique Identifier (GUID).

VSS provides the following infrastructure for running VSS applications:

- Coordinates activities of requesters, providers, and writers in the creation and use of shadow copies

- Furnishes the default system provider

- Implements low-level driver functionality necessary for any provider to work

A VSS requester is an application that requests VSS services to create shadow copies. Typically, VSS requesters are backup applications. Requesters communicate with writers to gather system data and signal writers to prepare data for backup.

A VSS provider manages storage volumes and creates shadow copies on demand. In response to a requester, a provider generates COM events to signal applications of an impending shadow copy and creates and maintains this copy until it is no longer needed. During the life cycle of the shadow copy, the provider effectively supports two independent copies: the disk that is actively updated and a fixed copy that is stable for backup.

A VSS writer is an application or a service that writes data to a disk and cooperates with VSS providers and requesters. During backups, writers ensure that data is in the proper state for a shadow copy.

The Oracle VSS writer is a Windows service that coordinates an Oracle Database instance and other VSS components. The writer service, which is started under the user account with `SYSDBA` privileges, runs separately from the database instance. If the writer service runs as a non administrator user, then the user should also be a part of Backup Operators group. You must use third-party requesters to perform backup and recovery within the VSS infrastructure.

As explained in the following sections, the Oracle VSS writer supports both volume-based and component-based shadow copies. You can use these shadow copies in a backup and recovery strategy or to create a copy of your original database. You can use the duplicate database for testing or as a standby database.

- [Component-Based Shadow Copies](componentbased-shadow-copies.md)
  The Oracle VSS writer supports component-based shadow copies, which are sets of database files.
- [Volume-Based Shadow Copies](volume-based-shadow-copies.md)
  The Oracle VSS writer supports volume-based shadow copies, which are snapshots of complete drive or volumes.
- [Oracle VSS Backup Types](oracle-vss-backup-types.md)
  Oracle VSS writer supports log, copy, full, differential, and incremental backups.

**Parent topic:** [Performing Database Backup and Recovery with VSS](performing-database-backup-and-recovery-with-vss.md)
