## Configuring Cluster Time Synchronization Service

Cluster Time Synchronization Service (CTSS) is provided by Oracle to synchronize the time across the nodes in your cluster.

When OUI discovers that neither the Windows Time or NTP services are active, the Cluster Time Synchronization Service is installed in active mode and synchronizes the time across the nodes. If the Windows Time service or NTP service is found on the server, then the Cluster Time Synchronization Service is started in observer mode, and no active time synchronization is performed by the Cluster Time Synchronization Service within the cluster.

To use Cluster Time Synchronization Service to provide synchronization service in the cluster, disable the Windows Time service and stop the NTP service. If you have an NTP service on your server but you cannot use the service to synchronize time with a time server, then you must deactivate and deinstall the NTP to use Cluster Time Synchronization Service.

- To confirm that the Cluster Time Synchronization Service is active after installation, enter the following command as the Oracle Grid Infrastructure installation owner:
      crsctl check ctss

**Parent topic:** [Configuring Time Synchronization for the Cluster](configuring-time-synchronization-for-the-cluster.md)
