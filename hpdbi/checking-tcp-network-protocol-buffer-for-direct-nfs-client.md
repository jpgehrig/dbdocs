Check your TCP network buffer size to ensure that it is adequate for the speed of your servers.

By default, the network buffer size is set to 1 MB for TCP, and 2 MB for UDP. The TCP buffer size can set a limit on file transfers, which can negatively affect performance for Direct NFS Client users.

To check the current TCP buffer size:

    bash-4.0$ ndd -get /dev/tcp tcp_xmit_hiwater_max
    bash-4.0$ ndd -get /dev/tcp tcp_recv_hiwater_max

Oracle recommends that you set the value based on the link speed of your servers. For example:

    bash-4.0# ndd -set /dev/tcp tcp_xmit_hiwater_max 10485760
    bash-4.0# ndd -set /dev/tcp tcp_recv_hiwater_max 10485760

**Parent topic:** [Configuring File System Storage for Oracle Database](configuring-file-system-storage-for-oracle-database.md)
