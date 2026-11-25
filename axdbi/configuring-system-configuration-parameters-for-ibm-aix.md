Use these instructions to verify and set the system configuration values manually if they are different from the minimum recommended value.

If you cannot use the Fixup scripts, then verify that the kernel parameters shown in the following table are set to values greater than or equal to the minimum value shown. If the current value for any parameter is greater than the value listed in this table, then the Fixup scripts do not change the value of that parameter.

Table A-2 Minimum System Configuration Parameter Values

| Parameter | Minimum Value |
|:----------|:--------------|
| maxuprocs | 16384         |
| ncargs    | 128           |

To verify and set the values manually:

1.  To verify that the maximum number of processes allowed per user is set to `16384` or greater:
    **Note:**

    For production systems, this value should be at least 128 plus the sum of the PROCESSES and PARALLEL_MAX_SERVERS initialization parameters for each database running on the system.
    1.  Enter the following command:
            # smit chgsys
    2.  Verify that the value shown for Maximum number of PROCESSES allowed per user is greater than or equal to 16384.
        If necessary, edit the existing value.
    3.  When you have finished making changes, press F10 to exit.
2.  To verify that long commands can be run from the shell, perform the following steps:
    **Note:**

    Oracle recommends that you set the ncargs system attribute to a value greater than or equal to 128. The ncargs attribute determines the maximum number of values that can be passed as command line arguments.
    1.   Enter the following command:
            # smit chgsys
    2.  Verify that the value shown for ARG/ENV list size in 4K byte blocks is greater than or equal to 128.
        If necessary, edit the existing value.
    3.  When you have finished making changes, press F10 to exit.

**Parent topic:** [Configuring Shell Limits and System Configuration Parameters for IBM AIX](configuring-shell-limits-and-system-configuration-parameters-for-ibm-aix.md)
