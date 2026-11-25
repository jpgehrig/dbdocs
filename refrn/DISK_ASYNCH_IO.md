## 1.109 DISK_ASYNCH_IO

`DISK_ASYNCH_IO` controls whether I/O to datafiles, control files, and logfiles is asynchronous (that is, whether parallel server processes can overlap I/O requests with CPU processing during table scans).

| Property            | Description    |
|:--------------------|:---------------|
| Parameter type      | Boolean        |
| Default value       | `true`         |
| Modifiable          | No             |
| Modifiable in a PDB | No             |
| Range of values     | `true | false` |
| Basic               | No             |

If your platform supports asynchronous I/O to disk, Oracle recommends that you leave this parameter set to its default value. However, if the asynchronous I/O implementation is not stable, you can set this parameter to `false` to disable asynchronous I/O. If your platform does not support asynchronous I/O to disk, this parameter has no effect.

If you set `DISK_ASYNCH_IO` to `false`, then you can increase `DB_WRITER_PROCESSES` or use `DBWR_IO_SLAVES` to simulate asynchronous I/O.

**See Also:**

- "[DB_WRITER_PROCESSES](DB_WRITER_PROCESSES.md)"

- "[DBWR_IO_SLAVES](DBWR_IO_SLAVES.md)"

- [Oracle Database Performance Tuning Guide](../tgdba/instance-tuning-using-performance-views.md) for more information
