## omsfscmds Command Reference

Use the various `omsfscmds` commands to perform basic file system operations, such as `mkfs`, `mount`, and `umount`.

### Purpose

`omsfscmds` is a command line utility for administering Oracle Memory Speed (OMS). To use `omsfscmds`, ensure that the OMS daemon is running.

Example 8-5 omsfscmds for Mounting the File System

Set the \$ORACLE SID to the same SID as the daemon and run `omsfscmds`.

    $ $ORACLE_HOME/bin/omsfscmds
    OMS> mount /mnt/pmem0/omsuberfile.test /oracle/omsfs_1

In this example, the PMEM device `/mnt/pmem0/omsuberfile.test` is mounted in the Oracle Database path `/oracle/omsfs_1`.

### Parameters

| Command                                                                        | Description                                                                                                                                                                                                                                                                                                                                |
|:-------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `help`                                                                         | Use the help command to learn more about each command.                                                                                                                                                                                                                                                                                     |
| `mkfs` pmem_device block_size                                                  | Use this command to format a persistent memory (PMEM) device pmem_device with block size block_size.                                                                                                                                                                                                                                       |
| `forcemkfs` pmem_device block_size                                             | Use this command to format the existing file system and create a new file system with persistent memory (PMEM) device pmem_device with block size block_size.                                                                                                                                                                              |
| `mount` pmem_device mount_path                                                 | Use this command to mount a PMEM device pmem_device in the mount path mount_path.                                                                                                                                                                                                                                                          |
| `umount` mount_path                                                            | Use this command to unmount a PMEM device from the mount path mount_path.                                                                                                                                                                                                                                                                  |
| `lsmount`                                                                      | Use this command to list all mounted file systems.                                                                                                                                                                                                                                                                                         |
| `df` mount_path                                                                | Display the amount of disk space available on the file system in the mount_path.                                                                                                                                                                                                                                                           |
| `cp` source_filepath dest_filepath                                             | Use this command to copy from the source file store source_filepath to the destination file store dest_filepath.                                                                                                                                                                                                                           |
| `ls` mount_path                                                                | Use this command to list all files in the mount path mount_path.                                                                                                                                                                                                                                                                           |
| `lls` mount_path                                                               | Use this command to list detailed information about all files in the mount path mount_path.                                                                                                                                                                                                                                                |
| `rm` file_path                                                                 | Use this command to delete a file in the path file_path.                                                                                                                                                                                                                                                                                   |
| `cd` dir_path                                                                  | Use this command to change the current working directory to the path dir_path.                                                                                                                                                                                                                                                             |
| `pwd`                                                                          | Use this command to print the current directory.                                                                                                                                                                                                                                                                                           |
| `dump` module_option pmem_device/mount_point/absolute_file_path dump_file_name | Use this command to dump diagnostic information to `dump_file_name`.<br>Available `module_option` values are `dalog`, `malog`, `dftbl`, `oftbl`, `lsom`, `lsof`, and `heap`.<br>pmem_device values can be `dalog` or `dftbl`.<br>mount_point values can be `malog`, `heap`, `lsom`, or `oftbl`.<br>absolute_file_path value can be `lsof`. |
| `trace` pmem_device trace_option_file                                          | Use this command to enabling tracing for `omsdaemon` and `omsfscmds`.                                                                                                                                                                                                                                                                      |
| `daemon` daemon_action                                                         | Use this command to set the OMS daemon trace level.<br>`exit` will shutdown the daemon.<br>`trace lvl `sets the daemon trace `lvl` to low, medium, or high.                                                                                                                                                                                |
| `exit`                                                                         | Exit the `omsfscmds` command prompt.                                                                                                                                                                                                                                                                                                       |

**Related Topics**

- [Oracle Memory Speed CLI Commands](oms-cli-commands.md)

**Parent topic:** [Deploying the Oracle Memory Speed File System](deploying_oms.md)
