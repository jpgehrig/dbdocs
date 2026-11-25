Oracle Database architecture on Windows. An Oracle instance is shown as a Windows service (a background process registered with the operating system). The service is started by Windows and requires no user interaction to start. It contains the memory structures and threads needed to access the database.

The client connects through a shadow thread to the Oracle instance. The shadow thread connects directly with the process monitor. The memory structures include a shared pool of a library cache and a data dictionary cache, a database buffer cache, and a redo log buffer.

The threads include the database writer, log writer, process monitor, system monitor, checkpoint process, distributed recovery process (all required while the database is available), and archive process (optional while the database is available).

There is an Oracle Database containing data files, control files, and redo log files. Associated with the database is the parameter file, password file, and archived log files.
