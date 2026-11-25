## Enabling the Name Service Cache Daemon

To allow Oracle Clusterware to better tolerate network failures with NAS devices or NFS mounts, enable the Name Service Cache Daemon (`nscd`).

To check to see if `nscd` is set to load when the system is restarted, enter the command `chkconfig --list nscd`. For example:

    # chkconfig --list nscd
    nscd                      0:off  1:off  2:off  3:on   4:off  5:off   6:off

`nscd` is turned on for run level 3, and turned off for run level 5. The `nscd` should be turned on for both run level 3 and run level 5.

To change the configuration to ensure that `nscd` is on for both run level 3 and run level 5, enter the following command as `root`:

    # chkconfig --level 35 nscd on

To start up `nscd` in the current session, enter the command as `root`:

    # service nscd start

To restart `nscd` with the new setting, enter the following command as `root`:

    # service nscd restart

For Oracle Linux 7, verify that `nscd` is enabled as follows:

    systemctl --all |grep nscd
    nscd.service loaded active running Name Service Cache Daemon

**Parent topic:** [Configuring Operating Systems for Oracle Grid Infrastructure on Linux](configuring-operating-systems-for-oracle-grid-infrastructure-on-linux.md)
