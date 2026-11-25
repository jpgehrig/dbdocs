Extract the database image files and use the `runInstaller` command to start the installation.

Have all the information you need to provide regarding users groups, and storage paths before you start installation. Oracle recommends that you have your My Oracle Support credentials available during installation. You should also be prepared to run root scripts or provide information to automate root scripts.

1.  Log in as the Oracle installation owner user account (`oracle`) that you want to own the software binaries.
2.  If this is the first time you are installing Oracle software, then create the Oracle base and the Oracle inventory directories as per the Oracle Optimal Flexible Architecture (OFA) recommendations. Specify the correct owner, group, and permissions for these directories.
        # mkdir -p /u01/app/oracle
        # mkdir -p /u01/app/oraInventory
        # chown -R oracle:oinstall /u01/app/oracle
        # chown -R oracle:oinstall /u01/app/oraInventory
        # chmod -R 775 /u01/app
3.  Download the Oracle Database installation image files (`db_home.zip`) to a directory of your choice. For example, you can download the image files to the `/tmp` directory.
4.  Create an OFA-compliant Oracle home directory and extract the image files that you have downloaded in to this Oracle home directory. For example:
        $ mkdir -p /u01/app/oracle/product/19.0.0/dbhome_1
        $ cd /u01/app/oracle/product/19.0.0/dbhome_1
        $ unzip -q /tmp/db_home.zip

    **Note:**

    - Ensure that the Oracle home directory path you create is in compliance with the Oracle Optimal Flexible Architecture recommendations. Also, unzip the installation image files only in this Oracle home directory that you created.
    - Oracle home or Oracle base cannot be `symlinks`, nor can any of their parent directories, all the way to up to the `root` directory.
5.  From the Oracle home directory, run the `runInstaller` command to start the Oracle Database Setup Wizard.
        $ cd /u01/app/oracle/product/19.0.0/dbhome_1
        $ ./runInstaller

    **Note:**

    - Run the `runInstaller` command from the Oracle home directory only. Do not use the `runInstaller` command that resides at `$ORACLE_HOME/oui/bin/`, or any other location, to install Oracle Database, Oracle Database Client, or Oracle Grid Infrastructure.
    - Use the `runInstaller` command with the `-applyRU` option to install Release Updates (RUs) during an Oracle Database installation or upgrade.
6.  In the Select Configuration Option screen, select Create and configure a single instance database.
7.  Select your installation type.
    Installation screens vary depending on the installation option you select. Respond to the configuration prompts as needed.
8.  Provide information to automate root scripts, or run scripts as root when prompted by the setup wizard.
    If you configure automation for running root scripts, and a root script fails, then you can fix the problem manually, and click Retry to run the root script again.

    **Note:**

    Click Help if you have any questions about the information you are asked to submit during installation.

**Parent topic:** [Installing the Oracle Database Software](installing-the-oracle-database-software.md)
