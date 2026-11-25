## Running Oracle Net Configuration Assistant Using Response Files

You can run Oracle Net Configuration Assistant (NETCA) in silent mode to configure and start an Oracle Net listener on the system, configure naming methods, and configure Oracle Net service names.

To run NETCA in silent mode, you must copy and edit a response file template. Oracle provides a response file template named `netca.rsp` in the `%ORACLE_HOME%\assistants\netca` directory.

To run NETCA using a response file:

1.  Copy the `netca.rsp` response file template from the response file directory to a directory on your system.
    `copy \``directory_path``\assistants\netca\netca.rsp ``local_directory`
    In this example, `directory_path` is the path of the directory where you have copied the installation binaries.
    If the software is staged on a hard drive, or has already been installed, then you can edit the file in the `response` directory located on the local disk instead.
2.  Open the response file in a text editor.
3.  Follow the instructions in the file to edit it.
    **Note:**

    NETCA fails if you do not correctly configure the response file.
4.  Log in as the Oracle Home user. Set the `%ORACLE_HOME%` environment variable to the correct Oracle home directory.
5.  Enter a command similar to the following to run NETCA in silent mode:
        C:\> Oracle_home\bin\netca -silent -responsefile X:\local_dir\netca.rsp

    In this command:

    - The `-silent` option runs NETCA in silent mode.

    - `X:\local_dir` is the full path of the directory where you copied the `netca.rsp` response file template, where X represents the drive on which the file is located, and local_dir the path on that drive.

**Related Topics**

- [Multiple Oracle Home Directories on Windows](multiple-oracle-home-directories-on-windows.md)
- [Changing the Current Setting for Oracle Home](changing-the-current-setting-for-oracle-home.md)

**Parent topic:** [Running Configuration Assistants Using Response Files](running-configuration-assistants-using-response-files.md)
