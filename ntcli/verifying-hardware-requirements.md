## Verifying Hardware Requirements

Use this procedure to verify your server configuration requirements.

To ensure that the system meets these requirements, follow these steps:

1.  Determine the physical RAM size.
    For example, on a computer running Windows Server 2012 R2, click System and Security, then click System.

    If the size of the physical RAM installed in the system is less than the required size, then you must install more memory before continuing.
2.  Determine the size of the configured virtual memory (also known as paging file size).
    For example, on a computer running Windows Server 2012 R2, click System and Security, then click System, click Advanced System Settings, click the Advanced tab on System Properties page, and then click Settings in the Performance section. Then select the Advanced tab on Performance Options page.

    The virtual memory is listed in the Virtual Memory section.

    If necessary, see your operating system documentation for information about how to configure additional virtual memory.
3.  Determine the amount of free disk space on the system.
    For example, on a computer running Windows Server 2012 R2, right-click My Computer and click Open.
4.  Determine the amount of disk space available in the `temp` directory. This is equivalent to the total amount of free disk space, minus what is required for the Oracle software to be installed.
    On Windows x64, if there is less than 130 MB of disk space available in the `temp` directory, then delete all unnecessary files. If the temp disk space is still less than 130 MB, then set the `TEMP` or `TMP` environment variable to point to a different hard drive location.

    For example, to change the environment variables on a computer running Windows Server 2012 R2, click System and Security, then click System, click Advanced System Settings, click the Advanced tab on System Properties page, and then click Environment Variables.

**Parent topic:** [Oracle Database Client Minimum Hardware Requirements](oracle-database-client-minimum-hardware-requirements.md)
