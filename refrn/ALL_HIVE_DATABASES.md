## 2.216 ALL_HIVE_DATABASES

`ALL_HIVE_DATABASES` describes all the Hive schemas accessible to the current user in a Hadoop cluster.

### Related Views

- `DBA_HIVE_DATABASES` describes all the Hive schemas in a Hadoop cluster.

- `USER_HIVE_DATABASES` describes all the Hive schemas owned by the current user in a Hadoop cluster.

| Column          | Datatype         | NULL | Description                                                            |
|:----------------|:-----------------|:-----|:-----------------------------------------------------------------------|
| `CLUSTER_ID`    | `VARCHAR2(4000)` |      | Hadoop cluster name                                                    |
| `DATABASE_NAME` | `VARCHAR2(4000)` |      | Name of the Hive database                                              |
| `DESCRIPTION`   | `VARCHAR2(4000)` |      | Description of the Hive database                                       |
| `DB_LOCATION`   | `VARCHAR2(4000)` |      | Physical location of the Hive database                                 |
| `HIVE_URI`      | `VARCHAR2(4000)` |      | The connection string (URI and port number) for the metastore database |

**See Also:**

- "[DBA_HIVE_DATABASES](DBA_HIVE_DATABASES.md)"

- "[USER_HIVE_DATABASES](USER_HIVE_DATABASES.md)"
