## Using Response Files

Review this information to use response files.

Use the following general steps to install and configure Oracle products using the installer in silent or response file mode:

1.  If you plan to use Oracle Automatic Storage Management and configure new disks, then you must perform the following steps:

    1.  Create partitions for DAS or SAN disks.

    2.  Manually configure the disks using the `asmtoolg` or `asmtool` utility.

2.  Customize or create a response file for the installation settings that you need.

    You can create the response file by using one of the following methods:

    - Modify one of the sample response files that is provided with the installation.

    - Run Oracle Universal Installer at a command prompt and save the inputs by selecting the Save Response File option.

3.  Run Oracle Universal Installer from a command prompt, specifying the response file, using either silent or response file mode.

    **Note:**

    Windows requires Administrator privileges at the command prompt.

**Parent topic:** [Installing and Configuring Oracle Database Using Response Files](advance.md)
