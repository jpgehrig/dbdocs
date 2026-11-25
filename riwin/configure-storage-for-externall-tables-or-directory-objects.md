## Configure Storage for External Tables, Shared Files, or Directory Objects

If your Oracle RAC database uses files that are external to the database, then the external files must be located on shared storage that is accessible to all nodes.

- Each node must use the same mount point to access the file.
  Acceptable shared file systems include Database File System (DBFS), Oracle Automatic Storage Management Cluster File System (Oracle ACFS), or a supported network file system (NFS) using the Direct NFS Client.
- The database directory object used to write and read files external to the database must point to a shared storage location.
- Each node must use the same mount point for the same shared storage location.
  For example, each node can have a directory object called DPUMP for the mount point `C:\app\acfsmounts\dpump`, which accesses Oracle ACFS shared storage.

**Note:**

There is no checking of the contents of the external files or directory object specified as part of the external table to ensure that the directory contents are consistent on each node. To avoid unpredictable results, you must ensure that the same file is accessed from all nodes, or that the same file is used on all nodes.

**Parent topic:** [Product-Specific Postinstallation Tasks](configure-oracle-products.md)
