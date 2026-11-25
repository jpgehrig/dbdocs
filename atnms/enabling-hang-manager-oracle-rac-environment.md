You can adjust the sensitivity, and control the size and number of the log files used by Hang Manager.

### Sensitivity

If Hang Manager detects a hang, then Hang Manager waits for a certain threshold time period to ensure that the sessions are hung. Change threshold time period by using `DBMS_HANG_MANAGER` to set the `sensitivity` parameter to either `Normal` or `High`. If the `sensitivity` parameter is set to `Normal`, then Hang Manager waits for the default time period. However, if the sensitivity is set to `High`, then the time period is reduced by 50%.

By default, the `sensitivity` parameter is set to `Normal`. To set Hang Manager sensitivity, run the following commands in SQL\*Plus as `SYS` user:

- To set the `sensitivity` parameter to `Normal`:
      exec dbms_hang_manager.set(dbms_hang_manager.sensitivity, dbms_hang_manager.sensitivity_normal);
- To set the `sensitivity` parameter to `High`:
      exec dbms_hang_manager.set(dbms_hang_manager.sensitivity, dbms_hang_manager.sensitivity_high);

### Size of the Trace Log File

The Hang Manager logs detailed diagnostics of the hangs in the trace files with `_base_` in the file name. Change the size of the trace files in bytes with the `base_file_size_limit` parameter. Run the following command in SQL\*Plus, for example, to set the trace file size limit to 100 MB:

    exec dbms_hang_manager.set(dbms_hang_manager.base_file_size_limit, 104857600);

### Number of Trace Log Files

The base Hang Manager trace files are part of a trace file set. Change the number of trace files in trace file set with the `base_file_set_count`  parameter. Run the following command in SQL\*Plus, for example, to set the number of trace files in trace file set to 6:

    exec dbms_hang_manager.set(dbms_hang_manager.base_file_set_count,6);

By default, `base_file_set_count` parameter is set to 5.

**Parent topic:** [Resolving Database and Database Instance Hangs](purpose-hang-manager.md)
