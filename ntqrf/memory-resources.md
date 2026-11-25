The resources provided by the UNIX default kernels are often inadequate for a medium or large instance of Oracle Database.

The maximum size of a shared memory segment (`SHMMAX`) and maximum number of semaphores available (`SEMMNS`) may be too low for Oracle Database recommendations.

On Windows, fewer resources are needed for interprocess communication (IPC), because the Oracle Database relational database management system is thread-based and not process-based. These resources, including shared memory and semaphores, are not adjustable by the user.

**Parent topic:** [Oracle Database Differences on Windows and UNIX](oracle-database-differences-on-windows-and-unix.md)
