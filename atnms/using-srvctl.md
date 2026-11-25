SRVCTL commands are the tools that offer total control on managing the life cycle of Oracle Cluster Health Advisor as a highly available service.

Use SRVCTL commands to the check the status and configuration of Oracle Cluster Health Advisor service on any active hub or leaf nodes of the Oracle RAC cluster.

**Note:**

A target is monitored only if it is running and the Oracle Cluster Health Advisor service is also running on the host node where the target exists.

1.  To check the status of Oracle Cluster Health Advisor service on all nodes in the Oracle RAC cluster:
        srvctl status cha [-help]

    For example:
        # srvctl status cha
        Cluster Health Advisor is running on nodes racNode1, racNode2.
        Cluster Health Advisor is not running on nodes racNode3, racNode4.
2.  To check if Oracle Cluster Health Advisor service is enabled or disabled on all nodes in the Oracle RAC cluster:
        srvctl config cha [-help]

    For example:
        # srvctl config cha
        Cluster Health Advisor is enabled on nodes racNode1, racNode2.
        Cluster Health Advisor is not enabled on nodes racNode3, racNode4.

**Parent topic:** [Proactively Detecting and Diagnosing Performance Issues for Oracle RAC](purpose-cluster-health-advisor.md)
