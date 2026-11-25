Workspace Manager is installed by default in the seed database and in all databases created by the Database Configuration Assistant (DBCA). However, in all other Oracle databases, such as those you create with a customized procedure, you must install Workspace Manager before you can use its features.

To install Workspace Manager in a custom database, do the following:

1.  At the system command prompt, change the current directory to the directory that contains Workspace Manager installation script and packages, as shown in the following example:

        cd <ORACLE_HOME>/rdbms/admin

2.  Connect as `SYS` to the Oracle instance with a command in the following format:

        sqlplus sys

    Enter the password for the `SYS` account when you are prompted.

3.  Run the `owminst.plb` script:

        SQL> @owminst.plb

4.  Verify the installation of Workspace Manager by entering the following command while connected as any valid database user, and ensure that the output is as shown here:

        SQL> select dbms_wm.getWorkspace from dual;

        GETWORKSPACE
        ----------------------------------------------------------------------------
        LIVE
