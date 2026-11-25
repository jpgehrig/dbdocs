## 5.241 DBA_PENDING_TRANSACTIONS

`DBA_PENDING_TRANSACTIONS` describes unresolved transactions (either due to failure or if the coordinator has not sent a commit/rollback).

| Column     | Datatype  | NULL | Description                                                |
|:-----------|:----------|:-----|:-----------------------------------------------------------|
| `FORMATID` | `NUMBER`  |      | The format identifier of the transaction identifier        |
| `GLOBALID` | `RAW(64)` |      | The global part (gtrid) of the transaction identifier      |
| `BRANCHID` | `RAW(64)` |      | The branch qualifier (bqual) of the transaction identifier |
