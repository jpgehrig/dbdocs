## 6.597 USER_PASSWORD_LIMITS

`USER_PASSWORD_LIMITS` describes the password profile parameters that are assigned to the user.

| Column          | Datatype       | NULL       | Description                   |
|:----------------|:---------------|:-----------|:------------------------------|
| `RESOURCE_NAME` | `VARCHAR2(32)` | `NOT NULL` | Name of the password resource |
| `LIMIT`         | `VARCHAR2(40)` |            | Value of the resource limit   |
