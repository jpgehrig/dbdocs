On both UNIX and Windows platforms, bypassing the file system buffer cache ensures data is written to disk.

On UNIX, Oracle Database uses the` O_SYNC `flag to bypass the file system buffer cache. The flag name depends on the UNIX port.

On Windows, Oracle Database bypasses the file system buffer cache completely.

**Parent topic:** [Oracle Database Differences on Windows and UNIX](oracle-database-differences-on-windows-and-unix.md)
