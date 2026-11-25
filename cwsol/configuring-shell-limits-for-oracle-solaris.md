For each installation software owner user account, check the shell limits for installation.

**Note:**

The shell limit values in this section are minimum values only. For production database systems, Oracle recommends that you tune these values to optimize the performance of the system. See your operating system documentation for more information about configuring shell limits.

The ulimit settings determine process memory related resource limits. Verify that the following shell limits are set to the values shown:

Table B-4 Oracle Solaris Shell Limit Recommended Ranges

| Resource Shell Limit | Description                                   | Soft Limit     | Hard Limit     |
|:---------------------|:----------------------------------------------|:---------------|:---------------|
| STACK                | Size (KB) of the stack segment of the process | at least 10240 | at most 32768  |
| NOFILES              | Open file descriptors                         | at least 1024  | at least 65536 |
| MAXUPRC or MAXPROC   | Maximum user processes                        | at least 2047  | at least 16384 |

To display the current value specified for these shell limits:

    ulimit -s
    ulimit -n

**Parent topic:** [Completing Preinstallation Tasks Manually](completing-preinstallation-tasks-manually.md)
