## 4.305 DBA_FLASHBACK_ARCHIVE_TS

`DBA_FLASHBACK_ARCHIVE_TS` describes all tablespaces in the flashback archives available in the database.

| Column                   | Datatype        | NULL       | Description                                                                                                           |
|:-------------------------|:----------------|:-----------|:----------------------------------------------------------------------------------------------------------------------|
| `FLASHBACK_ARCHIVE_NAME` | `VARCHAR2(255)` | `NOT NULL` | Name of the flashback archive                                                                                         |
| `FLASHBACK_ARCHIVE#`     | `NUMBER`        | `NOT NULL` | Number of the flashback archive                                                                                       |
| `TABLESPACE_NAME`        | `VARCHAR2(30)`  | `NOT NULL` | Name of a tablespace in the flashback archive                                                                         |
| `QUOTA_IN_MB`            | `VARCHAR2(40)`  |            | Maximum space (in MB) that can be used for Flashback Archive from the tablespace; NULL indicates no Quota restriction |
