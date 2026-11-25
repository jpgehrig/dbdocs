After you provision Docker, use this example to see how you can install Oracle Grid Infrastructure and Oracle Real Application Clusters (Oracle RAC)

- Client Machine Configuration
  The client machine used for remote based graphic user interface (GUI) installation of Oracle Real Application Clusters (Oracle RAC) into Docker containers used this configuration.
- Install Oracle Grid Infrastructure and Oracle RAC
  To set up Oracle Grid Infrastructure and Oracle Real Application Clusters (Oracle RAC) in Docker containers, complete these steps.
- Run the Oracle Grid Infrastructure Installer
  To install Oracle Grid Infrastructure on Docker, complete these procedures.
- Run the Oracle RAC Database Installer
  To install Oracle Real Application Clusters (Oracle RAC), run the Oracle RAC installer.
- Create the Oracle RAC Database with DBCA
  To create the Oracle Real Application Clusters (Oracle RAC) database on the container, complete these steps with Database Configuration Assistant (DBCA).

### Client Machine Configuration

The client machine used for remote based graphic user interface (GUI) installation of Oracle Real Application Clusters (Oracle RAC) into Docker containers used this configuration.

- Client: `user-client-1`
- CPU cores: 1 socket with 1 core, with 2 threads for each core. Intel<sup>®</sup> Xeon<sup>®</sup> Platinum 8167 M CPU at 2.00 GHz
- Memory
  - RAM: 8 GB
  - Swap memory: 8 GB
- Network card and IP: `ens3`, `10.0.20.57/24`
- Linux operating system: Oracle Linux 7.9 (Linux-x86-64) with the Unbreakable Enterprise Kernel 5: 4.14.35-2047.501.2el7uek.x86_64
- Packages:
  - X Window System
  - Gnome

**Parent topic:** Example of Installing Oracle Grid Infrastructure and Oracle RAC on Docker

### Install Oracle Grid Infrastructure and Oracle RAC

To set up Oracle Grid Infrastructure and Oracle Real Application Clusters (Oracle RAC) in Docker containers, complete these steps.

- Set Up the Docker Containers for Oracle Grid Infrastructure Installation
  To prepare for Oracle Real Application Clusters (Oracle RAC), complete these steps on the Docker containers.
- Configure Remote Display for Installation
  To use a remote display for Oracle Grid Infrastructure and Oracle Real Application Clusters (Oracle RAC) for installation, you must perform these configuration steps.

**Parent topic:** Example of Installing Oracle Grid Infrastructure and Oracle RAC on Docker

#### Set Up the Docker Containers for Oracle Grid Infrastructure Installation

To prepare for Oracle Real Application Clusters (Oracle RAC), complete these steps on the Docker containers.

- Create Paths and Change Permissions
  To create directory paths and change the permissions as needed for the cluster, complete this set of commands on the docker host.
- Configure SSH for the Cluster
  You must configure SSH for both the Oracle Real Application Clusters (Oracle RAC) software owner (`oracle`) and the Oracle Grid Infrastructure software owner (`grid`) before starting installation.

**Parent topic:** Install Oracle Grid Infrastructure and Oracle RAC

##### Create Paths and Change Permissions

To create directory paths and change the permissions as needed for the cluster, complete this set of commands on the docker host.

As `root`, run the following commands for `racnode1`:

    # docker exec racnode1 /bin/bash -c "mkdir -p /u01/app/oraInventory"
    # docker exec racnode1 /bin/bash -c "mkdir -p /u01/app/grid"
    # docker exec racnode1 /bin/bash -c "mkdir -p /u01/app/19c/grid"
    # docker exec racnode1 /bin/bash -c "chown -R grid:oinstall /u01/app/grid"
    # docker exec racnode1 /bin/bash -c "chown -R grid:oinstall /u01/app/19c/grid"
    # docker exec racnode1 /bin/bash -c "chown -R grid:oinstall /u01/app/oraInventory"
    # docker exec racnode1 /bin/bash -c "mkdir -p /u01/app/oracle"
    # docker exec racnode1 /bin/bash -c "mkdir -p /u01/app/oracle/product/19c/dbhome_1"
    # docker exec racnode1 /bin/bash -c "chown -R oracle:oinstall /u01/app/oracle"
    # docker exec racnode1 /bin/bash -c "chown -R oracle:oinstall /u01/app/oracle/product/19c/dbhome_1"

