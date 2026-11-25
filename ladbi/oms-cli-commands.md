## E Oracle Memory Speed CLI Commands

`omsfscmds` is a command line utility for administering Oracle Memory Speed (OMS). To use `omsfscmds`, ensure that the OMS daemon is running.

Example E-1 Running omsfscmds

Set the \$ORACLE SID to the same SID as the daemon and run `omsfscmds`.

    $ $ORACLE_HOME/bin/omsfscmds
    OMS>

- [mkfs and forcemkfs Command Reference](oms-mkfs-forcemkfs.md)
  Use `mkfs` and `forcemkfs` to format the OMS uber file placed in a PMEM DAX mount point.
- [mount, unmount and lsmount Command Reference](oms-mount-lsmount.md)
  Use `mount`, `umount` and, `lsmount` to manage and query the Oracle Memory Speed file system mount points.
- [df Command Reference](oms-disk-free-space.md)
  Use `df` to determine the total space, used space, and free space in a mounted Oracle Memory Speed (OMS) file system.
- [cp Command Reference](oms-copy-file.md)
  Use the copy command `cp` to copy files.
- [ls and lls Command Reference](oms-list-file.md)
  Use `ls` to list files in the Oracle Memory Speed (OMS) mount point, and `lls` to list files in the OMS mount point with additional information for each file.
- [rm Command Reference](oms-delete-file.md)
  Use the `rm` command to delete a file from an Oracle Memory Speed (OMS) mount point.
- [cd and pwd Command Reference](oms-cd-pwd.md)
  Use the current directory `cd` command to set the current working Oracle Memory Speed (OMS) mount point. Use the present working directory `pwd` command to display the current OMS mount point set by the previous `cd` command.
- [lsom and lsof Command Reference](oms-lsom-lsof.md)
  Use the `ls` of mount point `lsom` command to list the Oracle process identifiers of all processes that have opened files in an Oracle Memory Speed (OMS) mount point.
- [Daemon Control Command Reference](oms-daemon-control.md)
  Use the `daemon` command to control the OMS daemon process.
- [Diagnostics and Tracing](oms-diagnostics-tracing.md)
  The `dump` command has many sub options to print diagnostic information.
