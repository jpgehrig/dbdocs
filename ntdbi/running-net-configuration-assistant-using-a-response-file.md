## Running Net Configuration Assistant Using a Response File

When you run Net Configuration Assistant with a response file, you run it in a silent mode.

This lets you configure and start an Oracle Net listener on the system, configure naming methods, and configure Oracle Net service names. To run NetCA in a silent mode, use the `netca.rsp` response file in the` ORACLE_BASE\ORACLE_HOME``\assistants\netca` directory, and the `response` directory in the `database\response` directory on the DVD.

**Note:**

If you copied the software to a hard disk, the response files are located in the `stage_area``\database\response` directory.

On Windows, you must open command prompt with the Administrator privileges.

To create a Net Configuration Assistant response file:

1.  Copy the `netca.rsp` response file template from the response file directory to a directory on your system.

    The `netca.rsp` is located in the `database\response` directory on the Oracle Database installation media.

2.  Open the response file in a text editor.

3.  Edit the file, following the instructions in the file.

    Net Configuration Assistant fails if you do not correctly configure the `netca.rsp` response file.

To run Net Configuration Assistant using the response file you just created, run Net Configuration Assistant in silent mode as follows, replacing `local_dir` with the directory where you placed your version of the `netca.rsp` response file:

    C:\ORACLE_HOME\bin> netca /silent /responsefile local_dir\netca.rsp

For example:

    C:\ORACLE_HOME\bin> netca /silent /responsefile
    C:\oracle_response_files\mynetca.rsp

**Parent topic:** [Installing and Configuring Oracle Database Using Response Files](advance.md)
