This chapter shows how to use Database Configuration Assistant (DBCA) to create the destination database in the target server.

Run the PING command on source and target server to check if both of the servers are reachable.

- Creating the Target Database
  Create a new database on the target system.

### Creating the Target Database

Create a new database on the target system.

The new target database consists initially of just `SYSTEM`, `SYSAUX`, `UNDO`, temporary tablespaces, and user tablespaces. You can use DBCA to create the target database.

When creating the target database, consider the following:

- Although all user tablespaces from the original source database are transported and plugged into the new target database, initially the target database must contain placeholder tablespaces for the user tablespaces that will be transported. The size of the user tablespaces initially created in the target database can be small; the target tablespaces do not have to match the sizes in the source database. The placeholder tablespaces will be dropped from the target database before transporting the tablespaces from the source system.

- The sizes of the `SYSTEM`, `SYSAUX`, `UNDO`, and temporary tablespaces must be same or larger than those tablespaces on the source database.

- The sizes of log files and number of members for each log file group in the new target database should be the same as, or larger than, the source database.

- The source and target database must use the same character set and same national character set. Check the source database character sets by issuing the following query:
      SQL> select * from database_properties where property_name like '%CHARACTERSET';

- The database options and components used in the source database should be installed on the target database.

  - Query the `V$OPTION` view to get currently installed database options.

  - Query `DBA_REGISTRY` to get currently installed database components.

**Parent topic:** Preparing the Target Server
