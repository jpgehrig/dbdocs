## 4.220 DBA_CONTAINER_DATA

`DBA_CONTAINER_DATA` displays default (user-level) and object-specific `CONTAINER_DATA` attributes for container data objects.

Objects created with the `CONTAINER_DATA` clause include `CONTAINER_DATA` attributes.

| Column           | Datatype        | NULL | Description                                                                           |
|:-----------------|:----------------|:-----|:--------------------------------------------------------------------------------------|
| `USERNAME`       | `VARCHAR2(128)` |      | Name of the user whose attribute is described by this row                             |
| `DEFAULT_ATTR`   | `CHAR2(1)`      |      | An indicator of whether the attribute is a default attribute                          |
| `OWNER`          | `VARCHAR2(128)` |      | Name of the object owner if the attribute is object-specific                          |
| `OBJECT_NAME`    | `VARCHAR2(128)` |      | Name of the object if the attribute is object-specific                                |
| `ALL_CONTAINERS` | `VARCHAR2(1)`   |      | An indicator of whether this attribute applies to all containers                      |
| `CONTAINER_NAME` | `VARCHAR2(128)` |      | Name of a container included in this attribute if it does not apply to all containers |

**See Also:**

For more information about container data objects:

- "[CDB\_\* Views](cdb_-views.md)"

- "[ALL_TABLES](ALL_TABLES.md)"

- "[ALL_VIEWS](ALL_VIEWS.md)"

- "[ALL_VIEWS_AE](ALL_VIEWS_AE.md)"

- "[V\$ Views](about-dynamic-performance-views.md)"

- "[GV\$ Views](about-dynamic-performance-views.md)"

- [Oracle Multitenant Administrator's Guide](../multi/viewing-information-about-cdbs-and-pdbs-with-sql-plus.md)

- [Oracle Database Security Guide](../dbseg/configuring-privilege-and-role-authorization.md)
