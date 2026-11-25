## Checking TCP Network Protocol Buffer for Direct NFS Client

Check your TCP network buffer size to ensure that it is adequate for the speed of your servers.

By default, the network buffer size is set to 1 MB for TCP, and 2 MB for UDP. The TCP buffer size can set a limit on file transfers, which can negatively affect performance for Direct NFS Client users.

To check the current TCP buffer size, enter the following command:

    # sysctl -a |grep -e net.ipv4.tcp_[rw]mem

The output of this command is similar to the following:

    net.ipv4.tcp_rmem = 4096        87380   1056768
    net.ipv4.tcp_wmem = 4096        16384   1056768

Oracle recommends that you set the value based on the link speed of your servers. For example, perform the following steps:

1.  As `root`, use a text editor to open `/etc/sysctl.conf`, and add or change the following:

        net.ipv4.tcp_rmem = 4096        87380   4194304
        net.ipv4.tcp_wmem = 4096        16384   4194304

2.  Apply your changes by running the following command:

        # sysctl -p

3.  Restart the network:

        # /etc/rc.d/init.d/network restart

**Parent topic:** [Configuring File System Storage for Oracle Database](configuring-file-system-storage-for-oracle-grid-infrastructure.md)
