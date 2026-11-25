## 4.255 DBA_DDL_LOCKS

`DBA_DDL_LOCKS` lists all DDL locks held in the database and all outstanding requests for a DDL lock.

| Column           | Datatype         | NULL | Description                                                                                                                                                          |
|:-----------------|:-----------------|:-----|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `SESSION_ID`     | `NUMBER`         |      | Session identifier                                                                                                                                                   |
| `OWNER`          | `VARCHAR2(128)`  |      | Owner of the lock                                                                                                                                                    |
| `NAME`           | `VARCHAR2(1000)` |      | Name of the lock                                                                                                                                                     |
| `TYPE`           | `VARCHAR2(40)`   |      | Lock type:<br>• `Cursor`<br>• `Table/Procedure/Type`<br>• `Body`<br>• `Trigger`<br>• `Index`<br>• `Cluster`<br>• `Java Source`<br>• `Java Resource`<br>• `Java Data` |
| `MODE_HELD`      | `VARCHAR2(9)`    |      | Lock mode:<br>• `None`<br>• `Null`<br>• `Share`<br>• `Exclusive`                                                                                                     |
| `MODE_REQUESTED` | `VARCHAR2(9)`    |      | Lock request type:<br>• `None`<br>• `Null`<br>• `Share`<br>• `Exclusive`                                                                                             |

**See Also:**

[Oracle Database Concepts](../cncpt/data-concurrency-and-consistency.md) for more information about DDL locks
