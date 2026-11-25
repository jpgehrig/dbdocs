## Installing Standard Edition High Availability Database Software on Oracle ACFS

You can install Oracle Database software binaries on an Oracle ASM Cluster File System (Oracle ACFS) volume to enable the Oracle Database Standard Edition High Availability feature.

Ensure that all the cluster nodes, on which you plan to configure Standard Edition High Availability, have the same operating system configuration, users, groups, resource limits, and SSH equivalence for the Oracle Database software owner user (`oracle`) between the nodes.

Before you start the installation, have all the information you need about users groups, and storage paths. You should also be prepared to run root scripts or provide information to automate root scripts.

1.  As the `root` user, register Oracle ACFS as an Oracle Clusterware resource specifying the Oracle Database software owner user (`oracle`) as the mount owner.
        # Grid_home/bin/srvctl add filesystem -volume acfs_volume_name -diskgroup diskgroup_name -path mount_point -fstype ACFS -autostart ALWAYS -user oracle

    **Note:**

    Mount Oracle ACFS to a mount point where you plan to create Oracle base and Oracle home directories for this installation. For example, `/u01/app/oracle`.
2.  As the `oracle` user, mount the Oracle ACFS file system on all of the cluster nodes on which you want to configure Standard Edition High Availability.
        $ Grid_home/bin/srvctl start filesystem -volume acfs_volume_name -diskgroup diskgroup_name
3.  As the `root` user, create the Oracle base directory in an Oracle ACFS volume on the first cluster node on which you want to configure Standard Edition High Availability. Follow the Oracle Optimal Flexible Architecture (OFA) recommendations and specify the correct owner, group, and permissions for this directory.
        # mkdir -p /u01/app/oracle
        # chown oracle:oinstall /u01/app/oracle

    **Note:**

    If you have configured the Oracle ACFS file system with the `oracle` user as the mount owner and the `/u01/app/oracle` directory as the mount point, then this step is not required.
4.  Log in to the first cluster node as the Oracle Database software owner user (`oracle`).
5.  Download the Oracle Database 19c release 19.3 installation image file (`db_home.zip`) from Oracle Software Delivery Cloud website to a directory of your choice.
    <https://edelivery.oracle.com/>
6.  Download the Oracle Database Release Update 19.7 or later patch from My Oracle Support to a directory of your choice and unzip it.
    <https://support.oracle.com/>
7.  Create an OFA-compliant Oracle home directory in an Oracle ACFS volume and extract the image files that you have downloaded in to this Oracle home directory. For example:
        $ mkdir -p /u01/app/oracle/product/19.0.0/dbhome_1
        $ cd /u01/app/oracle/product/19.0.0/dbhome_1
        $ unzip -q /tmp/db_home.zip
8.  From the Oracle home directory, run the `runInstaller` command with the `-applyRU` flag to start the Oracle Database Setup Wizard and apply the Oracle Database Release Update 19.7 or later patch during installation.
        $ ./runInstaller -applyRU patch_directory_location/patch_ID

    **Note:**

    Run the `runInstaller` command from the Oracle home directory only. Do not use the `runInstaller` command that resides at `$ORACLE_HOME/oui/bin/`, or any other location, to install Oracle Database.
9.  In the Select Configuration Option screen, select Set Up Software Only.
10. In the Select Database Installation Option screen, select Single instance database installation.
11. In the Select Database Edition screen, select Standard Edition 2.
12. Respond to the configuration prompts as needed.
13. Provide information to automate root scripts, or run scripts as root when prompted by the setup wizard.
    If you configure automation for running root scripts, and a root script fails, then you can fix the problem manually, and click Retry to run the root script again.

    **Note:**

    Click Help if you have any questions about the information you are asked to submit during installation.
14. **Optional:** As the `oracle` user, enable read-only Oracle home on the first cluster node.
        $ $ORACLE_HOME/bin/roohctl -enable
15. Attach the Oracle home on the first node to the other cluster nodes on which you want to configure Standard Edition High Availability.
        $ $ORACLE_HOME/addnode/addnode.sh -silent CLUSTER_NEW_NODES=comma_separated_list_of_other_nodes
16. As the `root` user, run the `root.sh` script on all the other cluster nodes on which you are configuring Standard Edition High Availability.
        # /u01/app/oracle/product/19.0.0/dbhome_1/root.sh

After the Oracle Database software installation is complete, use Oracle Database Configuration Assistant (Oracle DBCA), in either interactive or silent mode, to create a Standard Edition database on the first cluster node on which you installed the Oracle Database software.

For more information about the requirements for creating a database, and the procedure for enabling and configuring Standard Edition High Availability for Oracle Databases, refer to [Oracle Database Administrator’s Guide](../admin/creating-and-configuring-an-oracle-database.md).

**Related Topics**

- [Oracle Grid Infrastructure Installation and Upgrade Guide for Linux](../cwlin/installing-oracle-grid-infrastructure.md)
- [Configuring Oracle Automatic Storage Management Cluster File System](../cwlin/configuring-oracle-automatic-storage-management-cluster-file-system.md)
- [Creating a Database with Oracle DBCA](../admin/creating-and-configuring-an-oracle-database.md)

**Parent topic:** [Deploying Standard Edition High Availability](installing-seha.md)
