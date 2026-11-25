## 4.314 DBA_GG_PROC_OBJECT_EXCLUSION

`DBA_GG_PROC_OBJECT_EXCLUSION` provides details about all tables that should be filtered when operating on given objects.

| Column          | Datatype        | NULL | Description                                    |
|:----------------|:----------------|:-----|:-----------------------------------------------|
| `PACKAGE_OWNER` | `VARCHAR2(384)` |      | Procedure package owner                        |
| `PACKAGE_NAME`  | `VARCHAR2(384)` |      | Procedure package name                         |
| `OBJECT_OWNER`  | `VARCHAR2(384)` |      | Object owner to filter for the given procedure |
| `OBJECT_NAME`   | `VARCHAR2(384)` |      | Object name to filter for the given procedure  |
