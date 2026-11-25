## Configuring Storage for External Tables, Shared Files, or Directory Objects

If your Oracle RAC database uses files that are external to the database, then locate the external files on shared storage that is accessible to all nodes. Each node should use the same mount point to access the file.

Acceptable shared file systems include Database File System (DBFS), Oracle ASM Cluster File System (Oracle ACFS), or a supported network file system (NFS) using the Direct NFS Client.

The database directory object used to write and read files external to the database must point to a shared storage location, and each node must use the same mount point for the same shared storage location.

**Note:**

There is no checking of the contents of the external files or directory object specified as part of the external table to ensure that the directory contents are consistent on each node. To avoid unpredictable results, you must ensure that the same file is accessed from all nodes, or that the same file is used on all nodes.

**See Also:**

[Oracle Grid Infrastructure Installation Guide](../install-and-upgrade.md) for more information about configuring storage

**Parent topic:** [Product-Specific Postinstallation Tasks](product-specific-postinstallation-tasks.md)
