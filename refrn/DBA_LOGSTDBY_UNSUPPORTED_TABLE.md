## 5.172 DBA_LOGSTDBY_UNSUPPORTED_TABLE

`DBA_LOGSTDBY_UNSUPPORTED_TABLE` displays the data tables that are not supported by Logical Standby.

The data displayed pertains to the container in which the view is queried. This view is for logical standby databases only.

| Column       | Datatype        | NULL | Description                    |
|:-------------|:----------------|:-----|:-------------------------------|
| `OWNER`      | `VARCHAR2(128)` |      | Owner of the unsupported table |
| `TABLE_NAME` | `VARCHAR2(128)` |      | Name of the unsupported table  |
