This illustration shows an example archived-log downstream capture configuration that involves the following steps:

1.  Users make changes to database objects at a source database.

2.  The log writer process (LGWR) at the source database logs these changes in the online redo log.

3.  The archiver writes the redo data to archived redo log files.

4.  Redo log files are copied to the downstream database.

5.  A capture process captures changes in the archived redo log files at the downstream database and enqueues these changes as LCRs at the downstream database.
