The following topics describe the installation of Oracle Database Gateways on Microsoft Windows (64-bit), as well as issues that you should consider before installing the software.

- Gateway Installation Configurations

- Gateway Installation Methods

- Installation Considerations

- Oracle Database Gateway Upgrades

- Accessing the Installation Software

- Running the Oracle Universal Installer

- Installing and Configuring in Cluster Environments

### Gateway Installation Configurations

You can install Oracle Database Gateway in either of the following configurations:

1.  On the same computer as an existing Oracle database but in a different Oracle home.

2.  On a system with no Oracle database.

3.  On the same computer as the Oracle database and in the same Oracle home directory. Note that in this case, the Oracle database and the gateway must be at the same release level.

### Gateway Installation Methods

Following are the installation methods to install Oracle Database Gateways:

- Interactive Installation Method

- Automated Installation Method Using Response Files

#### Interactive Installation Method

When you use the interactive method to install Oracle Database Gateway, Oracle Universal Installer displays a series of screens that enable you to specify all of the required information.

#### Automated Installation Method Using Response Files

By creating a response file and specifying this file when you start Oracle Universal Installer, you can automate some or all of the Oracle Database Gateway installation.

For more information about these modes and about how to complete an installation using response files, refer to [Using Response Files for Noninteractive Installation](gateway-response-files.md).

### Installation Considerations

This section contains information that you should consider before installing this product. They are:

- Release Notes

- Hardware and Software Certification

- Multiple Oracle Homes Support

- Using Windows User Account as Oracle Home User

#### Release Notes

Read the release notes for the product before installing it. The release notes are available on the Oracle Database 12c Release 2 (12.2) installation media. The latest version of the release notes is also available on the Oracle Technology Network (OTN) Web site:

    http://docs.oracle.com/

#### Hardware and Software Certification

The platform-specific hardware and software requirements included in this installation guide were current at the time this guide was published. However, because new platforms and operating system software versions might be certified after this guide is published, review the certification matrix on the My Oracle Support Web site for the most up-to-date list of certified hardware platforms and operating system versions. The My Oracle Support Web site is available at the following Web site:

