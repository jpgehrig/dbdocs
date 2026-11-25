## 6.621 USER_RESOURCE_LIMITS

`USER_RESOURCE_LIMITS` displays the resource limits for the current user.

| Column          | Datatype       | NULL       | Description                   |
|:----------------|:---------------|:-----------|:------------------------------|
| `RESOURCE_NAME` | `VARCHAR2(32)` | `NOT NULL` | Name of the resource          |
| `LIMIT`         | `VARCHAR2(40)` |            | Limit placed on this resource |
