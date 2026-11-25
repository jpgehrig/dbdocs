Use either the Oracle Cluster Time Synchronization or network time protocol (NTP) option for time synchronization.

Oracle Clusterware requires the same time zone environment variable setting on all cluster nodes. During installation, the installation process picks up the time zone (TZ) environment variable setting of the Grid installation owner on the node where Oracle Universal Installer (OUI) runs, and uses that time zone value on all nodes as the default TZ environment variable setting for all processes managed by Oracle Clusterware. The time zone default is used for databases, Oracle ASM, and any other managed processes. You have two options for time synchronization:

- An operating system configured network time protocol (NTP) such as `chronyd` or `ntpd`

- Oracle Cluster Time Synchronization Service

Oracle Cluster Time Synchronization Service is designed for organizations whose cluster servers are unable to access NTP services. If you use NTP, then the Oracle Cluster Time Synchronization daemon (ctssd) starts up in observer mode. If you do not have NTP daemons, then ctssd starts up in active mode and synchronizes time among cluster members without contacting an external time server.

**Note:**

Before starting the installation of Oracle Grid Infrastructure, Oracle recommends that you ensure the clocks on all nodes are set to the same time.

If you have NTP daemons on your server but you cannot configure them to synchronize time with a time server, and you want to use Cluster Time Synchronization Service to provide synchronization service in the cluster, then deactivate and deinstall the NTP.

### Deactivating the ntpd Service

To deactivate the NTP service, run the following command as `root`:

    # stopsrc -s xntpd

When the installer finds that the NTP protocol is not active, the Cluster Time Synchronization Service is installed in active mode and synchronizes the time across the nodes. If NTP is found configured, then the Cluster Time Synchronization Service is started in observer mode, and no active time synchronization is performed by Oracle Clusterware within the cluster.

### Confirming Oracle Cluster Time Synchronization Service After Installation

To confirm that `ctssd` is active after installation, enter the following command as the Grid installation owner:

    $ crsctl stat resource ora.ctssd -t -init

**Parent topic:** [Configuring Operating Systems for Oracle Grid Infrastructure on IBM AIX on POWER Systems (64–Bit)](configuring-operating-systems-for-oracle-grid-infrastructure-on-ibm-aix-on-power-systems.md)
