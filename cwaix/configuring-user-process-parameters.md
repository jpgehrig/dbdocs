Verify that the maximum number of processes allowed for each user is set to 16384 or greater.

1.  Enter the following command:
        # smit chgsys
2.  Verify that the value shown for Maximum number of PROCESSES allowed for each user is greater than or equal to 16384. If necessary, edit the existing value.
3.  When you have finished making changes, press Enter, then Esc+0 (Exit) to exit.
    For production systems, this value should be at least 128 plus the sum of the `PROCESSES` and `PARALLEL_MAX_SERVERS` initialization parameters for each database running on the system.

**Parent topic:** [Tuning AIX System Environment](tuning-aix-system-environment.md)
