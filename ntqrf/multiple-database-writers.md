On UNIX, you can specify many database writer process with initialization parameter `DB_WRITERS`.

Multiple database writers can help, for example, when a UNIX port does not support asynchronous I/O.

`DB_WRITERS` is supported but typically unnecessary on Windows, which has its own asynchronous I/O capabilities.

**See Also:**

[Oracle Database Specifications for Windows](oracle-database-specifications-for-windows.md)

**Parent topic:** [Oracle Database Differences on Windows and UNIX](oracle-database-differences-on-windows-and-unix.md)