[`https://support.oracle.com`](https://support.oracle.com)

#### Multiple Oracle Homes Support

This product supports multiple Oracle homes. This means that you can install this release or previous releases of the software more than once on the same system, in different Oracle home directories.

##### Installing the Software on a System with an Existing Oracle Installation

You must install this product in a new Oracle home directory. You cannot install products from one release of Oracle Database Gateways into an Oracle home directory of a different release. For example, you cannot install 12c Release 1 (12.1) software into an existing Oracle 10gR2 Oracle home directory. If you attempt to install this release in an Oracle home directory that contains software from an earlier Oracle release, then the installation will fail.

You can install this release more than once on the same system if each installation is installed in a separate Oracle home directory.

#### Using Windows User Account as Oracle Home User

With Windows, you log in to a user with Administrator privileges to install the Oracle Database software. You can also specify an Oracle Home User (based on a low-privileged, non-administrative user account) during installation.

The following are the Windows User Accounts:

- Windows Local User account

- Windows Domain User account

- Windows Managed Services Account (MSA)

- Windows Built-in Account

**See Also:**

"Using Oracle Home User on Windows" in [Oracle Database Platform Guide for Microsoft Windows](../ntqrf/managing-oracle-home-user.md)

#### Support for Windows Group Managed Service Accounts and Virtual Accounts

Starting with Oracle Database 12c Release 2 (12.2), the Group Managed Services Account (gMSA) and Virtual Accounts allow you to install an Oracle Database, and create and manage Database services without passwords. User names do not appear on the logon screen. The gMSA is a domain level account that can be used by multiple servers in a domain to run the services using this account.

Virtual Accounts are auto-managed.

See also: [Oracle® Database Platform Guide for Microsoft Windows](../ntqrf/using-oracle-home-user-for-oracle-single-instance-database-and-oracle-database-client.md) for more information

### Oracle Database Gateway Upgrades

Upgrades are not supported for Oracle Database Gateways.

### Accessing the Installation Software

You can access the Oracle Database Gateway software by using one of the following methods:

- Downloading Oracle Software from the OTN Web Site

- Copying the Oracle Software

#### Downloading Oracle Software from the OTN Web Site

You can download the installation files from the OTN and extract them to a local directory on your system.

To download the installation files:

1.  Use any browser to access the OTN software download page:
        http://www.oracle.com/technetwork/indexes/downloads/index.html
2.  Navigate to each of the download pages for the product that you want to install.
3.  On each download page, identify the required disk space by adding the file sizes for each required file. The file sizes are listed next to the file names.
4.  Select a file system with enough free space to store and expand the files. In most cases, the available disk space must be at least twice the size of each compressed file.
5.  On the file system that you just selected, create a parent directory for each product that you plan to install, for example `Dg_1`, to hold the installation directories.
6.  Download all the installation files to the directories that you just created.
7.  Verify that the files that you downloaded are the same size as the corresponding files on OTN.
8.  Extract the files in each directory that you just created.
9.  After you have extracted the required installation files, go to the Running the Oracle Universal Installer section.

#### Copying the Oracle Software

Before installing Oracle Database Gateway, you might want to copy the software to a local directory. This enables the installation process to run faster.

To copy the contents of the installation media to a local directory:

1.  Create a directory on your hard drive. For example:
        d:\install\Disk1
2.  Copy the contents of the installation media to the directory that you just created.
3.  After you have copied all the required installation files, go to the Running the Oracle Universal Installer section.

### Running the Oracle Universal Installer

In most cases, you use the graphical user interface (GUI) provided by Oracle Universal Installer to install the gateway. However, you can also use Oracle Universal Installer to complete noninteractive installations, without using the GUI.

**See Also:**

Refer to [Using Response Files for Noninteractive Installation](gateway-response-files.md) for information about noninteractive installations and other advanced installation topics

Start the Installer and install the software, as follows:

1.  If you are installing from a local directory, then double-click `setup.exe` located in the directory you created for the downloaded or copied installation files.

2.  When installing from the installation media, the Autorun screen automatically appears. If the Autorun screen does not appear, then:

    1.  From the Start menu, select Run.

    2.  Enter the following:

            DRIVE_LETTER:\autorun\autorun.exe

        In the Autorun screen, select Install/Deinstall Products.

3.  Use the following guidelines to complete the installation:

    - Follow the instruction displayed in the Installer window. If you need additional information, click Help.

    - If you encounter errors while installing or linking the software, then see [Oracle Database Gateway Troubleshooting](troubleshooting-gateway.md) for information about troubleshooting.

4.  When the installation is complete, click Exit, then click Yes to exit from the Installer.

### Installing and Configuring in Cluster Environments

Oracle Database Gateway can be installed in the existing Oracle Database home or in a separate gateway home, on all nodes. Oracle OUI can install Oracle Database Gateway on either all nodes or selective nodes.

Oracle recommends not to use the listener from the Oracle Database Gateway home. Instead configure the listener in Grid home. By default a local listener is created during cluster configuration that runs out of the grid infrastructure home and listens on the specified port (default is 1521) of the node Virtual IP(VIP).

#### Support for Single Client Access Name (SCAN)

Oracle Database 11g Release 2 and higher clients connect to the database using Support for Single Client Access Name (SCAN). It provides a single name to the clients connecting to Oracle RAC that does not change throughout the life of the cluster, even if you add or remove nodes from the cluster. Clients connecting with SCAN can use a simple connection string, such as a thin JDBC URL or EZConnect, and achieve load balancing and client connection failover.

In addition to the three SCAN listeners (one per virtual IP address), there is a node listener on every node hosting a database instance. The purpose of using two layers of listeners (SCAN listeners and node listeners) is to separate the two functions of listeners in an Oracle RAC, firstly to load balance connections and secondly to spawn-and-bequeath sessions. The SCAN listeners will receive connection requests from clients, randomly distributed by the GNS (Grid Naming Services). The SCAN listener will then use load balancing metrics to redirect the request intelligently to the node listener on the node best able to offer the requested service. Database instances register with the SCAN listeners as remote listeners, and with the node listeners as local listeners.

Oracle Database Gateway can not be configured with SCAN, a single name for Database to connect to the gateway. There are two reasons for this. Gateway does not work with remote listeners. Unlike Database where you can specify `REMOTE_LISTENER` to set to the SCAN listener, there is no support for it in Oracle Database Gateways. This is essential for SCAN listener to route the connection to the node listener. Secondly, the gateway does not register with the cluster for it to be managed as a cluster resource.

For gateway, SCAN is not very useful when the Oracle Database and Oracle Database Gateway are running on the same cluster. Oracle Database Gateway can be installed and configured on each node where database is installed, and database can be configured such that each instance connect to the Gateway running on the same node.

#### Local Listener

Oracle Database Gateway service should be configured using the local listener. It is the local listener that spawns the gateway process. That means listener should know which gateway process to spawn. Use the `listener.ora` in Grid infrastructure home to add the Gateway SID. If a SCAN listener for Database is already running on that node, you can use the same listener.ora file to configure the local listener.

#### Load Balancing and Transparent Application Failover(TAF)

Oracle Database Gateway itself does not support either the client-side (using tnsnames in database home) or server-side (using SCAN) load balancing. Load balancing at the Gateway level is not applicable because the Gateway process is currently dedicated to a single session. However, by associating a different Oracle Database Gateway instance for each database instance, you can achieve node level load balancing, that is, selecting a least loaded node happens through load balancing on the database.

Oracle Database Gateway supports connection failover feature. If you configure client-side connection load balancing for Gateway, it works similar to failover.

Whenever database fail over happens, that is, session migrates from one database instance to other database instance (on a new node), the migrated session will use the gateway instance from that new node.

Three types of Oracle Net failover functionality are available by default to Oracle Call Interface (OCI) applications:

- session: Set to failover the session. If a user connection is lost, then a new session is automatically created for the user on the backup. This type of failover does not attempt to recover select operations.

- select: Set to enable users with open cursors to continue fetching on them after failure. However, this mode involves overhead on the client side in normal select operations.

- none: This is the default. No failover functionality is used. This can also be explicitly specified to prevent failover from happening.

For failover to work, `tnsnames.ora` in Database home need to be configured with multiple listener addresses.

If the instance fails after the connection, then the TAF application fails over to the other node's listener, reserving any `SELECT` statements in progress.

In the following example of `tnsnames.ora `for load balancing that only works as failover, the database connects to the gateway on host `gateway2-server` only if the gateway on `gateway1-server` is not available:

    dg4sybs.us.example.com=
     (DESCRIPTION=
      (LOAD_BALANCE=on)
      (FAILOVER=on)
      (ADDRESS=
           (PROTOCOL=tcp)
           (HOST=gateway1-server)
           (PORT=1521))
      (ADDRESS=
           (PROTOCOL=tcp)
           (HOST=gateway2-server)
           (PORT=1521))
      (CONNECT_DATA=
         (SERVICE_NAME=dg4sybs.us.example.com) (HS=OK)
         (FAILOVER_MODE=
           (TYPE=select)
           (METHOD=basic))))