Next, repeat the commands for `racnode2`:

    # docker exec racnode2 /bin/bash -c "mkdir -p /u01/app/oraInventory"
    # docker exec racnode2 /bin/bash -c "mkdir -p /u01/app/grid"
    # docker exec racnode2 /bin/bash -c "mkdir -p /u01/app/19c/grid"
    # docker exec racnode2 /bin/bash -c "chown -R grid:oinstall /u01/app/grid"
    # docker exec racnode2 /bin/bash -c "chown -R grid:oinstall /u01/app/19c/grid"
    # docker exec racnode2 /bin/bash -c "chown -R grid:oinstall /u01/app/oraInventory"
    # docker exec racnode2 /bin/bash -c "mkdir -p /u01/app/oracle"
    # docker exec racnode2 /bin/bash -c "mkdir -p /u01/app/oracle/product/19c/dbhome_1"
    # docker exec racnode2 /bin/bash -c "chown -R oracle:oinstall /u01/app/oracle"
    # docker exec racnode2 /bin/bash -c "chown -R oracle:oinstall /u01/app/oracle/product/19c/dbhome_1"

**Parent topic:** Set Up the Docker Containers for Oracle Grid Infrastructure Installation

##### Configure SSH for the Cluster

You must configure SSH for both the Oracle Real Application Clusters (Oracle RAC) software owner (`oracle`) and the Oracle Grid Infrastructure software owner (`grid`) before starting installation.

Configure SSH separately for `grid` and `oracle`:

Log in to Oracle RAC containers from your Docker host, and reset the passwords for the `grid` and `oracle` users:

    # docker exec -i -t racnode1 /bin/bash
    # passwd grid
    # passwd oracle
    # docker exec -i -t racnode2 /bin/bash
    # passwd grid
    # passwd oracle

For information about configuring SSH on cluster nodes, refer to Oracle Grid Infrastructure Installation and Upgrade Guide for Linux to see how to set up user equivalency for the `grid` and `oracle` users inside the containers.

**Parent topic:** Set Up the Docker Containers for Oracle Grid Infrastructure Installation

#### Configure Remote Display for Installation

To use a remote display for Oracle Grid Infrastructure and Oracle Real Application Clusters (Oracle RAC) for installation, you must perform these configuration steps.

If you are using Docker bridge, then you can reach Oracle RAC Containers from the Docker host by using IP addresses. However, if you are using a MACVLAN Docker network bridge, then you can use any other client machine using the same subnet to connect to container.

- Modify sshd_config
  To run the installation of Oracle Real Application Clusters (Oracle RAC) on Docker, you must modify the configuration file, `sshd_config` so that X11 forwarding is enabled.
- Enable Remote Display
  To ensure that your client can display the installation windows, you must enable remote display control of your Oracle Real Application Clusters (Oracle RAC) on Docker environment.

**Parent topic:** Install Oracle Grid Infrastructure and Oracle RAC

##### Modify sshd_config

To run the installation of Oracle Real Application Clusters (Oracle RAC) on Docker, you must modify the configuration file, `sshd_config` so that X11 forwarding is enabled.

Run the following on `racnode1` only.

Open the `sshd` configuration file `/etc/ssh/sshd_config` using the VIM editor, and set the following parameters:

    X11Forwarding yes
    X11UseLocalhost no
    X11DisplayOffset 10

Save the `sshd_config` file with these changes.

Restart `sshd`:

    # systemctl daemon-reload
    # systemctl restart sshd

You do not need to repeat these steps on `racnode2`, because Oracle RAC installations are run from a single node.

**Parent topic:** Configure Remote Display for Installation

##### Enable Remote Display

To ensure that your client can display the installation windows, you must enable remote display control of your Oracle Real Application Clusters (Oracle RAC) on Docker environment.

