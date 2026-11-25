## 1.196 MAX_DATAPUMP_JOBS_PER_PDB

`MAX_DATAPUMP_JOBS_PER_PDB` determines the maximum number of concurrent Oracle Data Pump jobs per PDB.

| Property            | Description                                      |
|:--------------------|:-------------------------------------------------|
| Parameter type      | String                                           |
| Syntax              | `MAX_DATAPUMP_JOBS_PER_PDB = { AUTO | integer }` |
| Default value       | 100                                              |
| Modifiable          | `ALTER SYSTEM`                                   |
| Modifiable in a PDB | Yes                                              |
| Range of values     | `0` to `250` or `AUTO`                           |
| Basic               | No                                               |
| Oracle RAC          | The same value must be used on all instances.    |

The default value will not work for all databases. Database administrators will have to determine if the default value works well for their database.

When this parameter has a value of `AUTO`, Oracle Data Pump will derive its actual value to be 50% of the `SESSIONS` initialization parameter.

A value that is too large could cause Oracle Data Pump to consume too many system resources, while a value that is too small could prevent users from performing their Oracle Data Pump tasks.

The main resource Oracle Data Pump uses is shared pool in the System Global Area (SGA) for the database. Parallel jobs increase the number of sessions and, depending on the job, the number of PX servers used.

**See Also:**

- [Oracle Database Utilities](../sutil/oracle-data-pump-overview.md) for more information about using Oracle Data Pump with CDBs

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_DATAPUMP.md) for more information about the `DBMS_DATAPUMP` PL/SQL package
