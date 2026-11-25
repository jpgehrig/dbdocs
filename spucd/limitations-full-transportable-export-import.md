There are limitations on full transportable export/import.

Be aware of the following limitations on full transportable export/import:

- The general limitations described in "[General Limitations on Transporting Data](general-limitations-on-transporting-data.md)" apply to full transportable export/import.

- You cannot transport an encrypted tablespace to a platform with different endianness.

  To transport an encrypted tablespace to a platform with the same endianness, during export set the `ENCRYPTION_PWD_PROMPT` export utility parameter to `YES`, or use the `ENCRYPTION_PASSWORD` export utility parameter. During import, use the equivalent import utility parameter, and set the value to the same password that was used for the export.

- Full transportable export/import can export and import user-defined database objects in administrative tablespaces using conventional Data Pump export/import, such as direct path or external table. Administrative tablespaces are non-user tablespaces supplied with Oracle Database, such as the `SYSTEM` and `SYSAUX` tablespaces.

- Full transportable export/import cannot transport a database object that is defined in both an administrative tablespace (such as `SYSTEM` and `SYSAUX`) and a user-defined tablespace. For example, a partitioned table might be stored in both a user-defined tablespace and an administrative tablespace. If you have such database objects in your database, then you can redefine them before transporting them so that they are stored entirely in either an administrative tablespace or a user-defined tablespace. If the database objects cannot be redefined, then you can use conventional Data Pump export/import.

- When transporting a database over the network using full transportable export/import, auditing cannot be enabled for tables stored in an administrative tablespace (such as `SYSTEM` and `SYSAUX`) when the audit trail information itself is stored in a user-defined tablespace. See [Oracle Database Security Guide](../dbseg/part_6.md) for more information about auditing.

**Parent topic:** [Transporting Databases](transporting-databases.md)