In this example, we enable remote display from the client to the Docker Host, and log in as the Grid user.

1.  From the client machine, start `xhost` (in our case `user-client-1`):

        # hostname
        # xhost + 10.0.20.150

    **Note:**

    `10.0.20.150` is the IP address of the first Oracle RAC container (`racnode1`). This IP address is reachable from our client machine.

2.  From the client, use SSH to log in to the Oracle RAC Container (`racnode1`) as the `grid` user:

        # ssh -X grid@10.0.20.150

3.  When prompted for a password, provide the `grid` user password, and then export the display inside the `racnode1` container to the client, where `display_computer` is the client system, and `port` is the port for the display:

        $ export DISPLAY=display_computer:port

    **Note:**

    You can only use the private IP address of the client as the export target for `DISPLAY`.

**Parent topic:** Configure Remote Display for Installation

### Run the Oracle Grid Infrastructure Installer

To install Oracle Grid Infrastructure on Docker, complete these procedures.

- Extract the Oracle Grid Infrastructure Files
  From your client connection to the Docker container as the `grid` user, extract the Oracle Grid Infrastructure image files into the Grid home on one of the Oracle RAC Containers.
- Start the Oracle Grid Infrastructure Installer
  Use this procedure to start up the Oracle Grid Infrastructure installer, and provide information for the configuration.

**Parent topic:** Example of Installing Oracle Grid Infrastructure and Oracle RAC on Docker

#### Extract the Oracle Grid Infrastructure Files

From your client connection to the Docker container as the `grid` user, extract the Oracle Grid Infrastructure image files into the Grid home on one of the Oracle RAC Containers.

Also download and extract the most recent Release Update (RU), October 2021 or later. For example: Grid Infrastructure Release Update 19.16 (Patch 34130714).

For example:

1.  Ensure that the Grid user has read-write-execute privileges in the software stage home in the Oracle RAC node 1 container (in this example, `/software/stage`).

