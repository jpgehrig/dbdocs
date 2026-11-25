You should consider the following issues before installing Oracle Database Gateway:

- Gateway Installation Configurations

- Gateway Installation Methods

- Installation Considerations

- Oracle Database Gateway Upgrades

- Accessing the Installation Software

- Running the Oracle Universal Installer

- Installing and Configuring in Cluster Environments

### 1.1 Gateway Installation Configurations

You can install Oracle Database Gateway in any of the following configurations:

- On the same computer as an existing Oracle database but in a different Oracle home.

- On a system with no Oracle database.

- On the same computer as the Oracle database and in the same Oracle home directory. Note that in this case, the Oracle database and the gateway must be at the same release level.

### 1.2 Gateway Installation Methods

Following are the installation methods to install Oracle Database Gateway:

- Interactive Installation Method

- Automated Installation Method Using Response Files

#### 1.2.1 Interactive Installation Method

When you use the interactive method to install Oracle Database Gateway, Oracle Universal Installer displays a series of screens that enable you to specify all of the required information.

#### 1.2.2 Automated Installation Method Using Response Files

By creating a response file and specifying this file when you start Oracle Universal Installer, you can automate some or all of the Oracle Database Gateway installation. These automated installation methods are useful if you need to perform multiple installations on similarly configured systems or if the system where you want to install the software does not have X Window system software installed.

When you use a response file, you can run Oracle Universal Installer in the following modes, depending on whether you specify all of the required information or not:

- Silent Mode

  Oracle Universal Installer runs in silent mode if you use a response file that specifies all required information. None of the Oracle Universal Installer screens are displayed.

- Suppressed Mode

  Oracle Universal Installer runs in suppressed mode if you do not specify all required information in the response file. Oracle Universal Installer displays only the screens that prompt for the information that you did not specify.

For more information about these modes and about how to complete an installation using response files, refer to [Using Response Files for Noninteractive Installation](using-response-files-for-noninteractive-installation.md).

### 1.3 Installation Considerations

Refer to the following topics for information that you should consider before installing this product. They are:

- Release Notes

- Hardware and Software Certification

- Multiple Oracle Homes Support

#### 1.3.1 Release Notes

Read the release notes for the product before installing it. The release notes are available on the Oracle Database 12c Release 2 (12.2) installation media. The latest version of the release notes is also available on the Oracle Technology Network (OTN) Web site:

