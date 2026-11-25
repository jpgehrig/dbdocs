Use this procedure to gather information about your server configuration.

1.  To determine physical RAM size on the server:
        # /usr/sbin/lsattr -E -l sys0 -a realmem
2.  To determine the available RAM and swap space:
        # /usr/sbin/lsps -s

    Oracle recommends that you take multiple values for the available RAM and swap space before finalizing a value. This is because the available RAM and swap space keep changing depending on the user interactions with the computer.
3.  To determine the size of the configured swap space:
        # /usr/sbin/lsps -a

    If necessary, see your operating system documentation for information about how to configure additional swap space.
4.  Determine the amount of space available in the `/tmp` directory:
        # df -m /tmp

    If the free space available in the `/tmp` directory is less than what is required, then complete one of the following steps:

    - Delete unnecessary files from the `/tmp` directory to meet the disk space requirement.

    - When you set the Oracle user's environment, also set the TMP and TMPDIR environment variables to the directory you want to use instead of `/tmp`.

    - Extend the file system that contains the `/tmp` directory.
5.  Determine the amount of free disk space on the system:
        # df -g
        # df -m
6.  Determine if the system architecture can run the software:
        # /usr/bin/getconf HARDWARE_BITMODE

    The expected output of this command is 64. If you do not see the expected output, then you cannot install the software on this system.
    To determine if the system is started in 64-bit mode:
        # /usr/sbin/bootinfo -K

    The result of this command must be 64, indicating that the 64-bit kernel is enabled.

    Verify that the processor architecture matches the Oracle software release to install. If you do not see the expected output, then you cannot install the software on this system.

    **Note:**

    For AIX Based Systems, Oracle Database supports 64-bit kernel and does not provide support for 32-bit kernel applications.
7.   To determine the run level:
        /usr/bin/who -r

**Parent topic:** [Checking and Configuring Server Hardware for Oracle Grid Infrastructure](checking-configure-server-hardware-grid-infrastructure.md)