2.  Confirm that you have downloaded and staged the required files for Oracle Grid Infrastructure and Oracle Database Release 19c (19.3), as well as the patch files. You must be able to see the Oracle Grid Infrastructure and Oracle Real Application Clusters (Oracle RAC) software staged under the path `/software/stage` inside the Oracle RAC Node 1 container.

        $ ls -l /software/stage/*.zip
        -rw-r--r--. 1 root 1001 3059705302 Feb 3 09:29 /software/stage/LINUX.X64_193000_db_home.zip
        -rw-r--r--. 1 root 1001 2889184573 Feb 3 09:30 /software/stage/LINUX.X64_193000_grid_home.zip
        -rw-r--r--. 1 root root 1006462657 Jul 29 20:36 /software/stage/p32869666_1916000ACFSRU_Linux-x86-64.zip
        -rw-r--r--. 1 root root 2814622872 Jul 28 09:13 /software/stage/p34130714_190000_Linux-x86-64.zip
        -rw-r--r--. 1 root root 275787541 Jul 28 19:52 /software/stage/p34339952_1916000OCWRU_Linux-x86-64.zip
        -rw-r--r--. 1 root 1001 124109254 Jun 3 01:46 /software/stage/p6880880_190000_Linux-x86-64.zip

3.  As the grid user, unzip the files at their intended location. For example:

        $ cd /u01/app/19c/grid
        $ unzip -q /software/stage/LINUX.X64_193000_grid_home.zip
        $ cd /software/stage
        $ unzip -q p34130714_190000_Linux-x86-64.zip
        $ unzip -q p34339952_1916000OCWRU_Linux-x86-64.zip
        $ unzip -q p32869666_1916000ACFSRU_Linux-x86-64.zip

4.  As the grid user, unzip the new OPatch version in the Oracle Grid Infrastructure home to replace the existing one. For example, where `OPATCH-patch-zip-file` is the OPatch zip file:

        $ cd /u01/app/19c/grid
        $ mv OPatch OPatch_19.3
        $ unzip -q /software/stage/OPATCH-patch-zip-file

    For example, for the OPatch 12.2.0.1.32 for DB 19.0.0.0.0 (Jul 2022) Product Oracle Global Lifecycle Management OPatch utility:

        $ cd /u01/app/19c/grid
        $ mv OPatch OPatch_19.3
        $ unzip -q /software/stage/p6880880_190000_Linux-x86-64.zip

After you unzip the OPatch zip file, you can remove the `OPatch_19.3` directory.

**Related Topics**

- [Oracle Database 19c Release Update & Release Update Revision July 2022 Known Issues (Doc ID 19202207.9)](https://support.oracle.com/rs?type=doc&id=19202207.9)
- [How To Download And Install The Latest OPatch(6880880) Version (Doc ID 274526.1)](https://support.oracle.com/rs?type=doc&id=274526.1)

**Parent topic:** Run the Oracle Grid Infrastructure Installer

#### Start the Oracle Grid Infrastructure Installer

Use this procedure to start up the Oracle Grid Infrastructure installer, and provide information for the configuration.

**Note:**

The instructions in the "Oracle Database Patch 34130714 - GI Release Update 19.16.0.0.220719" patch notes tell you to use `opatchauto` to install the patch. However, this patch should be applied by the Oracle Grid Infrastructure installer using the `-applyRU` argument

1.  From your client connection to the Docker container as the Grid user on `racnode1`, start the installer, using the following command:

        /u01/app/19c/grid/gridSetup.sh -applyRU /software/stage/34130714 \
        -applyOneOffs /software/stage/34339952,/software/stage/32869666

2.  Choose the option Configure Grid Infrastructure for a New Cluster, and click Next.

    The Select Cluster Configuration window appears.

3.  Choose the option Configure an Oracle Standalone Cluster, and click Next.

4.  In the Cluster Name and SCAN Name fields, enter the names for your cluster, and for the cluster Single Client Access Names (SCANs) that are unique throughout your entire enterprise network. For this example, we used these names:

    - Cluster Name: `raccluster01`
    - SCAN Name: `racnode-scan`
    - SCAN Port : `1521`

5.  If you have configured your domain name server (DNS) to send to the GNS virtual IP address name resolution, then you can select Configure GNS requests for the subdomain GNS servers. Click Next.

6.  In the Public Hostname column of the table of cluster nodes, check to see that you have the following values set

    - Public Hostname:
      - `racnode1.example.info`
      - `racnode2.example.info`
    - Virtual Hostname:
      - `racnode1-vip.example.info`
      - `racnode2-vip.example.info`

7.  Click SSH connectivity, and set up SSH between `racnode1` and `racnode2`.

    When SSH is configured, click Next.

8.  On the Network Interface Usage window, select the following:

    - `eth0 10.0.20.0` for the Public network
    - `eth1 192.168.17.0` for the first Oracle ASM and Private network
    - `eth2 192.168.18.0` for the second Oracle ASM and Private network

    After you make those selections, click Next.

9.  On the Storage Option window, select Use Oracle Flex ASM for Storage and click Next.

10. On the GIMR Option window, leave the default selection (No), and click Next.

11. On the Create ASM Disk Group window, click Change Discovery Path, and set the value for Disk Discovery Path to `/dev/asm*`, and click OK. Provide the following values:

    - Disk group name: `DATA`
    - Redundancy: `External`
    - Select the default, Allocation Unit Size
    - Select Disks, and provide the following values:
      - `/dev/asm-disk1`
      - `/dev/asm-disk2`

    When you have entered these values, click. Next.

12. On the ASM Password window, provide the passwords for the `SYS` and `ASMSNMP` users, and click Next.

13. On the Failure Isolation window, Select the default, and click Next.

14. On the Management Options window, select the default, and click Next.

15. On the Operating System Group window, select the default, and click Next.

16. On the Installation Location window, for Oracle base, enter the path `/u01/app/grid`, and click Next.

17. On the Oracle Inventory window, for Inventory Directory, enter `/u01/app/oraInventory`, and click Next.

18. On the Root Script Execution Configuration window, leave Automatically run configuration scripts unchecked, and click Next.

19. On the Prerequisite Checks window, under Verification Results, you may see a `Systemd` status warning. You can ignore this warning, and proceed.

    If you encounter an unexpected warning, then refer to "Known Issues " in My Oracle Support ID 2488326.1.

20. On the Prerequisite Checks window, it is possible that you can see a warning indicating that `cvuqdisk-1.0.10-1` is missing, and see the failure message "Device Checks for ASM" failed. If this warning appears, then you must install the package `cvuqdisk-1.0.10-1` on both the containers. In this case:
    - The Fix & Check Again button is disabled, and you need to install the package manually. Complete the following steps:

      1.  Open a terminal, and log in as `root` to `racnode1 /bin/bash`.

      2.  Run the following command to install the `cvuqdisk` RPM package:

              rpm -ivh /tmp/GridSetupActions*/CVU_*/cvuqdisk-1.0.10-1.rpm

      3.  Click Check Again.

      4.  Repeat steps a and b to install the RPM on `racnode2`.

      You should not see any further warnings or failure messages. The installer should automatically proceed to the next window.

