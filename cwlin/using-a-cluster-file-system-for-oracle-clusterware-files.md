## Using a Cluster File System for Oracle Clusterware Files

Starting with Oracle Grid Infrastructure 19c, you can use Oracle Automatic Storage Management (Oracle ASM) or certified shared file system to store OCR files and voting files.

For new Oracle Standalone Cluster installations, you can use Oracle ASM or shared file system to store voting files and OCR files. For other cluster types, you must use Oracle Automatic Storage Management (Oracle ASM) to store voting files and OCR files. For Linux 86-64 (64-bit) and Linux Itanium platforms, Oracle provides a cluster file system, OCFS2. However, Oracle does not recommend using OCFS2 for Oracle Clusterware files.

**Parent topic:** [Supported Storage Options for Oracle Database and Oracle Grid Infrastructure](supported-storage-options-for-oracle-database-and-oracle-grid-infrastructure.md)
