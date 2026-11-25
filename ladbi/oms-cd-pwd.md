## cd and pwd Command Reference

Use the current directory `cd` command to set the current working Oracle Memory Speed (OMS) mount point. Use the present working directory `pwd` command to display the current OMS mount point set by the previous `cd` command.

### Syntax

    cd dirpath
    pwd

### Usage Notes

`cd` allows you to use other commands such as `ls` without an explicit argument.

### Example

    OMS> pwd
    pwd: /
    OMS> cd /oracle/omsfs_1
    cd /oracle/omsfs_1 succeeded.
    OMS> pwd
    pwd: /oracle/omsfs_1
    OMS> ls
    OMS:ls: Files in /oracle/omsfs_1/:
    OMS:ls: [blobno] blobname
    OMS:ls cb: [4] /control01.ctl
    OMS:ls cb: [5] /df1.dbf
    OMS:ls cb: [6] /tempfile
    OMS:lst: Total bytes allocated: 212640K
    OMS>

**Parent topic:** [Oracle Memory Speed CLI Commands](oms-cli-commands.md)
