## Identifying All Instances On a Cluster Using the Windows Services Control Manager

You can use Windows Services Control Manager to identify all database instances and services associated with an Oracle home.

1.  Log in to a cluster node as a user with Administrator privileges.
2.  Use the Windows Services Control Manager to locate the Oracle services related to the Oracle home.
    Look for any Oracle services (their names begin with `Ora`) that access the Oracle home you are removing and have the status `Started`.
    To determine which Oracle home a service is associated with, check "Path to Executable" for a service to see the directory where the executable for the service is located.

**Parent topic:** [Identifying All Instances On a Cluster](identifying-all-instances-on-a-cluster.md)
