## lsom and lsof Command Reference

Use the `ls` of mount point `lsom` command to list the Oracle process identifiers of all processes that have opened files in an Oracle Memory Speed (OMS) mount point.

### Syntax

    dump lsom mount_point dump_file_name
    dump lsof absolute_file dump_file_name

### Usage Notes

Use the `ls` of file `lsof` to list the Oracle process identifiers of all processes that have the specified file open.

Browse the alert log to determine the OS pid of the process from the Oracle pid. `lsom` and `lsof` are available only when the Oracle instance is up-and-running.

### Examples

    OMS> dump lsom /oracle/omsfs_1 /tmp/lsom
    OMS> exit
    $ cat /tmp/lsom
    18 /control01.ctl
    18 /df1.dbf
    18 /tempfile
    19 /df1.dbf
    20 /df1.dbf
    21 /df1.dbf
    22 /df1.dbf
    23 /df1.dbf
    24 /df1.dbf
    25 /df1.dbf
    26 /df1.dbf
    27 /df1.dbf
    28 /df1.dbf
    29 /df1.dbf
    31 /control01.ctl
    30 /control01.ctl
    30 /df1.dbf
    32 /tempfile
    43 /control01.ctl
    8 /control01.ctl
    47 /control01.ctl

    OMS> dump lsof /oracle/omsfs_2/control02.ctl /tmp/lsof
    OMS> exit
    $ cat /tmp/lsof
    18 /control02.ctl
    31 /control02.ctl
    30 /control02.ctl
    43 /control02.ctl
    8 /control02.ctl
    47 /control02.ctl

**Parent topic:** [Oracle Memory Speed CLI Commands](oms-cli-commands.md)
