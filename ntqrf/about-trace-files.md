Oracle Database for Windows background threads use trace files to record occurrences and exceptions of database operations, and errors.

Background thread trace files are created and stored in the Automatic Diagnostic Repository (ADR) directory specified by the parameter `DIAGNOSTIC_DEST` in the initialization parameter file.

Oracle Database creates a different trace file for each foreground and background thread. The name of the trace file contains the name of the thread, followed by the extension ".`trc"`. The following are examples of foreground trace file names:

- `ops_ora_5804.trc`

- `ops_ora_4160.trc`

The following are the examples of the background trace file names:

- `ops_pmon_1556.trc`

- `ops_mmon_3768.trc`

- `ops_lgwr_2356.trc`

- `ops_dbw0_132.trc`

Trace files are also created for user threads and stored in the ADR directory specified by the parameter `DIAGNOSTIC_DEST` in the initialization parameter file. Trace files for user threads have the form `ora``xxxxx``.trc`, where `xxxxx` is a 5-digit number indicating the Windows thread `ID`.

**Parent topic:** [Monitoring a Database on Windows](monitoring-a-database-on-windows.md)
