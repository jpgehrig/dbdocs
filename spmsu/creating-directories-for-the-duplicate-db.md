On the destination host, you must create the directories that RMAN uses to store the duplicate database files on the destination host.

This includes the directories that store the data files, control files, online redo log files, and temp files.

Use the `NOFILENAMECHECK` clause to indicate that RMAN must not display an error when the names of the database files are the same in the source and duplicate database.

**Parent topic:** [Preparing the Auxiliary Instance on the Destination Host](preparing-the-auxiliary-instance-destination-host.md)
