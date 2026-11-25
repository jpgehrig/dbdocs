## Disk Space Requirements

The disk space requirements for installing Oracle Restart are:

- At least 7 GB of disk space

- The amount of disk space available in the `%TEMP%` directory is equivalent to the total amount of free disk space, minus what is required to install Oracle Restart

If the free disk space is less than 1 GB in the `%TEMP%` directory, then:

- Delete unnecessary files from the `%TEMP%` directory to meet the disk space requirement.

- Set `TEMP` environment variable. Go to System Properties, then Environment Variables, "`TEMP=C:\Temp\`."

**Parent topic:** [Requirements for an Oracle Restart Installation](requirements-for-an-oracle-grid-infrastructure-for-a-standalone-server-oracle-restart-installation.md)
