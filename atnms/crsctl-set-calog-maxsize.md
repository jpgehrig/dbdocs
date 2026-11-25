Configure the maximum amount of space allotted to store Oracle Clusterware-managed resource activity information.

### Syntax

    crsctl set calog maxsize maximum_size

### Usage Notes

Specify a value, in MB, for the maximum size of the storage space that you want to allot to the cluster resource activity log.

**Note:**

If you reduce the amount of storage space, then the contents of the storage are lost.

### Example

The following example sets maximum amount of space, to store Oracle Clusterware-managed resource activity information, to 1024 MB:

    $ crsctl set calog maxsize 1024

**Parent topic:** [Managing the Cluster Resource Activity Log](cluster-resource-activity-log.md)
