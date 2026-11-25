## Configuring Network Time Protocol

The Network Time Protocol (NTP) is a client/server application.

Each server must have NTP client software installed and configured to synchronize its clock to the network time server. The Windows Time service is not an exact implementation of the NTP, but it is based on the NTP specifications.

If you decide to use NTP instead of the Windows Time service, then, after you have installed the NTP client software on each cluster node, you must start the NTP service with the `-x` option to prevent time from being adjusted backward. Restart the network time protocol service after you complete this task:

1.  Use the registry editor to edit the value for the `ntpd` executable under `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\NTP`.
2.  Add the `-x` option to the `ImagePath` key value, behind `%INSTALLDIR%\ntpd.exe`.
3.  Restart the NTP service using the following commands:
        net stop NTP
        net start NTP

**Parent topic:** [Configuring Time Synchronization for the Cluster](configuring-time-synchronization-for-the-cluster.md)
