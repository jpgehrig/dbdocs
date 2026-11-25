## ls and lls Command Reference

Use `ls` to list files in the Oracle Memory Speed (OMS) mount point, and `lls` to list files in the OMS mount point with additional information for each file.

### Syntax

    ls mount_path
    lls mount_path

### Usage Notes

`lls` reports an accurate accounting of the total bytes allocated for the files. However, `ls` may not always report an accurate accounting of the total bytes allocated for the files.

### Example

    ls /oracle/omsfs_1
    OMS:ls: dirpath fixed to /oracle/omsfs_1/
    OMS:ls: Files in /oracle/omsfs_1/:
    OMS:ls: [blobno] blobname
    OMS:ls cb: [4] /control01.ctl
    OMS:ls cb: [5] /df1.dbf
    OMS:ls cb: [6] /tempfile
    OMS:lst: Total bytes allocated: 212640K
    OMS> lls /oracle/omsfs_1
    OMS:ls: dirpath fixed to /oracle/omsfs_1/
    OMS:lls: Files in /oracle/omsfs_1/:
    OMS:lls cb: : Blob Name : /control01.ctl
    OMS:lls cb: : Blob Num : 4
    OMS:lls cb: : Size : 8011776
    OMS:lls cb: : BlockSize : 4096
    OMS:lls cb: : DB ID: : 0
    OMS:lls cb: : Dir ID: : 0
    OMS:lls cb: : Blob Name : /df1.dbf
    OMS:lls cb: : Blob Num : 5
    OMS:lls cb: : Size : 104865792
    OMS:lls cb: : BlockSize : 4096
    OMS:lls cb: : DB ID: : 0
    OMS:lls cb: : Dir ID: : 0
    OMS:lls cb: : Blob Name : /tempfile
    OMS:lls cb: : Blob Num : 6
    OMS:lls cb: : Size : 104865792
    OMS:lls cb: : BlockSize : 4096
    OMS:lls cb: : DB ID: : 0
    OMS:lls cb: : Dir ID: : 0
    OMS:lst: Total bytes allocated: 212640K
    OMS>

**Parent topic:** [Oracle Memory Speed CLI Commands](oms-cli-commands.md)
