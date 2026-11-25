## 1.347 SQL_TRACE

`SQL_TRACE` enables or disables the SQL trace facility.

| Property            | Description                     |
|:--------------------|:--------------------------------|
| Parameter type      | Boolean                         |
| Default value       | `false`                         |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM` |
| Modifiable in a PDB | Yes                             |
| Range of values     | `true | false`                  |
| Basic               | No                              |

Setting this parameter to `true` provides information on tuning that you can use to improve performance.

**Note:**

Using this initialization parameter to enable the SQL trace facility for the entire instance can have a severe performance impact. Enable the facility for specific sessions using the `ALTER SESSION` statement. If you must enable the facility on an entire production environment, then you can minimize performance impact by:

- Maintaining at least 25% idle CPU capacity

- Maintaining adequate disk space for the `USER_DUMP_DEST` location

- Striping disk space over sufficient disks

**Note:**

The `SQL_TRACE` parameter is deprecated. Oracle recommends that you use the `DBMS_MONITOR` and `DBMS_SESSION` packages instead. `SQL_TRACE` is retained for backward compatibility only.

**See Also:**

- "[USER_DUMP_DEST](USER_DUMP_DEST.md)"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_MONITOR.md) for more information about the `DBMS_MONITOR` package

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_SESSION.md) for more information about the `DBMS_SESSION` package

- [Oracle Database Performance Tuning Guide](../tgdba/part-II-diagnosing-and-tuning-database-performance.md) for more information about performance diagnostic tools
