## About Cluster Time Synchronization

For the Microsoft Windows operating system, there are three different methods you can use to synchronize the time between the nodes of your cluster.

During installation, the installation process picks up the time zone environment variable setting of the Oracle Installation user for Oracle Grid Infrastructure on the node where OUI runs. Then the installation process uses that time zone value on all nodes as the default TZ environment variable setting for all processes managed by Oracle Clusterware. The time zone default is used for databases, Oracle ASM, and any other managed processes.

You have three options for time synchronization between cluster nodes:

- Windows Time service

- An operating system configured network time protocol (NTP)

- Oracle Cluster Time Synchronization Service

Oracle Cluster Time Synchronization Service is designed for organizations whose cluster servers are unable to access NTP services. If you use NTP, then the Oracle Cluster Time Synchronization daemon (ctssd) starts in observer mode. If neither NTP or the Windows Time service is found, then ctssd starts in active mode and synchronizes time among cluster members without contacting an external time server.

**Note:**

- Before starting the installation of Oracle Grid Infrastructure, Oracle recommends that you ensure the clocks on all nodes are set to the same time.

- The IP address for an NTP server can be an IPv6 address.

**Parent topic:** [Configuring Time Synchronization for the Cluster](configuring-time-synchronization-for-the-cluster.md)
