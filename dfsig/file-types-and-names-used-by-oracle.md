The following is a list of file types and names used by Oracle Database on BS2000:

### sid.DBS.xxx.DBF

Database files such as `sid`.`DBS`.`CONTROL`.`DBF`, `sid`.`DBS`.`DATABASE1`.`DBF`, or `sid`.`DBS`.`LOG1`.`DBF` contain the entire Oracle database including data dictionary, user tables, log files, and so on.

### sid.DBS.INIT.ORA

Parameter file used when an instance is started.

### sid.P.ORAENV

Environment definition file, which defines the program environment. You must run this file before starting an instance or an application:

`/CALL-PROCEDURE` `sid`.`P`.`ORAENV`

### S.E.tsn.YYYY-MM-DD.hh.mm.ss

Temporary `ENTER-PROCEDURE` file for starting the background processes.

### S.OUT.tsn.YYYY-MM-DD.hhmmss.number

Temporary files of background processes containing the runtime information. After a task is successfully completed, these files are removed. These files can help in diagnosis.

### L.sid.xxxx.SYSOUT.tsn

Run-time listing documenting the start of a background process. When a process finishes, orderly listings are removed, except the `SDF-P` variable `BGJOUT` is set to `KEEP` in `sid`.`P`.`ORAENV` for diagnosis purposes. xxxx corresponds with the identifier of Oracle background jobs.

### Oracle Net Services LOG files

All errors encountered in Oracle network products are appended to a log file.

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/troubleshooting-oracle-net-services.md) for more information about Oracle Net Services log files

### T.sid.INSTALL.E.SUPER

Temporary file created by the BS2000 procedure `INSTALL.P.SUPER`. You can remove this file after a successful Oracle Database installation.

### T.sid.INSTALL.E.SUPER.72

Temporary file created by the BS2000 procedure `INSTALL.P.SUPER`. You can remove this file after a successful Oracle Database installation.

### L.sid.xxx.LOG

Log file created by the BS2000 procedure `INSTALL.P.SUPER`, for example, `L`.`sid`.`CATALOG`.`LOG`. You can remove this file after a successful Oracle Database installation.

### ORAXALOG.tsn-NULL-YYMMDD.TRC

This file is used to trace errors when openUTM is used with Oracle Database. This file is created only when an error occurs or when tracing is turned on. You can replace `NULL` by a `db_name` when specified in the open string.
