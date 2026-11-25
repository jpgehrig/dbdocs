This illustration shows an example real-time downstream capture configuration that involves the following steps:

1.  Users make changes to database objects at a source database.

2.  The log writer process (LGWR) at the source database logs these changes in the online redo log at the source database.

3.  Redo transport services at the source database sends redo data to the downstream database.

4.  Remote file server (RFS) at the downstream database receives the redo data over the network from the LGWR at the source database.

5.  RFS logs the redo data in the standby redo log at the downstream database.

6.  The archiver writes the redo data in the standby redo log to archived redo log files at the downstream database.

7.  At the downstream database, a capture process captures changes standby redo log whenever possible and in the archived redo log files whenever necessary and enqueues these changes as LCRs at the downstream database.
