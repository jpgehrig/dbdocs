Use the transportable tablespaces feature to copy a set of tablespaces from one Oracle Database to another.

- [Checking Character Set Compatibility](checking-character-set-compatibility.md)
  Run these commands on the source and destination databases to find character sets that are compatible.
- [Transporting Tablespaces Between Databases](transporting-tablespaces-between-databases.md)
  You can transport a tablespace or a set of tablespaces between databases.
- [Task 1: Pick a Self-Contained Set of Tablespaces](task-1-pick-a-self-contained-set-of-tablespaces.md)
  There may be logical or physical dependencies between the database objects in the transportable set and the database objects outside of the transportable set. You can only transport a tablespace set that is self-contained, that is, none of the database objects inside a tablespace set are dependent on any of the database objects outside of that tablespace set.
- [Task 2: Generate a Transportable Tablespace Set](task-2-generate-a-transportable-tablespace-set.md)
  After ensuring that you have a self-contained set of tablespaces that you want to transport, generate a transportable tablespace set.
- [Task 3: Transport the Export Dump File](task-3-transport-the-export-dump-file.md)
  Transport the dump file to the directory pointed to by the `DATA_PUMP_DIR` directory object, or to any other directory of your choosing. The new location must be accessible to the target database.
- [Task 4: Transport the Tablespace Set](task-4-transport-the-tablespace-set.md)
  Transport the data files of the tablespaces to a directory that is accessible to the target database.
- [Task 5: (Optional) Restore Tablespaces to Read/Write Mode](task-5-restore-tablespaces-to-read-write-mode.md)
  Make the transported tablespaces read/write again at the source database.
- [Task 6: Import the Tablespace Set](task-6-import-the-tablespace-set.md)
  To complete the transportable tablespaces operation, import the tablespace set.
- [Postmigration Tasks](postmigration-tasks.md)
  Complete these tasks to prepare the target Oracle Database for use.
