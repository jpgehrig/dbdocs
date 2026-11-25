## 5.287 DBA_RESOURCE_INCARNATIONS

`DBA_RESOURCE_INCARNATIONS` lists all resource incarnations that are running or eligible for HA status notification.

| Column           | Datatype                      | NULL       | Description                                   |
|:-----------------|:------------------------------|:-----------|:----------------------------------------------|
| `RESOURCE_TYPE`  | `VARCHAR2(30)`                | `NOT NULL` | Type of resource                              |
| `RESOURCE_NAME`  | `VARCHAR2(256)`               |            | Name of resource                              |
| `DB_UNIQUE_NAME` | `VARCHAR2(30)`                | `NOT NULL` | Database unique name                          |
| `DB_DOMAIN`      | `VARCHAR2(128)`               | `NOT NULL` | Database domain                               |
| `INSTANCE_NAME`  | `VARCHAR2(30)`                | `NOT NULL` | Name of instance at which resource is located |
| `HOST_NAME`      | V`ARCHAR2(512)`               |            | Name of host at which resource is located     |
| `STARTUP_TIME`   | `TIMESTAMP(9) WITH TIME ZONE` |            | Resource startup date and time                |
