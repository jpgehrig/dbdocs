Use this procedure to gather information about your server configuration.

1.  To determine the physical RAM size on the server:
        # /usr/contrib/bin/machinfo  | grep -i Memory
2.  To determine the size of the configured swap space:
        # /usr/sbin/swapinfo -a

    If necessary, see your operating system documentation for information about how to configure additional swap space.
3.  To determine the amount of space available in the `/tmp` directory:
        # bdf /tmp

    If the free space available in the /tmp directory is less than what is required, then complete one of the following steps:

    - Delete unnecessary files from the /tmp directory to meet the disk space requirement.

    - When you set the Oracle user's environment, also set the TMP and TMPDIR environment variables to the directory you want to use instead of `/tmp`.
4.  To determine the amount of free disk space on the system:
        # bdf
5.  To determine if the system architecture can run the software:
        # uname -m

    Verify that the processor architecture matches the Oracle software release to install. For example, you should see the following for a x86-64 bit system:
        ia64 (itanium)

    If you do not see the expected output, then you cannot install the software on this system.
6.  To view the shared memory kernel parameters (shmmni, shmseg, and shmmax) and determine if any changes are necessary for your system:
        # kctune -v shmmni
        # kctune -v shmseg
        # kctune -v shmmax

    Use the `kctune shmmni=1024` command to set the memory kernel parameter to the required value.

**Parent topic:** [Checking and Configuring Server Hardware for Oracle Database Client](checking-and-configuring-server-hardware-for-oracle-database-client.md)
