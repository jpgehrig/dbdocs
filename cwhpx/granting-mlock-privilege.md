Grant the MLOCK privilege to `dba` to avoid Oracle Database installation errors.

The asynchronous Input-Output pseudo-driver on HP-UX enables Oracle Database to perform Input-Output to raw disk partitions using an asynchronous method, resulting in less Input-Output overhead and higher throughput. To permit Oracle Database to process asynchronous Input-Output operations, assign the MLOCK privilege to the OSDBA group (`dba`) before you start the Oracle Database installation.

To assign the MLOCK privilege:

1.  Log in as the `root` user.
2.  Using any text editor, open the `/etc/privgroup` file, or create it, if necessary.
3.  Add or edit the following line, which begins with the name of the OSDBA group, specifying the privilege MLOCK:
        dba RTPRIO RTSCHED MLOCK

    **Note:**

    You must use only one line to specify the privileges for a particular group in this file. If the file already contains a line for the `dba` group, then add the MLOCK privilege in the same line.
4.  Save the file and quit the text editor.
5.  Enter the following command to grant the privileges to the OSDBA group:
        # /usr/sbin/setprivgrp -f /etc/privgroup
6.  Enter the following command to verify if the privileges are set correctly:
        # /usr/bin/getprivgrp dba

**Parent topic:** [Configuring Users, Groups and Environments for Oracle Grid Infrastructure and Oracle Database](configuring-users-groups-and-environments-for-oracle-grid-infrastructure-and-oracle-database.md)
