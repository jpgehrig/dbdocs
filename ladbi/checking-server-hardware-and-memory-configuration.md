## Checking Server Hardware and Memory Configuration

Use this procedure to gather information about your server configuration.

1.  Use the following command to determine physical RAM size on the server:
        # grep MemTotal /proc/meminfo

    If the size of the physical RAM installed in the system is less than the required size, then you must install more memory before continuing.
2.  Determine the size of the configured swap space:
        # grep SwapTotal /proc/meminfo

    If necessary, see your operating system documentation for information about how to configure additional swap space.
3.  Determine the amount of space available in the `/tmp` directory:
        # df -h /tmp

    If the free space available in the `/tmp` directory is less than what is required, then complete one of the following steps:

    - Delete unused files from the `/tmp` directory to meet the disk space requirement.

      **Note:**

      If you perform this step after installing Oracle software, then do not remove `/tmp/.oracle` or `/var/tmp/.oracle` directories or their files.

    - When you set the Oracle user's environment, also set the `TMP` and `TMPDIR` environment variables to the directory you want to use instead of `/tmp`.
4.  Determine the amount of free RAM and disk swap space on the system:
        # free
5.  Determine if the system architecture can run the software:
        # uname -m

    Verify that the processor architecture matches the Oracle software release to install. For example, you should see the following for a x86-64 bit system:
        x86_64

    If you do not see the expected output, then you cannot install the software on this system.
6.  Verify that shared memory (`/dev/shm`) is mounted properly with sufficient size:
        df -h /dev/shm

    The `df-h` command displays the filesystem on which `/dev/shm` is mounted, and also displays in GB the total size and free size of shared memory.

**Related Topics**

- [Server Hardware Checklist for Oracle Database Installation](server-hardware-checklist-for-oracle-database-installation.md)

**Parent topic:** [Checking and Configuring the Server for Oracle Database](checking-and-configuring-server-hardware-for-oracle-database.md)
