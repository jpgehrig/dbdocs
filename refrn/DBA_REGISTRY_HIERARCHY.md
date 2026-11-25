## 5.279 DBA_REGISTRY_HIERARCHY

`DBA_REGISTRY_HIERARCHY` displays information about the components loaded into the database, grouped by owner and organized in the component hierarchy.

| Column         | Datatype         | NULL       | Description                                                                                                                                                                     |
|:---------------|:-----------------|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NAMESPACE`    | `VARCHAR2(30)`   | `NOT NULL` | Component namespace                                                                                                                                                             |
| `COMP_ID`      | `VARCHAR2(4000)` |            | Component identifier                                                                                                                                                            |
| `VERSION`      | `VARCHAR2(30)`   |            | Component version loaded                                                                                                                                                        |
| `VERSION_FULL` | `VARCHAR2(30)`   |            | Component full version                                                                                                                                                          |
| `STATUS`       | `VARCHAR2(11)`   |            | Component status:<br>• `INVALID`<br>• `VALID`<br>• `LOADING`<br>• `LOADED`<br>• `UPGRADING`<br>• `UPGRADED`<br>• `DOWNGRADING`<br>• `DOWNGRADED`<br>• `REMOVING`<br>• `REMOVED` |
| `MODIFIED`     | `VARCHAR2(20)`   |            | Time when the component was last modified                                                                                                                                       |
