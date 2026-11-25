You can transport a tablespace or a set of tablespaces between databases.

The following list of tasks summarizes the process of transporting a tablespace. Details for each task are provided in the subsequent example.

1.  Pick a self-contained set of tablespaces.
2.  At the source database, configure the set of tablespaces in read-only mode and generate a transportable tablespace set.
    A transportable tablespace set (or transportable set) consists of data files for the set of tablespaces being transported and an export dump file containing structural information (metadata) for the set of tablespaces. You use Data Pump to perform the export.
3.  Transport the export dump file.
    Copy the export dump file to a place that is accessible to the target database.
4.  Transport the tablespace set.
    Copy the data files to a directory that is accessible to the target database.

    If the source platform and target platform are different, then check the endian format of each platform by running the query on the `V$TRANSPORTABLE_PLATFORM` view.

    If the source platform's endian format is different from the target platform's endian format, then use one of the following methods to convert the data files:

    - Use the `GET_FILE` or `PUT_FILE` procedure in the `DBMS_FILE_TRANSFER` package to transfer the data files. These procedures convert the data files to the target platform's endian format automatically.

    - Use the RMAN `CONVERT` command to convert the data files to the target platform's endian format.

      **Note:**

      Conversion of data files between different endian formats is not supported for data files having undo segments.
5.  (Optional) Restore tablespaces to read/write mode on the source database.
6.  At the target database, import the tablespace set.
    Run the Data Pump utility to import the metadata for the tablespace set.

Example 5-1 Example

These tasks for transporting a tablespace are illustrated more fully in the example that follows, where it is assumed the following data files and tablespaces exist:

| Tablespace | Data File                                       |
|:-----------|:------------------------------------------------|
| `sales_1`  | `/u01/app/oracle/oradata/salesdb/sales_101.dbf` |
| `sales_2`  | `/u01/app/oracle/oradata/salesdb/sales_201.dbf` |

**Parent topic:** [Migrating Oracle Database](migrating-oracle-database.md)