21. Click Install.

22. When prompted, run `orainstRoot.sh` and `root.sh` on `racnode1` and `racnode2`.

23. After installation is complete, confirm that the CRS stack is up:

        $ORACLE_HOME/bin/crsctl stat res -t

**Related Topics**

- [Oracle RAC on Docker - Released Versions and Known Issues (Doc ID 2488326.1)](https://support.oracle.com/rs?type=doc&id=2488326.1)

**Parent topic:** Run the Oracle Grid Infrastructure Installer

### Run the Oracle RAC Database Installer

To install Oracle Real Application Clusters (Oracle RAC), run the Oracle RAC installer.

- Extract the Oracle Real Application Clusters Files
  To prepare for installation, log in to `racnode1` as the Oracle Software Owner account (`oracle`), and extract the software.
- Run the Oracle RAC Installer
  To proceed through the Oracle Real Application Clusters (Oracle RAC) installer screen workflow, run the installer, and answer questions as prompted.

**Parent topic:** Example of Installing Oracle Grid Infrastructure and Oracle RAC on Docker

#### Extract the Oracle Real Application Clusters Files

To prepare for installation, log in to `racnode1` as the Oracle Software Owner account (`oracle`), and extract the software.

1.  From the client, use SSH to log in to the Oracle RAC Container (`racnode1`) as the `oracle` user:

        # ssh -X oracle@10.0.20.150

2.  When prompted for a password, provide the `oracle` user password, and then export the display inside the `racnode1` container to the client, where `display_computer` is the client system, and `port` is the port for the display:

        $ export DISPLAY=display_computer:port

3.  Unzip the Oracle Database files with the following commands:

        $ cd /u01/app/oracle/product/19c/dbhome_1
        $ unzip -q /software/stage/LINUX.X64_193000_db_home.zip

4.  As the Oracle user, unzip the new Opatch version in the Oracle Database (Oracle home) to replace the existing one. For example, where `OPATCH-patch-zip-file` is the Opatch zip file:

        $ cd /u01/app/oracle/product/19c/dbhome_1
        $ mv OPatch OPatch_19.3
        $ unzip -q /software/stage/OPATCH-patch-zip-file

    For example, for the OPatch 12.2.0.1.32 for DB 19.0.0.0.0 (Jul 2022) Product Oracle Global Lifecycle Management OPatch utility:

        $ cd /u01/app/oracle/product/19c/dbhome_1
        $ mv OPatch OPatch_19.3
        $ unzip -q /software/stage/p6880880_190000_Linux-x86-64.zip

    After you unzip the OPatch zip file, you can remove the `OPatch_19.3` directory.

**Parent topic:** Run the Oracle RAC Database Installer

#### Run the Oracle RAC Installer

To proceed through the Oracle Real Application Clusters (Oracle RAC) installer screen workflow, run the installer, and answer questions as prompted.

1.  Run the installer with the following command:
        $ /u01/app/oracle/product/19c/dbhome_1/runInstaller -applyRU /software/stage/34130714
2.  Select Set Up Software only, and click Next.
3.  Choose Oracle Real Application Clusters database installation, and click Next.
4.  Ensure that both the `racnode1` and `racnode2` nodes are selected, and click SSH connectivity.
5.  In SSH connectivity, provide the SSH password, and click set up. Click OK after completing the SSH setup, and then click Next.
6.  Choose Enterprise Edition,and click Next.
7.  Set the Oracle base path to `/u01/app/oracle`, and click Next.
8.  On Operating System Groups, choose the default, and click Next.
9.  On Root Script execution, choose the default, and click Next.
10. Click Install.
11. When prompted, run `root.sh` on both of the nodes.
12. After the installation completes, click Close to exit the installer.

**Parent topic:** Run the Oracle RAC Database Installer

### Create the Oracle RAC Database with DBCA

To create the Oracle Real Application Clusters (Oracle RAC) database on the container, complete these steps with Database Configuration Assistant (DBCA).

The DBCA utility is typically located in the `ORACLE_HOME/bin` directory.

1.  Change directory to `$ORACLE_HOME/bin`, and enter the command `dbca`.
2.  On the Database Operation window, select Create Database, and click Next.
3.  Select Advanced Configuration, and click Next.
4.  On the Select Database Deployment Type window, Select from the Configuration Type list the database management policy that you want to use:
    - Admin-managed (the default)

      Administrator-managed deployment is based on the Oracle RAC deployment types that existed before Oracle Database 11g release 2 (11.2) and requires that you statically configure each database instance to run on a specific node in the cluster, and that you configure database services to run on specific instances belonging to a certain database using the preferred and available designation.

    - Policy-managed

      Policy-managed deployment is based on server pools, where database services run within a server pool as singleton or uniform across all of the servers in the server pool. Databases are deployed in one or more server pools and the size of the server pools determine the number of database instances in the deployment.

    When you have made your management policy selection, click Next.
5.  Select both `racnode` and `racnode2`, and click Next.
6.  On the Database Identification window, enter values for these fields:
    - Global Database Name: Enter `orclcdb.example.info`
    - SID Prefix: Enter `orclcdb`
    - Select Use Local Undo Tablespace for PDBs
    - Select Create a Container database with one or more PDBs
    - Select Number of PDBs
    - In PDB name, enter `orclpdb`

    Click Next
7.  On the Storage Option window, select the following options:
    - Database files location: Enter +`DATA/{DB_UNIQUE_NAME}`
    - Select Use Oracle-Managed Files (OMF)

    After you make your selections, click Next.
8.  On the Fast Recovery Option window, select the following:
    - Select Fast Recovery Area, and enter `+DATA`
    - Select Enable Archiving, and select the default option

    When you have made your selections, click Next.
9.  On the Data Vault Option window, select the default, and click Next.
10. On the Configuration Option window, under the Memory tab, enter the following values:
    - SGA Size: 3G
    - PGA Size: 2G

    Select the default values for the rest of the fields on the window, and click Next.

    Container available memory is considered to be the total allocated memory to the container. However, if no memory is assigned to the container, then the host memory is considered to be the available memory. Because with `cgroups`, anyone can assign more memory than the physical memory to container, CVU honors only lower or max host memory.

    The SGA and PGA values as computed by DBCA are incorrectly based the host memory. For more information, refer to My Oracle Support Doc ID 2885873.1. Allocate SGA and PGA based on the memory that you have allocated to the container. In this case, we have given 3G to the SGA, and 2G to the PGA.

    For the SGA and PGA memory capacity values, manually enter 3GB for SGA and 2GB for PGA, and then confirm Yes to the pop-up window, and continue.
11. On the Specify Management Options window, choose the default.
12. On the Specify Database User Credentials window, provide the password
13. On the Select Database Creation Option window, choose the default, and click Next.
14. The Prerequisite Checks window displays. Confirm that the prerequisites are completed without errors. It should redirect to the Install window.
15. Click Finish to begin the installation.

After the database is created, you can either connect to the database using your application, or connect with SQL\*Plus using the SCAN `racnode-scan.example.info` on port 1521.

**Parent topic:** Example of Installing Oracle Grid Infrastructure and Oracle RAC on Docker
