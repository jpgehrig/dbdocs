Consider the columns of each table of `IX` sample schema.

- Table IX.ORDERS_QUEUETABLE

- Table IX.STREAMS_QUEUE_TABLE

### 4.9.1 Table IX.ORDERS_QUEUETABLE

Table 4-24 IX.ORDERS_QUEUETABLE Table Description

| Column Name         | Null?      | Type              |
|:--------------------|:-----------|:------------------|
| `Q_NAME`            |            | `VARCHAR2(30)`    |
| `MSGID`             | `NOT NULL` | `RAW(16)`         |
| `CORRID`            |            | `VARCHAR2(128)`   |
| `PRIORITY`          |            | `NUMBER`          |
| `STATE`             |            | `NUMBER`          |
| `DELAY`             |            | `TIMESTAMP(6)`    |
| `EXPIRATION`        |            | `NUMBER`          |
| `TIME_MANAGER_INFO` |            | `TIMESTAMP(6)`    |
| `LOCAL_ORDER_NO`    |            | `NUMBER`          |
| `CHAIN_NO`          |            | `NUMBER`          |
| `CSCN`              |            | `NUMBER`          |
| `DSCN`              |            | `NUMBER`          |
| `ENQ_TIME`          |            | `TIMESTAMP(6)`    |
| `ENQ_UID`           |            | `VARCHAR2(30)`    |
| `ENQ_TID`           |            | `VARCHAR2(30)`    |
| `DEQ_TIME`          |            | `TIMESTAMP(6)`    |
| `EEQ_UID`           |            | `VARCHAR2(30)`    |
| `DEQ_TID`           |            | `VARCHAR2(30)`    |
| `RETRY_COUNT`       |            | `NUMBER`          |
| `EXCEPTION_QSCHEMA` |            | `VARCHAR2(30)`    |
| `EXCEPTION_QUEUE`   |            | `VARCHAR2(30)`    |
| `STEP_NO`           |            | `NUMBER`          |
| `RECIPIENT_KEY`     |            | `NUMBER`          |
| `DEQUEUE_MSGID`     |            | `RAW(16)`         |
| `SENDER_NAME`       |            | `VARCHAR2(30)`    |
| `SENDER_ADDRESS`    |            | `VARCHAR2(1024)`  |
| `SENDER_PROTOCOL`   |            | `NUMBER`          |
| `USER_DATA`         |            | `ORDER_EVENT_TYP` |
| `USER_PROP`         |            | `SYS.ANYDATA`     |

### 4.9.2 Table IX.STREAMS_QUEUE_TABLE

Table 4-25 IX.STREAMS_QUEUE_TABLE Table Description

| Column Name         | Null?      | Type              |
|:--------------------|:-----------|:------------------|
| `Q_NAME`            |            | `VARCHAR2(30)`    |
| `MSGID`             | `NOT NULL` | `RAW(16)`         |
| `CORRID`            |            | `VARCHAR2(128)`   |
| `PRIORITY`          |            | `NUMBER`          |
| `STATE`             |            | `NUMBER`          |
| `DELAY`             |            | `TIMESTAMP(6)`    |
| `EXPIRATION`        |            | `NUMBER`          |
| `TIME_MANAGER_INFO` |            | `TIMESTAMP(6)`    |
| `LOCAL_ORDER_NO`    |            | `NUMBER`          |
| `CHAIN_NO`          |            | `NUMBER`          |
| `CSCN`              |            | `NUMBER`          |
| `DSCN`              |            | `NUMBER`          |
| `ENQ_TIME`          |            | `TIMESTAMP(6)`    |
| `ENQ_UID`           |            | `VARCHAR2(30)`    |
| `ENQ_TID`           |            | `VARCHAR2(30)`    |
| `DEQ_TIME`          |            | `TIMESTAMP(6)`    |
| `EEQ_UID`           |            | `VARCHAR2(30)`    |
| `DEQ_TID`           |            | `VARCHAR2(30)`    |
| `RETRY_COUNT`       |            | `NUMBER`          |
| `EXCEPTION_QSCHEMA` |            | `VARCHAR2(30)`    |
| `EXCEPTION_QUEUE`   |            | `VARCHAR2(30)`    |
| `STEP_NO`           |            | `NUMBER`          |
| `RECIPIENT_KEY`     |            | `NUMBER`          |
| `DEQUEUE_MSGID`     |            | `RAW(16)`         |
| `SENDER_NAME`       |            | `VARCHAR2(30)`    |
| `SENDER_ADDRESS`    |            | `VARCHAR2(1024)`  |
| `SENDER_PROTOCOL`   |            | `NUMBER`          |
| `USER_DATA`         |            | `ORDER_EVENT_TYP` |
| `USER_PROP`         |            | `SYS.ANYDATA`     |
