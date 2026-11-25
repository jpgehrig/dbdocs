## Understanding Network Time Requirements

Oracle Clusterware 19c is automatically configured with Cluster Time Synchronization Service (CTSS).

CTSS provides automatic synchronization of the time settings on all cluster nodes. CTSS uses the optimal synchronization strategy for the type of cluster you deploy.

If you have an existing cluster synchronization service, such as network time protocol (NTP) or Windows Time Service, then CTSS starts in an observer mode. Otherwise, CTSS starts in an active mode to ensure that time is synchronized between cluster nodes. CTSS will not cause compatibility issues.

The CTSS module is installed as a part of Oracle Grid Infrastructure installation. CTSS daemons are started by the Oracle High Availability Services daemon (`ohasd`), and do not require a command-line interface.

**Parent topic:** [Configuring Time Synchronization for the Cluster](configuring-time-synchronization-for-the-cluster.md)
