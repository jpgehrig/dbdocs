Oracle Clusterware stores logs about resource failures in the cluster resource activity log, which is located in the Grid Infrastructure Management Repository.

Failures can occur as a result of a problem with a resource, a hosting node, or the network.

The cluster resource activity log provides precise and specific information about a resource failure, separate from diagnostic logs. The cluster resource activity log also provides a unified view of the cause of resource failure.

Use the following commands to manage and view the contents of the cluster resource activity log:

- [crsctl query calog](crsctl-query-calog.md)
  Query the cluster resource activity logs matching specific criteria.
- [crsctl get calog maxsize](crsctl-get-calog-maxsize.md)
  To store Oracle Clusterware-managed resource activity information, query the maximum space allotted to the cluster resource activity log.
- [crsctl get calog retentiontime](crsctl-get-calog-retentiontime.md)
  Query the retention time of the cluster resource activity log.
- [crsctl set calog maxsize](crsctl-set-calog-maxsize.md)
  Configure the maximum amount of space allotted to store Oracle Clusterware-managed resource activity information.
- [crsctl set calog retentiontime](crsctl-set-calog-retentiontime.md)
  Configure the retention time of the cluster resource activity log.

**Parent topic:** [Appendixes](appendixes.md)