[`http://docs.oracle.com`](http://docs.oracle.com)

#### 1.3.2 Hardware and Software Certification

The platform-specific hardware and software requirements included in this installation guide were current at the time this guide was published. However, because new platforms and operating system software versions might be certified after this guide is published, review the certification matrix on the My Oracle Support Web site for the most up-to-date list of certified hardware platforms and operating system versions. The My Oracle Support Web site is available at the following Web site:

[`https://support.oracle.com/`](https://support.oracle.com/)

#### 1.3.3 Multiple Oracle Homes Support

This product supports multiple Oracle homes. This means that you can install this release or previous releases of the software more than once on the same system, in different Oracle home directories.

##### 1.3.3.1 Installing the Software on a System with an Existing Oracle Installation

You must install this product in a new Oracle home directory. You cannot install products from one release of Oracle Database Gateway into an Oracle home directory of a different release. For example, you cannot install 12c Release 1 (12.1) software into an existing Oracle 11g Release 2 (11.2) Oracle home directory. If you attempt to install this release in an Oracle home directory that contains software from an earlier Oracle release, then the installation will fail.

You can install this release more than once on the same system if each installation is installed in a separate Oracle home directory.

### 1.4 Oracle Database Gateway Upgrades

Upgrades are not supported for Oracle Database Gateway.

### 1.5 Accessing the Installation Software

You can access the Oracle Database Gateway software by using one of the following methods:

- Downloading Oracle Software from the OTN Web Site.

- Copying the Oracle Software

#### 1.5.1 Downloading Oracle Software from the OTN Web Site

Perform the following steps to download the installation archive files and extract them to your system:

- Download the Installation Archive Files from OTN

- Extract the Installation Files

##### 1.5.1.1 Download the Installation Archive Files from OTN

To download the installation archive files from Oracle Technology Network do the following:

1.  Use any browser to access the software download page on Oracle Technology Network:
        http://www.oracle.com/technetwork/indexes/downloads/index.html
2.  Navigate to the download page for the product that you want to install.
3.  Select a file system with enough free space to store and expand the archive files.
    In most cases, the available drive space must be at least twice the size of the archive files.
4.  On the file system that you selected in step 3, create a directory, for example, `gateway`, to hold the installation archive files.
5.  Download the installation archive files to the directory that you created in step 4.
6.  Verify that the files you downloaded are the same size as the corresponding files on Oracle Technology Network.

##### 1.5.1.2 Extract the Installation Files

To extract the installation archive files, perform the following steps:

1.  If necessary, change directory to the directory that contains the downloaded installation archive files.
2.  If the downloaded file has the `zip` extension, use the following command to extract the content:
        unzip file_name.zip

    If the downloaded file has the `cpio.gz` extension, use the following command:

        $ gunzip filename.cpio.gz

    This command creates files with names similar to the following:

        filename.cpio
3.  To extract the installation files, enter a command similar to the following:
        $ cpio -idmv < filename.cpio

    **Note:**

    Refer to the download page for information about the correct options to use with the `cpio` command.

    Some browsers uncompress files while downloading them, but leave the` .gz` file extension. If these steps do not work, remove the `.gz` extension from the files and repeat step 3.

    For each file, this command creates a subdirectory named `gateways`.

#### 1.5.2 Copying the Oracle Software

Before installing Oracle Database Gateway, you might want to copy the software to a local directory. This enables the installation process to run faster.

To copy the contents of the installation media to a local directory:

1.  Create a directory to hold the Oracle Database Gateway software:
        $ mkdir gateway
2.  Change directory to the directory you created in step 1:
        $ cd gateway
3.  Copy the contents to the new directory as follows:
        $ cp -R /directory_path gateway

    In this example, `/``directory_path` is the installation media mount point directory. The mount point directory is `/cdrom`.

### 1.6 Running the Oracle Universal Installer

In most cases, you use the graphical user interface (GUI) provided by Oracle Universal Installer to install the gateway. However, you can also use Oracle Universal Installer to complete noninteractive installations, without using the GUI.

**See Also:**

Refer to [Using Response Files for Noninteractive Installation](using-response-files-for-noninteractive-installation.md) for information about noninteractive installations and other advanced installation topics

Start the Installer and install the software, as follows:

1.  Log in as the Oracle software owner user (`oracle`) and set the `DISPLAY` environment variable.
2.  To start the Installer, enter the following commands where `directory_path` is the directory path of the software.
        $ /directory_path/runInstaller
3.  Use the following guidelines to complete the installation:
    - Follow the instruction displayed in the Installer window. If you need additional information, click Help.

    - When the Installer prompts you to run a script with `root` privileges, enter a command similar to the following in a terminal where you are logged in as the root user, then click Continue or OK:

          # /script_path/script_name

    - If you encounter errors while installing or linking the software, then see [Oracle Database Gateway Troubleshooting](troubleshooting-gateways.md) for information about troubleshooting.
4.  When the installation is complete, click Exit and then click Yes to exit from the Installer.

### 1.7 Installing and Configuring in Cluster Environments

Oracle Database Gateway can be installed in the existing Oracle Database home or in a separate gateway home, on all nodes. Oracle OUI can install Oracle Database Gateway on either all nodes or selective nodes.

Oracle recommends not to use the listener from the Oracle Database Gateway home. Instead configure the listener in Grid home. By default a local listener is created during cluster configuration that runs out of the grid infrastructure home and listens on the specified port (default is 1521) of the node Virtual IP(VIP).

#### 1.7.1 Support for Single Client Access Name (SCAN)

Oracle Database 11g Release 2 and higher clients connect to the database using Support for Single Client Access Name (SCAN). It provides a single name to the clients connecting to Oracle RAC that does not change throughout the life of the cluster, even if you add or remove nodes from the cluster. Clients connecting with SCAN can use a simple connection string, such as a thin JDBC URL or EZConnect, and achieve load balancing and client connection failover.

In addition to the three SCAN listeners (one per virtual IP address), there is a node listener on every node hosting a database instance. The purpose of using two layers of listeners (SCAN listeners and node listeners) is to separate the two functions of listeners in an Oracle RAC, firstly to load balance connections and secondly to spawn-and-bequeath sessions. The SCAN listeners will receive connection requests from clients, randomly distributed by the GNS (Grid Naming Services). The SCAN listener will then use load balancing metrics to redirect the request intelligently to the node listener on the node best able to offer the requested service. Database instances register with the SCAN listeners as remote listeners, and with the node listeners as local listeners.

Oracle Database Gateway can not be configured with SCAN, a single name for Database to connect to the gateway. There are two reasons for this. Gateway does not work with remote listeners. Unlike Database where you can specify `REMOTE_LISTENER` to set to the SCAN listener, there is no support for it in gateways. This is essential for SCAN listener to route the connection to the node listener. Secondly, the gateway does not register with the cluster for it to be managed as a cluster resource.

For gateway, SCAN is not very useful when the Oracle Database and Oracle Database Gateway are running on the same cluster. Oracle Database Gateway can be installed and configured on each node where database is installed, and database can be configured such that each instance connect to the Gateway running on the same node.

#### 1.7.2 Local Listener

Oracle Database Gateway service should be configured using the local listener. It is the local listener that spawns the gateway process. That means listener should know which gateway process to spawn. Use the `listener.ora` in Grid infrastructure home to add the Gateway SID. If a SCAN listener for Database is already running on that node, you can use the same listener.ora file to configure the local listener.

#### 1.7.3 Load Balancing and Transparent Application Failover(TAF)

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
