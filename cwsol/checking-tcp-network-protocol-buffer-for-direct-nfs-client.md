Check your TCP network buffer size to ensure that it is adequate for the speed of your servers.

By default, the network buffer size is set to 1 MB for TCP, and 2 MB for UDP. The TCP buffer size can set a limit on file transfers, which can negatively affect performance for Direct NFS Client users.

To check the current TCP buffer size on Oracle Solaris 11:

    # ipadm show-prop -p max_buf tcp

Oracle recommends that you set the value based on the link speed of your servers. For example:

On Oracle Solaris 11:

    # ipadm set-prop -p max_buf=1048576 tcp

Additionally, check your TCP send window size and TCP receive window size to ensure that they are adequate for the speed of your servers.

To check the current TCP send window size and TCP receive window size on Oracle Solaris 11:

    # ipadm show-prop -p send_buf tcp
    # ipadm show-prop -p recv_buf tcp

Oracle recommends that you set the value based on the link speed of your servers. For example:

On Oracle Solaris 11:

    # ipadm set-prop -p send_buf=1056768 tcp
    # ipadm set-prop -p recv_buf=1056768 tcp

**Parent topic:** [Configuring File System Storage for Oracle Database](configuring-file-system-storage-for-oracle-database.md)
