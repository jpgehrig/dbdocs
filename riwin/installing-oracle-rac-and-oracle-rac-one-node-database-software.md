## Installing Oracle RAC and Oracle RAC One Node Database Software

Install Oracle RAC or Oracle RAC One Node software.

Oracle Real Application Clusters Database installation is a two-step process. This procedure describes the first step — to install Oracle RAC software.

If you have an existing Oracle installation, then write down the version numbers, patches, and other configuration information, and review upgrade procedures for your existing installation. Review Oracle Database Upgrade Guide before proceeding with the installation.

1.  Log in as an Administrator user.
2.  Open a command prompt window to run the installer, and log in as the user account that you want to own the Oracle Database installation (for example, `oracle`).
3.  Download the Oracle Database installation image files (`db_home.zip`) and extract the files into a new Oracle home directory.
    **Note:**

    Oracle recommends that the Oracle home directory path you create is in compliance with the Oracle Optimal Flexible Architecture recommendations. Also, unzip the installation image files only in this Oracle home directory that you created.
4.  From the Oracle home directory, start the Oracle Database software installation:
        cd C:\app\oracle\product\19.0.0\dbhome_1
        setup.exe

    **Note:**

    Run the `setup.exe` command from the Oracle home directory only. Do not run `setup.exe` from any other location.
5.  In the Select Configuration Option screen, select the Setup Software Only option. Click Next.
6.  In the Select Database Installation Option screen, select the Oracle Real Application Clusters Database Installation option. Click Next.
7.  In the Node Selection screen, select all the nodes where you want to install Oracle RAC or Oracle RAC One Node software. Click Next.
8.  In the Select Database Edition screen, select the Enterprise Edition option. Click Next.
9.  In the Specify Install Location screen, provide the location of Oracle base for Oracle RAC software installation.
    The Oracle base directory must be different from the Grid home directory. Click Next.
10. The Perform Prerequisite Checks screen displays the results of the prerequisites checks. If any of the checks have a status of Failed and are not Fixable, then you must manually correct these issues. After you have fixed the issue, you can click the Check Again button to have the installer recheck the requirement and update the status. Repeat as needed until all the checks have a status of Succeeded. Click Next.
11. Review the contents of the Summary screen and then click Install.
    The installer displays a progress indicator enabling you to monitor the installation process.

After installing Oracle RAC software, run Database Configuration Assistant (DBCA) from the `ORACLE_HOME\bin\dbca` directory to create and configure Oracle RAC databases.

**Related Topics**

- [Oracle Real Application Clusters Postinstallation Procedures](oracle-real-application-clusters-postinstallation-procedures.md)
- [Creating Oracle RAC or Oracle RAC One Node Databases with DBCA](creating-oracle-rac-or-oracle-rac-one-node-databases-with-dbca.md)

**Parent topic:** [Installing Oracle RAC and Oracle RAC One Node Databases](running-oracle-universal-installer-to-install-oracle-database.md)
