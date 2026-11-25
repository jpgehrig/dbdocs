## 67  DBMS_DNFS

The `DBMS_DNFS` package provides an interface to assists in creating a database using files in the backup set.

This chapter contains the following topics:

- Security Model

- Summary of DBMS_DNFS Subprograms

**See Also:**

[Oracle Database Administrator's Guide](../admin/creating-and-configuring-an-oracle-database.md)

### 67.1 DBMS_DNFS Security Model

This package has to be executed by users with `SYSDBA` privileges.

### 67.2 Summary of DBMS_DNFS Subprograms

The `DBMS_DNFS` package includes the `CLONEDB_RENAMEFILE`, `RESTORE_DATAFILE_PERMISSIONS`, and `UNMOUNTVOLUME` procedures.

Table 67-1 DBMS_DNFS Package Subprograms

| Subprogram                             | Description                                                                                                                                                                                                  |
|:---------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CLONEDB_RENAMEFILE Procedure           | Renames datafiles that were pointing to the backup set to the actual file name in cloned database.                                                                                                           |
| RESTORE_DATAFILE_PERMISSIONS Procedure | This procedure will restore the file permissions for the data files belonging to the PDB to read write. PDB data files are converted to read only when one or more clones are created using this source PDB. |
| UNMOUNTVOLUME Procedure                | This procedure cleans up the cached Direct NFS file handles in SGA.                                                                                                                                          |

#### 67.2.1 CLONEDB_RENAMEFILE Procedure

This procedure is used to rename datafiles that were pointing to the backup set to the actual file name in cloned database.

The `srcfile` is the file name that represents the data file in the backup image copy or a read-only storage snapshot. The `destfile` destination file path must point to a NFS volume where cloneDB datafiles will be created. When the procedure is run successfully, the control file record is updated with the new datafile name.

##### Syntax

    DBMS_DNFS.CLONEDB_RENAMEFILE (
       srcfile        IN         VARCHAR2,
       destfile       IN         VARCHAR2);

##### Parameters

Table 67-2 CLONEDB_RENAMEFILE Procedure Parameters

| Parameter  | Description                              |
|:-----------|:-----------------------------------------|
| `srcfile`  | Source datafile name in the control file |
| `destfile` | New datafile name                        |

#### 67.2.2 RESTORE_DATAFILE_PERMISSIONS Procedure

This procedure restores the file permissions for the data files belonging to the PDB to `read write`. PDB data files are converted to `read only` when one or more clones are created using this source PDB. This procedure must be invoked after the last clone is dropped to restore the data file permissions for the source PDB files.

##### Syntax

    DBMS_DNFS.RESTORE_DATAFILE_PERMISSIONS (
       pdb_name       IN         VARCHAR2  DEFAULT NULL);

##### Parameters

Table 67-3 RESTORE_DATAFILE_PERMISSIONS Procedure Parameters

| Parameter  | Description                                                            |
|:-----------|:-----------------------------------------------------------------------|
| `pdb_name` | Name of pluggable database whose file permissions need to be restored. |

#### 67.2.3 UNMOUNTVOLUME Procedure

This procedure cleans up the cached Direct NFS file handles in SGA. This procedure must be used when any NFS mount changes are being made via the operating system and the OS unmount and mount commands are invoked.

The server is the host name or IP address of the NFS server. The volume is the exported path from the NFS server. This procedure will fail if the database has any open files in the volume that is being unmounted.

##### Syntax

    DBMS_DNFS.UNMOUNTVOLUME (
       server         IN         VARCHAR2,
       volume         IN         VARCHAR2);

##### Parameters

Table 67-4 UNMOUNTVOLUME Procedure Parameters

| Parameter | Description                         |
|:----------|:------------------------------------|
| `server`  | NFS server host name or IP address. |
| `volume ` | Exported path from the NFS server.  |
