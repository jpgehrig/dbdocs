A (manual) hot backup is equivalent to backing up a tablespace that is in an offline backup mode.

Backup strategy on UNIX is as follows: put the tablespace into backup mode, copy the files to the backup location, and bring the tablespace out of backup mode.

Windows supports the same backup strategy, but you cannot copy files in use with the usual Windows utilities. Use OCOPY to copy open database files to another disk location. Then use a utility to copy the files to tape.

**Parent topic:** [Oracle Database Differences on Windows and UNIX](oracle-database-differences-on-windows-and-unix.md)
