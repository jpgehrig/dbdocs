## rm Command Reference

Use the `rm` command to delete a file from an Oracle Memory Speed (OMS) mount point.

### Syntax

    rm filepath

### Usage Notes

The file path must be an absolute path to an OMS file. `rm` is enabled only when the Oracle instance is down. If you delete critical files, then it may cause the instance start-up to fail.

**Caution:**

You cannot restore the files you delete.

**Parent topic:** [Oracle Memory Speed CLI Commands](oms-cli-commands.md)
