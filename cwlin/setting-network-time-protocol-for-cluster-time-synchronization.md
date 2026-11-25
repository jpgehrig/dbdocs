## Setting Network Time Protocol for Cluster Time Synchronization

Use either the Oracle Cluster Time Synchronization or network time protocol (NTP) option for time synchronization.

**Note:**

Cluster Time Synchronization Service (CTSS) is deprecated in Oracle Database 19c. 

To synchronize time between cluster member nodes, use either an operating system configured network time protocol such as `ntp` or `chrony`, or Microsoft Windows Time service. To verify that you have network time synchronization configured, you can use the `cluvfy comp clocksync -n all` command.

Oracle Clusterware requires the same time zone environment variable setting on all cluster nodes. During installation, the installation process picks up the time zone (TZ) environment variable setting of the Grid installation owner on the node where Oracle Universal Installer (OUI) runs, and uses that time zone value on all nodes as the default TZ environment variable setting for all processes managed by Oracle Clusterware. The time zone default is used for databases, Oracle ASM, and any other managed processes. You have two options for time synchronization:

- An operating system configured network time protocol (NTP) such as `chronyd` or `ntpd`

- Oracle Cluster Time Synchronization Service

Oracle Cluster Time Synchronization Service is designed for organizations whose cluster servers are unable to access NTP services. If you use NTP, then the Oracle Cluster Time Synchronization daemon (ctssd) starts up in observer mode. If you do not have NTP daemons, then `ctssd` starts up in active mode and synchronizes time among cluster members without contacting an external time server.

**Note:**

- Before starting the installation of Oracle Grid Infrastructure, Oracle recommends that you ensure the clocks on all nodes are set to the same time.

- By default, the NTP service available on Oracle Linux 7 and Red Hat Linux 7 is `chronyd`.

If you have NTP daemons on your server but you cannot configure them to synchronize time with a time server, and you want to use Cluster Time Synchronization Service to provide synchronization service in the cluster, then deactivate and deinstall the NTP.

When the installer finds that the NTP protocol is not active, the Cluster Time Synchronization Service is installed in active mode and synchronizes the time across the nodes. If NTP is found configured, then the Cluster Time Synchronization Service is started in observer mode, and no active time synchronization is performed by Oracle Clusterware within the cluster.

### Deactivating the NTP Service

To deactivate the Network Time Protocol (NTP) service, you must stop the `ntpd` and `chronyd` services, and disable them from the initialization sequences.

Complete these steps on Oracle Linux 7 and Red Hat Linux 7:

1.  Run the following commands as the `root` user to stop the `ntpd` service:

        # systemctl stop ntpd
        # systemctl disable ntpd

2.  Rename the NTP-related configuration files in the `/etc` directory.

3.  Run the following commands as the `root` user to stop the `chronyd` service:

        # systemctl stop chronyd
        # systemctl disable chronyd

4.  Remove the `chronyd` service configuration file.

### Confirming Oracle Cluster Time Synchronization Service After Installation

To confirm that `ctssd` is active after installation, enter the following command as the Grid installation owner:

    $ crsctl check ctss

**Parent topic:** [Configuring Operating Systems for Oracle Grid Infrastructure on Linux](configuring-operating-systems-for-oracle-grid-infrastructure-on-linux.md)
