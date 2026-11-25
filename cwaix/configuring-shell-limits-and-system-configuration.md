These topics explain how to configure shell limits and system configuration parameters manually if you cannot complete them using the fixup scripts.

**Note:**

The parameter and shell limit values shown in this section are recommended values only. For production database systems, Oracle recommends that you tune these values to optimize the performance of the system. See your operating system documentation for more information about tuning kernel parameters.

- [Configuring System Configuration Parameters for IBM AIX](configuring-system-configuration.md)
  Use these instructions to verify and set the system configuration values manually if they are different from the minimum recommended value.
- [Configuring Shell Limits on IBM AIX](configuring-shell-limits-on-ibm-aix.md)
  For IBM AIX on POWER Systems (64-bit), it is the ulimit settings that determine process memory related resource limits. Use these instructions to display and change the shell limit values if they are different from the recommended value.
- [Checking Asynchronous Input Output Processes](checking-asynchronous-input-output.md)
  On IBM AIX 6 and IBM AIX 7, the Asynchronous Input Output (AIO) device drivers are enabled by default. For both IBM AIX 6 and IBM AIX 7, increase the number of aioserver processes from the default value. The recommended value for aio_maxreqs is 64k (65536). Confirm this value for both IBM AIX 6 and IBM AIX 7.

**Parent topic:** [Completing Preinstallation Tasks Manually](completing-preinstallation-tasks-manually.md)
