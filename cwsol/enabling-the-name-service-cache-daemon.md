To allow Oracle Clusterware to better tolerate network failures with NAS devices or NFS mounts, enable the Name Service Cache Daemon (`nscd`).

Starting with Oracle Solaris 11, when you enable nscd, nscd performs all name service lookups. Before this release, nscd cached a small subset of lookups. By default, nscd is started during system startup in runlevel 3, which is a multiuser state with NFS resources shared. To check to see if nscd is running, enter the following Service Management Facility (SMF) command:

    # svcs name-service-cache
    STATE          STIME    FMRI
    online         Oct_15   svc:/network/nfs/status:default
    online         Oct_30   svc:/system/name-service-cache:default

For Solaris 11, the SMF service `svc:/system/name-service/cache` contains the configuration information for nscd. The file `/etc/nscd.conf` is deprecated. Note that `svc:/system/name-service-cache` still exists on Solaris 11 systems but it is not connected.

If the nscd service is not online, you can enable it using the following command:

    # svcadm enable svc:/system/name-service-cache:default

**Parent topic:** [Configuring Oracle Solaris Operating Systems for Oracle Grid Infrastructure](configuring-operating-systems-for-oracle-grid-infrastructure-on-oracle-solaris.md)
