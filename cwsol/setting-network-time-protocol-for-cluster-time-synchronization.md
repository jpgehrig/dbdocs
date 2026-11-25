Oracle Clusterware requires the same time zone environment variable setting on all cluster nodes.

During installation, the installation process picks up the time zone environment variable setting of the Grid installation owner on the node where OUI runs, and uses that time zone value on all nodes as the default TZ environment variable setting for all processes managed by Oracle Clusterware. The time zone default is used for databases, Oracle ASM, and any other managed processes. You have two options for cluster time synchronization:

- An operating system configured network time protocol (NTP)

- Oracle Cluster Time Synchronization Service

Oracle Cluster Time Synchronization Service is designed for organizations whose cluster servers are unable to access NTP services. If you use NTP, then the Oracle Cluster Time Synchronization daemon (ctssd) starts up in observer mode. If you do not have NTP daemons, then ctssd starts up in active mode and synchronizes time among cluster members without contacting an external time server.

On Oracle Solaris Cluster systems, Oracle Solaris Cluster software supplies a template file called `ntp.conf.cluster` (see` /etc/inet/ntp.conf.cluster` on an installed cluster host) that establishes a peer relationship between all cluster hosts. One host is designated as the preferred host. Hosts are identified by their private host names. Time synchronization occurs across the cluster interconnect. If Oracle Clusterware detects either that the Oracle Solaris Cluster NTP or an outside NTP server is set default NTP server in the system in the `/etc/inet/ntp.conf` or the `/etc/inet/ntp.conf.cluster` files, then CTSS is set to the observer mode. See the Oracle Solaris 11 Information Library for more information about configuring NTP for Oracle Solaris.

**Note:**

Before starting the installation of Oracle Grid Infrastructure, Oracle recommends that you ensure the clocks on all nodes are set to the same time.

If you have NTP daemons on your server but you cannot configure them to synchronize time with a time server, and you want to use Cluster Time Synchronization Service to provide synchronization service in the cluster, then deactivate and deinstall the NTP.

To disable the NTP service, run the following command as the root user:

    # /usr/sbin/svcadm disable ntp

When the installer finds that the NTP protocol is not active, the Cluster Time Synchronization Service is installed in active mode and synchronizes the time across the nodes. If NTP is found configured, then the Cluster Time Synchronization Service is started in observer mode, and no active time synchronization is performed by Oracle Clusterware within the cluster.

To confirm that `ctssd` is active after installation, enter the following command as the Grid installation owner:

    $ crsctl check ctss

If you are using NTP, and you prefer to continue using it instead of Cluster Time Synchronization Service, then you need to modify the NTP configuration. Restart the network time protocol daemon after you complete this task.

You can modify the NTP configuration as in the following example on Oracle Solaris 11 and later versions:

Run the following command as `root` user:

    # /usr/sbin/svccfg -s svc:/network/ntp:default setprop config/slew_always = true

Then, restart the NTP service:

    # /usr/sbin/svcadm refresh svc:/network/ntp:default

To enable NTP after it has been disabled, enter the following command:

    # /usr/sbin/svcadm enable ntp

**Related Topics**

- [Oracle Solaris Cluster 3.3 Documentation](http://www.oracle.com/technetwork/documentation/solaris-cluster-33-192999.html)
- [Oracle Solaris Cluster 4 Documentation](http://www.oracle.com/technetwork/documentation/solaris-cluster-40-1405284.html)

**Parent topic:** [Configuring Oracle Solaris Operating Systems for Oracle Grid Infrastructure](configuring-operating-systems-for-oracle-grid-infrastructure-on-oracle-solaris.md)
