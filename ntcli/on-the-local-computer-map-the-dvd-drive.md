## Step 2: On the Local Computer, Map the DVD Drive

Use this procedure to map the DVD drive on the local computer.

Perform these steps on the local computer to map a remote DVD drive and to run Oracle Universal Installer from the mapped drive:

1.  Map the remote DVD drive.

    1.  Start Windows Explorer on the local computer.

    2.  From the Tools menu, select Map Network Drive to display the Map Network Drive dialog box.

    3.  Select a drive letter to use for the remote DVD drive.

    4.  In Folder, enter the location of the remote DVD drive using the following format:

            \\remote_hostname\share_name

        where:

        - `remote_hostname` is the name of the remote computer with the DVD drive.

        - `share_name` is the share name that you use when you map the DVD drive on the local computer. For example:

              \\computer2\dvd

    5.  If you must connect to the remote computer as a different user, click different user name, and enter the user name.

    6.  Click Finish.

2.  Run Oracle Universal Installer from the mapped DVD drive.

**Related Topics**

- [Installing the Oracle Database Client Software](installing-the-oracle-database-client-software.md)

**Parent topic:** [Installing from a Remote DVD Drive](installing-from-a-remote-dvd-drive.md)
