## 1.167 JOB_QUEUE_PROCESSES

`JOB_QUEUE_PROCESSES` specifies the maximum number of job workers per instance that can be created for the execution of `DBMS_JOB` jobs and Oracle Scheduler (`DBMS_SCHEDULER`) jobs.

| Property            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Parameter type      | Integer                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Default value       | Derived. The lesser value of:<br>• `CPU_COUNT` \* 20<br>• `SESSIONS` / 4<br>For a CDB, if the result of the above derivation is less than twice the number of open containers in the CDB, then the value of this parameter is adjusted to equal twice the number of open containers in the CDB. Containers include `CDB$ROOT`, `PDB$SEED`, PDBs, application roots, application seeds, and application PDBs. You can obtain the number of open containers in a CDB with the following query:<br>`SELECT COUNT(*) FROM V$CONTAINERS`<br>`  WHERE open_mode != 'MOUNTED';` |
| Modifiable          | `ALTER SYSTEM`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Modifiable in a PDB | Yes                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Range of values     | `0` to `4000`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Basic               | No                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Oracle RAC          | Multiple instances can have different values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |

`DBMS_JOB` and Oracle Scheduler share the same job coordinator and job workers, and they are both controlled by the `JOB_QUEUE_PROCESSES` parameter. The actual number of job workers created for Oracle Scheduler jobs is auto-tuned by the Scheduler depending on several factors, including available resources, Resource Manager settings, and currently running jobs. However, the combined total number of job workers running `DBMS_JOB` jobs and Oracle Scheduler jobs in a non-CDB, CDB, or PDB can never exceed the value of `JOB_QUEUE_PROCESSES` for that non-CDB, CDB, or PDB.

The default value for `JOB_QUEUE_PROCESSES` provides a compromise between quality of service for applications and reasonable use of system resources. However, it is possible that the default value does not suit every environment. In such cases, you can use the following guidelines to fine tune this parameter:

- In a non-CDB:

  Set `JOB_QUEUE_PROCESSES` to the maximum number of job workers that can be used simultaneously in the entire database instance. If `JOB_QUEUE_PROCESSES` is `0`, then `DBMS_JOB` jobs and Oracle Scheduler jobs will not run in the database instance.

- In a CDB root:

  Set `JOB_QUEUE_PROCESSES` to the maximum number of job workers that can be used simultaneously in the entire CDB. Oracle recommends that you set the value of this parameter to at least twice the number of open containers in the CDB, otherwise, there might be severe starvation between PDBs trying to run multiple jobs. If `JOB_QUEUE_PROCESSES` is set to `0` in a CDB root, then `DBMS_JOB` and Oracle Scheduler jobs cannot run in the CDB root or in any PDB, regardless of the `JOB_QUEUE_PROCESSES` setting at the PDB level.

- In a PDB:

  Set `JOB_QUEUE_PROCESSES` to the maximum number of job workers that can be used simultaneously in the PDB. The actual number depends on the resources assigned by Resource Manager and the demand in other containers. When multiple PDBs request jobs, Oracle Scheduler attempts to give all PDBs a fair share of the processes. Oracle recommends that you set the value of this parameter to at least `2` in a PDB. However, if you do not want to run `DBMS_JOB` and Oracle Scheduler jobs in a PDB, then set `JOB_QUEUE_PROCESSES` to `0` in the PDB.

Materialized views and AutoTask use Oracle Scheduler for automatic refreshes. Setting `JOB_QUEUE_PROCESS` to `0` will disable these features and any other features that use Oracle Scheduler or `DBMS_JOB`.

**Note:**

`DBMS_JOB` is deprecated in Oracle Database 12c Release 2 (12.2.0.1) and may be removed in a future release. Oracle recommends that you use `DBMS_SCHEDULER` instead.

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_SCHEDULER.md) for more information on the `DBMS_SCHEDULER` package

- [Oracle Database Data Warehousing Guide](../dwhsg/refreshing-materialized-views.md) for more information on managing materialized views

- [Oracle Database Advanced Queuing User's Guide](../adque/aq-basic-components.md) for more information about job queue processes

- [Oracle Database Administrator’s Guide](../admin/oracle-scheduler-concepts.md) for more information about the maximum number of scheduler job processes
