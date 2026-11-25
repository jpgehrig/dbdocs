## 5.170 DBA_LOGSTDBY_SKIP_TRANSACTION

`DBA_LOGSTDBY_SKIP_TRANSACTION` displays the skip settings chosen. This view is for logical standby databases only.

| Column     | Datatype        | NULL | Description                        |
|:-----------|:----------------|:-----|:-----------------------------------|
| `XIDUSN`   | `NUMBER`        |      | Transaction ID undo segment number |
| `XIDSLT`   | `NUMBER`        |      | Transaction ID slot number         |
| `XIDSQN`   | `NUMBER`        |      | Transaction ID sequence number     |
| `CON_NAME` | `VARCHAR2(384)` |      | Container name                     |
