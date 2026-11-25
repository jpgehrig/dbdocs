## Checking Cluster Health Monitor Repository Size After Upgrading

If you are upgrading Oracle Grid Infrastructure from a prior release using IPD/OS to the current release, then review the Cluster Health Monitor repository size (the CHM repository).

1.  Review your CHM repository needs, and determine if you need to increase the repository size to maintain a larger CHM repository.
    **Note:**

    Your previous IPD/OS repository is deleted when you install Oracle Grid Infrastructure.
    By default, the CHM repository size is a minimum of either 1GB or 3600 seconds (1 hour), regardless of the size of the cluster.
2.  To enlarge the CHM repository, use the following command syntax, where RETENTION_TIME is the size of CHM repository in number of seconds:
        oclumon manage -repos changeretentiontime RETENTION_TIME

    For example, to set the repository size to four hours:

        oclumon manage -repos changeretentiontime 14400

    The value for RETENTION_TIME must be more than 3600 (one hour) and less than 259200 (three days). If you enlarge the CHM repository size, then you must ensure that there is local space available for the repository size you select on each node of the cluster. If you do not have sufficient space available, then you can move the repository to shared storage.

**Parent topic:** [Upgrading Oracle Grid Infrastructure](upgrading-oracle-grid-infrastructure.md)
