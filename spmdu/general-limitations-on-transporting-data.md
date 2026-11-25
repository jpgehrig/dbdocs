There are general limitations on transporting data. There are also limitations that are specific to full transportable export/import, transportable tablespaces, or transportable tables.

Be aware of the following general limitations as you plan to transport data:

- The source and the target databases must use compatible database character sets. Specifically, one of the following must be true:

  - The database character sets of the source and the target databases are the same.

  - The source database character set is a strict (binary) subset of the target database character set, and the following three conditions are true:

    - The source database is Oracle Database 10g Release 1 (10.1.0.3) or later.

    - The tablespaces to be transported contain no table columns with character length semantics or the maximum character width is the same in both the source and target database character sets.

    - The data to be transported contains no columns with the `CLOB` data type, or the source and the target database character sets are both single-byte or both multibyte.

  - The source database character set is a strict (binary) subset of the target database character set, and the following two conditions are true:

    - The source database is before Oracle Database 10g Release 1 (10.1.0.3).

    - The maximum character width is the same in the source and target database character sets.

  **Note:**

  The subset-superset relationship between character sets recognized by Oracle Database is documented in the [Oracle Database Globalization Support Guide](../nlspg/appendix-A-locale-data.md).

- The source and the target databases must use compatible national character sets. Specifically, one of the following must be true:

  - The national character sets of the source and target databases are the same.

  - The source database is Oracle Database 10g Release 1 (10.1.0.3) or later, and the tablespaces to be transported contain no columns with `NCHAR`, `NVARCHAR2`, or `NCLOB` data types.

- When running a transportable export operation, the following limitations apply:

  - The default tablespace of the user performing the export must not be one of the tablespaces being transported.

  - The default tablespace of the user performing the export must be writable.

- In a non-CDB, you cannot transport a tablespace to a target database that contains a tablespace of the same name.

  In a CDB, you cannot transport a tablespace to a target container that contains a tablespace of the same name. However, different containers can have tablespaces with the same name.

  You can use the `REMAP_TABLESPACE` import parameter to import the database objects into a different tablespace. Alternatively, before the transport operation, you can rename either the tablespace to be transported or the target tablespace.

  Starting with Oracle Database 12c Release 2 (12.2), the Recovery Manager (RMAN) `RECOVER` command can move tables to a different schema while remapping a tablespace. See [Oracle Database Backup and Recovery User’s Guide](../bradv/rman-recovering-tables-partitions.md) for more information.

- In a CDB, the default Data Pump directory object, `DATA_PUMP_DIR`, does not work with PDBs. You must define an explicit directory object within the PDB that you are using with Data Pump export/import.

- Transporting data with XMLTypes has the following limitations:

  - The target database must have XML DB installed.

  - Schemas referenced by XMLType tables cannot be the XML DB standard schemas.

  - If the schema for a transported XMLType table is not present in the target database, then it is imported and registered. If the schema already exists in the target database, then a message is displayed during import.

  - You must use only Data Pump to export and import the metadata for data that contains XMLTypes.

  The following query returns a list of tablespaces that contain XMLTypes:

      select distinct p.tablespace_name from dba_tablespaces p,
        dba_xml_tables x, dba_users u, all_all_tables t where
        t.table_name=x.table_name and t.tablespace_name=p.tablespace_name
        and x.owner=u.username;

  See [Oracle XML DB Developer's Guide](../adxdb/intro-to-XML-DB.md) for information on XMLTypes.

- Types whose interpretation is application-specific and opaque to the database (such as `RAW`, `BFILE`, and the AnyTypes) can be transported, but they are not converted as part of the cross-platform transport operation. Their actual structure is known only to the application, so the application must address any endianness issues after these types are moved to the new platform. Types and objects that use these opaque types, either directly or indirectly, are also subject to this limitation.

- When you transport a tablespace containing tables with `TIMESTAMP` `WITH` `LOCAL` `TIME` `ZONE` (TSLTZ) data between databases with different time zones, the tables with the TSLTZ data are not transported. Error messages describe the tables that were not transported. However, tables in the tablespace that do not contain TSLTZ data are transported.

  You can determine the time zone of a database with the following query:

      SELECT DBTIMEZONE FROM DUAL;

  You can alter the time zone for a database with an `ALTER` `DATABASE` SQL statement.

  You can use Data Pump to perform a conventional export/import of tables with TSLTZ data after the transport operation completes.

- Analytic workspaces cannot be part of cross-platform transport operations. If the source platform and target platform are different, then use Data Pump export/import to export and import analytic workspaces. See [Oracle OLAP DML Reference](../oladm/olap-dml-basic-concepts.md) for more information about analytic workspaces.

**Note:**

Do not invoke Data Pump export utility `expdp` or import utility `impdp` as `SYSDBA`, except at the request of Oracle technical support. `SYSDBA` is used internally and has specialized functions; its behavior is not the same as for general users.

**Parent topic:** [Migrating Data Using Transportable Tablespaces](transportable-tablespaces.md)
