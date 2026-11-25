Use this procedure to gather information about your server configuration.

1.  Use the following command to report the number of memory pages and swap-file disk blocks that are currently unused:
        # sar -r n i

    For example:

        # sar -r 2 10

    If the size of the physical RAM installed in the system is less than the required size, then you must install more memory before continuing.
2.  Determine the swap space usage and size of the configured swap space:
        # /usr/sbin/swap -s

    If necessary, see your operating system documentation for information about how to configure additional swap space.
3.  Determine the amount of space available in the `/tmp` directory:
        # df -kh /tmp

    If the free space available in the /tmp directory is less than what is required, then complete one of the following steps:

    - Delete unnecessary files from the /tmp directory to meet the disk space requirement.

    - When you set the Oracle user's environment, also set the TMP and TMPDIR environment variables to the directory you want to use instead of `/tmp`.
4.  Determine the amount of free disk swap space on the system:
        # df -kh
5.  Determine the RAM size:
        # /usr/sbin/prtconf | grep "Memory size"
6.  Determine if the system architecture can run the software:
        # /bin/isainfo -kv

    This command displays the processor type. For example:
        64-bit sparcv9 kernel modules

        64-bit amd64 kernel modules

    If you do not see the expected output, then you cannot install the software on this system.

**Parent topic:** [Checking and Configuring Server Hardware for Oracle Grid Infrastructure](checking-and-configuring-server-hardware-for-oracle-grid-infrastructure.md)
