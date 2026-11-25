## Creating a Fleet Patching and Provisioning Server

The Oracle FPP Server uses a repository to store metadata. This repository uses Oracle ACFS file system to store all the software homes that you want to make available to clients and `rhpclient`-less targets.

**Note:**

- The Oracle ACFS file system is created automatically during Oracle FPP Server installation, you must not create the Oracle ACFS file system manually.
- When you install Oracle Grid Infrastructure, the Oracle Fleet Patching and Provisioning (Oracle FPP) Server is configured, by default, in Oracle FPP Local Mode to support the local switch home capability. To configure the central Oracle FPP Server, you must remove the current Oracle FPP Local Mode configuration.

1.  Use the Oracle ASM configuration assistant (ASMCA) to create an Oracle ASM disk group on the Fleet Patching and Provisioning Server to store software.
        $ Grid_home/bin/asmca

    Because this disk group is used to store software, Oracle recommends a minimum of 100 GB for this disk group.

    **Note:**

    You must set Oracle ASM Dynamic Volume Manager (Oracle ADVM) compatibility settings for this disk group to `19.0`.
2.  Provide a mount path that exists on all nodes of the cluster. The Fleet Patching and Provisioning Server uses this path to mount gold images.
        $ mkdir -p storage_path
3.  Check if Grid Infrastructure Management Repository (GIMR) is configured on your cluster.
        $ srvctl status mgmtdb
        Database is enabled
        Instance -MGMTDB is running on node myhost01
4.  If GIMR is not configured on your cluster, then as the `grid` user, add a GIMR to your cluster.
    1.  For Oracle Database 19c Release Update (19.6) or earlier releases:
            $ $ORACLE_HOME/bin/mgmtca createGIMRContainer [-storageDiskGroup disk_group_name]
    2.  For Oracle Database 19c Release Update (19.7) or later releases:
            $ $ORACLE_HOME/bin/mgmtca createGIMRContainer [-storageDiskLocation disk_location]
5.  **Optional:** As the `root` user, add the Grid Naming Service Virtual IP Address (GNS VIP) without zone delegation.
        # srvctl add gns -vip myhost-gnsvip3
        # srvctl start gns
        # srvctl status gns
        GNS is running on node myhost01.
        GNS is enabled on node myhost01.
6.  **Optional:** If you do not want to use GNS, then you can use the Oracle FPP VIP address by configuring it while adding the Oracle FPP Server.
    **Note:**

    Oracle recommends that you use Oracle FPP VIP address to configure your Oracle FPP Server.
7.  Remove any existing local automaton from your cluster.
        # srvctl stop rhpserver
        # srvctl remove rhpserver
8.  Create the Fleet Patching and Provisioning Server resource.
        # Grid_home/bin/srvctl add rhpserver -storage storage_path
            -diskgroup disk_group_name -rhpsvip_address vip_name
9.  Start the Fleet Patching and Provisioning Server.
        $ Grid_home/bin/srvctl start rhpserver

After you start the Fleet Patching and Provisioning Server, use the Fleet Patching and Provisioning Control (RHPCTL) utility to further manage Fleet Patching and Provisioning.

**Related Topics**

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/diskgroup-compatibility.md)
- [RHPCTL Command Reference](fleet-patching-provisioning-commands.md)

**Parent topic:** [Configuring Oracle Fleet Patching and Provisioning Server](configuring-oracle-fpp-server.md)
