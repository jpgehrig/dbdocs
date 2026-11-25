## About Managing Undo Tablespaces in Oracle RAC

Oracle Database stores rollback or undo information in undo tablespaces.

To manage undo tablespaces, Oracle recommends that you use Automatic Undo Management. Automatic Undo Management is an automated management mode for undo tablespaces that is easier to administer than manual undo management.

When Oracle ASM and Oracle Managed Files are used along with Automatic Undo Management, an instance that is started for the first time, and thus does not have an undo tablespace, has its undo tablespace created for it by another instance automatically. The same is also true for online redo logs.

**See Also:**

- [Oracle Database Administrator's Guide](../admin/managing-undo.md) for more information about automatic undo management

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/administering-storage-in-oracle-rac.md) for more information about managing undo tablespaces

**Parent topic:** [Understanding the Oracle RAC Installed Configuration](understanding-the-oracle-rac-installed-configuration.md)
