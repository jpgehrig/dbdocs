## Installing Standard Edition High Availability Database Software on Local File System

You can install Oracle Database software binaries on a local file system to enable the Oracle Database Standard Edition high availability feature.

Ensure that all the cluster nodes, on which you plan to configure Standard Edition High Availability, have the same operating system configuration, database users, database groups, resource limits, and SSH equivalence for the Oracle Database software owner user (`oracle`).

Before you start the installation, have all the information you need about users, groups, and storage paths. You should also be prepared to run root scripts or provide information to automate root scripts.

1.  As the `Administrator` user, log into the first cluster node on which you want to configure Standard Edition High Availability and create the Oracle base directory on the local file system. Follow the Oracle Optimal Flexible Architecture (OFA) recommendations and specify the correct owner, group, and permissions for this directory.
        C:\>md C:\app\oracle
        C:\>icacls oracle:oinstall C:\app\oracle
2.  Log in to the first cluster node as the Oracle Database software owner user (`oracle`).
3.  Download the Oracle Database 19c release 19.3 installation image file (`db_home.zip`) from Oracle Software Delivery Cloud website to a directory of your choice.
    <https://edelivery.oracle.com/>
4.  Download the Oracle Database Release Update 19.7 or later patch from My Oracle Support to a directory of your choice and unzip it.
    <https://support.oracle.com/>
5.  Create an OFA-compliant Oracle home directory on the local file system and extract the image files that you have downloaded in to this Oracle home directory. For example:
        C:\>md C:\app\oracle\product\19.0.0\dbhome_1
        C:\>cd C:\app\oracle\product\19.0.0\dbhome_1
        C:\app\oracle\product\19.0.0\dbhome_1> unzip \tmp\db_home.zip
6.  From the Oracle home directory, run the `setup.exe` command to start the Oracle Database Setup Wizard.
        C:\app\oracle\product\19.0.0\dbhome_1>setup.exe

    **Note:**

    Run the `setup.exe` command from the Oracle home directory only. Do not use the `setup.exe` command that resides at `%ORACLE_HOME%\oui\bin\`, or any other location, to install Oracle Database.
7.  In the Select Configuration Option screen, select Set Up Software Only.
8.  In the Select Database Installation Option screen, select Single instance database installation.
9.  In the Select Database Edition screen, select Standard Edition 2.
10. Respond to the configuration prompts as needed.
    **Note:**

    Click Help if you have any questions about the information you are asked to submit during installation.
11. Apply the Oracle Database Release Update (RU) 19.7 or later patch. Review the patch documentation for instructions on how to apply the patch.
    **Note:**

    Ensure that you apply the Oracle Clusterware (OCW) RU of the same version to the Oracle Database home.
12. **Optional:** As the `oracle` user, enable read-only Oracle home on the first cluster node.
        cd C:\app\vldb22\product\19.0.0\dbhome_1\bin
        C:\app\vldb22\product\19.0.0\dbhome_1\bin>roohctl.bat -enable

    **Note:**

    Do not use the `-disable` flag with the `roohctl` command, as it is not supported.
13. As the `Administrator` user, create the Oracle base directory on all of the other cluster nodes on which you want to configure Standard Edition High Availability.
        C:\>md C:\app\oracle
        C:\>icacls oracle:oinstall C:\app\oracle
14. As the `oracle` user, run the `addnode.bat` script from the first node to perform the following operations on the other nodes on which you want to configure Standard Edition High Availability:
    - Copy the Oracle home directory from the first node to the other nodes.
    - Setup Oracle base, Oracle inventory directories, and Oracle DB registry keys on the other nodes.

    <!-- -->

        C:\>%ORACLE_HOME%\addnode\addnode.bat -silent CLUSTER_NEW_NODES=comma_separated_list_of_other_nodes
15. If you specify a non built-in and a non Administrator's user account while installing Oracle Database, then add the respective user's password to the CRS wallet using the following command:
        crsctl add wallet -type OSUSER -user DB service user name -password

After the Oracle Database software installation is complete, use Oracle Database Configuration Assistant (Oracle DBCA), in either interactive or silent mode, to create a Standard Edition database on the first cluster node on which you installed the Oracle Database software.

For more information about the requirements for creating a database, and the procedure for enabling and configuring Standard Edition High Availability for Oracle Databases, refer to [Oracle Database Administrator’s Guide](../admin/creating-and-configuring-an-oracle-database.md)

**Related Topics**

- [Oracle Grid Infrastructure Installation and Upgrade Guide for Linux](../cwlin/installing-oracle-grid-infrastructure.md)
- [Creating a Database with Oracle DBCA](../admin/creating-and-configuring-an-oracle-database.md)

**Parent topic:** [Deploying Standard Edition High Availability](installing-seha.md)
