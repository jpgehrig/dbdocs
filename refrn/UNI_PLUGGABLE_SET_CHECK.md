## 6.260 UNI_PLUGGABLE_SET_CHECK

`UNI_PLUGGABLE_SET_CHECK` contains pluggable check information.

| Column            | Datatype        | NULL | Description                          |
|:------------------|:----------------|:-----|:-------------------------------------|
| `OBJ1_OWNER`      | `VARCHAR2(128)` |      | Owner of object                      |
| `OBJ1_NAME`       | `VARCHAR2(128)` |      | Object 1                             |
| `OBJ1_SUBNAME`    | `VARCHAR2(128)` |      | SubObject1Name                       |
| `OBJ1_TYPE`       | `VARCHAR2(18)`  |      | Object Type                          |
| `TS1_NAME`        | `VARCHAR2(30)`  |      | Tablespace containing Object 1       |
| `OBJ2_NAME`       | `VARCHAR2(128)` |      | Object Name                          |
| `OBJ2_SUBNAME`    | `VARCHAR2(128)` |      | SubObject2Name                       |
| `OBJ2_TYPE`       | `VARCHAR2(18)`  |      | Object Type                          |
| `OBJ2_OWNER`      | `VARCHAR2(128)` |      | Object owner of second object        |
| `TS2_NAME`        | `VARCHAR2(30)`  |      | Tablespace containing Object 1       |
| `CONSTRAINT_NAME` | `VARCHAR2(128)` |      | Name of dependent constraint         |
| `REASON`          | `VARCHAR2(86)`  |      | Reason for Pluggable check violation |
| `MESG_ID`         | `NUMBER`        |      | The message ID                       |
