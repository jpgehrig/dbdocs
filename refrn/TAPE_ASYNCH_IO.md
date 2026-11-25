## 1.358 TAPE_ASYNCH_IO

`TAPE_ASYNCH_IO` controls whether I/O to sequential devices (for example, backup or restore of Oracle data to or from tape) is asynchronous—that is, whether parallel server processes can overlap I/O requests with CPU processing during table scans.

| Property            | Description    |
|:--------------------|:---------------|
| Parameter type      | Boolean        |
| Default value       | `true`         |
| Modifiable          | No             |
| Modifiable in a PDB | No             |
| Range of values     | `true | false` |
| Basic               | No             |

If your platform supports asynchronous I/O to sequential devices, Oracle recommends that you leave this parameter set to its default. However, if the asynchronous I/O implementation is not stable, you can set `TAPE_ASYNCH_IO` to `false` to disable asynchronous I/O. If your platform does not support asynchronous I/O to sequential devices, this parameter has no effect.

**See Also:**

[Oracle Database VLDB and Partitioning Guide](../vldbg/parameters-parallel-exec.md) for more information about this parameter
