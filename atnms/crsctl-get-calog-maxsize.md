To store Oracle Clusterware-managed resource activity information, query the maximum space allotted to the cluster resource activity log.

### Syntax

    crsctl get calog maxsize

### Parameters

The `crsctl get calog maxsize` command has no parameters.

### Example

The following example returns the maximum space allotted to the cluster resource activity log to store activities:

    $ crsctl get calog maxsize

    CRS-6760: The maximum size of the Oracle cluster activity log is 1024 MB.

**Parent topic:** [Managing the Cluster Resource Activity Log](cluster-resource-activity-log.md)
