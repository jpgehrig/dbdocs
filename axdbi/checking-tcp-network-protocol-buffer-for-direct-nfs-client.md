Check your TCP network buffer size to ensure that it is adequate for the speed of your servers.

By default, the network buffer size is set to 1 MB for TCP, and 2 MB for UDP. The TCP buffer size can set a limit on file transfers, which can negatively affect performance for Direct NFS Client users.

To check the current TCP buffer size:

    # /usr/sbin/no -o sb_max

Oracle recommends that you set the value based on the link speed of your servers. For example:

    # /usr/sbin/no -p -o sb_max=524288

**Parent topic:** [Configuring File System Storage for Oracle Database](configuring-file-system-storage-for-oracle-database.md)
