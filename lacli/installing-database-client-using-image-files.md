## Installing Oracle Database Client Using Image File

Extract the Oracle Database Client image files and use the `runInstaller` command to start the Oracle Database Client installation.

Starting with 19c, the Oracle Database Client software is also available as an image file for download and installation.

Have all the information you need to provide regarding storage paths before you start the installation. Oracle recommends that you have your My Oracle Support credentials available during installation. During installation, you are asked to run configuration scripts as the `root` user. You must run these scripts manually as `root` when prompted.

1.  Log in as the Oracle installation owner user account (`oracle`).
2.  Download the Oracle Database Client installation image files (`client_home.zip`) to a directory of your choice. For example, you can download the image files to the `/tmp` directory.
3.  Create the Oracle home directory and extract the image files that you have downloaded in to this Oracle home directory. For example:
        $ mkdir -p /u01/app/oracle/product/19.0.0/client_1
        $ chgrp oinstall /u01/app/oracle/product/19.0.0/client_1
        $ cd /u01/app/oracle/product/19.0.0/client_1
        $ unzip -q /tmp/client_home.zip

    **Note:**

    - Oracle recommends that the Oracle home directory path you create is in compliance with the Oracle Optimal Flexible Architecture recommendations. Also, unzip the installation image files only in this Oracle home directory that you created.
    - Oracle home or Oracle base cannot be `symlinks`, nor can any of their parent directories, all the way to up to the `root` directory.
4.  From the Oracle home directory, run the `runInstaller` command to start the Oracle Database Client Setup Wizard.
        $ cd /u01/app/oracle/product/19.0.0/client_1
        $ ./runInstaller

    **Note:**

    Run the `runInstaller` command from the Oracle home directory only. Do not use the `runInstaller` command that resides at `$ORACLE_HOME/oui/bin/`, or any other location, to install Oracle Database, Oracle Database Client, or Oracle Grid Infrastructure.
5.  The setup wizard starts an Administrator type installation of Oracle Database Client.
    Installation screens vary depending on the installation option you select. Respond to the configuration prompts as needed.

    **Note:**

    At any time during installation, if you have a question about what you are being asked to do, click Help.

**Parent topic:** [Installing the Oracle Database Client Software](installing-the-oracle-database-client-software.md)
