## 1.87 DB_FLASHBACK_RETENTION_TARGET

`DB_FLASHBACK_RETENTION_TARGET` specifies the upper limit (in minutes) on how far back in time the database may be flashed back.

| Property            | Description                |
|:--------------------|:---------------------------|
| Parameter type      | Integer                    |
| Default value       | `1440` (minutes)           |
| Modifiable          | `ALTER SYSTEM ... SID='*'` |
| Modifiable in a PDB | No                         |
| Range of values     | `0` to 2<sup>31</sup> - 1  |
| Basic               | No                         |

How far back one can flashback a database depends on how much flashback data Oracle has kept in the fast recovery area.

**See Also:**

[Oracle Data Guard Broker](../dgbkr/oracle-data-guard-broker-concepts.md) for enabling Flashback Database on Oracle Data Guard primary and target standby databases
