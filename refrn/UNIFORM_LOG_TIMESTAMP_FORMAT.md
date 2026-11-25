## 1.375 UNIFORM_LOG_TIMESTAMP_FORMAT

`UNIFORM_LOG_TIMESTAMP_FORMAT` specifies that a uniform timestamp format be used in Oracle Database trace (.trc) files and log files (such as the alert log).

| Property            | Description                                   |
|:--------------------|:----------------------------------------------|
| Parameter type      | Boolean                                       |
| Default value       | `true`                                        |
| Modifiable          | `ALTER SYSTEM`                                |
| Modifiable in a PDB | No                                            |
| Range of values     | `true | false`                                |
| Basic               | No                                            |
| Oracle RAC          | Multiple instances should use the same value. |

When the value of `UNIFORM_LOG_TIMESTAMP_FORMAT` is `TRUE`, the format used for timestamps in trace files is standardized on universal time with millisecond precision. For example:

    2012-09-26 00:16:47.154

When the value of `UNIFORM_LOG_TIMESTAMP_FORMAT` is `FALSE`, trace files include a mix of timestamps using different precisions, with some timestamps showing local time and other timestamps showing universal time.
