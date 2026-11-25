## Checking the Available TEMP Disk Space

The amount of disk space available in the TEMP directory is equivalent to the total amount of free disk space, minus what is needed to install the Oracle software.

Log in as or switch to the user that will be performing the installation. See "[About the Oracle Installation User](about-the-oracle-installation-user.md)" for more information.

**Note:**

The temporary directory must reside in the same directory path on each node in the cluster.

You must have 1 GB of disk space available in the `TEMP` directory. If you do not have sufficient space, then first delete all unnecessary files. If the temporary disk space is still less than the required amount, then increase the partition size of the disk or set the `TEMP` environment variable to point to a different hard drive. Ensure the environment variables `TEMP` and `TMP` both point to the location of the `TEMP` directory, for example:

    TEMP=C:\WINDOWS\TEMP
    TMP=C:\WINDOWS\TEMP

1.  From the Control Panel, select System.
2.  Select Advanced System Settings.
3.  In the System Properties windows, select the Advanced tab, then click Environment Variables.
4.  Modify the value of the `TEMP` environment variable in the user variables list.

**Parent topic:** [Checking Server Hardware and Memory Configuration](checking-server-hardware-and-memory-configuration.md)
