## Installing Oracle RAC and Oracle RAC One Node Database Software

Install Oracle RAC or Oracle RAC One Node software.

Oracle Real Application Clusters Database installation is a two-step process. This procedure describes the first step — to install Oracle RAC software.

If you have an existing Oracle installation, then write down the version numbers, patches, and other configuration information, and review upgrade procedures for your existing installation. Review Oracle Database Upgrade Guide before proceeding with the installation.

Ensure that you have `su` or `sudo` credentials, because you will be required to either provide `root` credentials to automatically run the root scripts or run a script as the `root` user during installation.

1.  Ensure that you can access other nodes with SSH. The installer requires that the user account running the Oracle RAC installation is permitted to set up passwordless SSH. The installer can set this up for you automatically, or your system administrator can set this up for you before installation is started.
2.  Open the terminal from which you intend to run the installer, and log in as the user account that you want to own the Oracle Database installation (for example, `oracle`).
    If you are not able to turn off `stty` commands, or have other restrictions that prevent automatic SSH configuration from within the installer, then you must ensure that SSH is configured and enabled before you proceed to start installation.
3.  Download the Oracle Database installation image files (`db_home.zip`) and extract the files into a new Oracle home directory. For example:
        $ mkdir -p /u01/app/oracle/product/19.0.0/dbhome_1
        $ chgrp oinstall /u01/app/oracle/product/19.0.0/dbhome_1
        $ cd /u01/app/oracle/product/19.0.0/dbhome_1
        $ unzip -q /tmp/db_home.zip

    **Note:**

    - Oracle recommends that the Oracle home directory path you create is in compliance with the Oracle Optimal Flexible Architecture recommendations. Also, unzip the installation image files only in this Oracle home directory that you created.

    - Oracle home or Oracle base cannot be `symlinks`, nor can any of their parent directories, all the way to up to the `root` directory.
4.  From the Oracle home directory, start the Oracle Database software installation:
        $ cd /u01/app/oracle/product/19.0.0/dbhome_1
        $ ./runInstaller

    **Note:**

    Run the `runInstaller` command from the Oracle home directory only. Do not run `runInstaller` command that resides at `$ORACLE_HOME/oui/bin/`, or any other location, to install Oracle Real Application Clusters or Oracle Grid Infrastructure.
5.  In the Select Configuration Option screen, select the Setup Software Only option. Click Next.
6.  In the Select Database Installation Option screen, select the Oracle Real Application Clusters Database Installation option. Click Next.
7.  In the Node Selection screen, select all the nodes where you want to install Oracle RAC or Oracle RAC One Node software. Click Next.
8.  In the Select Database Edition screen, select the Enterprise Edition option. Click Next.
9.  In the Specify Install Location screen, provide the location of Oracle base for Oracle RAC software installation.
    The Oracle base directory must be different from the Grid home directory. Click Next.
10. In the Privileged Operating System Groups screen, accept the default operating system group names for Oracle Database administration and click Next.
11. Select the option to Automatically run configuration scripts. Enter the credentials for the `root` user or a `sudo` account, then click Next.
    Alternatively, you can run the scripts manually as the `root` user at the end of the installation process when prompted by the installer.
12. The Perform Prerequisite Checks screen displays the results of the prerequisites checks. If any of the checks have a status of Failed and are not Fixable, then you must manually correct these issues. After you have fixed the issue, you can click the Check Again button to have the installer recheck the requirement and update the status. Repeat as needed until all the checks have a status of Succeeded. Click Next.
13. Review the contents of the Summary screen and then click Install.
    The installer displays a progress indicator enabling you to monitor the installation process.
14. If you did not configure automation of the root scripts, then you are required to run `root.sh` script as the `root` user, as specified in the Execute Configuration Scripts window. Do not click OK until you have run the `root.sh` script on all nodes as directed.
    You can run the `root.sh` script simultaneously on all nodes in the cluster for Oracle RAC installations or upgrades.

After installing Oracle RAC software, run Database Configuration Assistant (DBCA) from the `ORACLE_HOME/bin/dbca` directory to create and configure Oracle RAC databases.

**Related Topics**

- [About Deploying Oracle Databases Using Oracle Fleet Patching and Provisioning](about-deploying-oracle-databases-using-fleet-patching-and-provisioning.md)
- [Oracle Real Application Clusters Postinstallation Procedures](oracle-real-application-clusters-postinstallation-procedures.md)
- [Creating Oracle RAC or Oracle RAC One Node Databases with Oracle DBCA](selecting-dbca-options-to-create-oracle-rac-or-oracle-rac-one-node-databases-with-dbca.md)

**Parent topic:** [Installing Oracle RAC and Oracle RAC One Node Databases](running-oracle-universal-installer-to-install-oracle-database.md)
