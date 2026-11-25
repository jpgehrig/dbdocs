## Running RPM Packages to Install Oracle Database

Perform the following steps to install and configure Oracle Database using RPM packages.

### Installing Oracle Database RPM using yum

1.  Log in as `root`.

2.  If you are using Oracle Linux and have subscribed to Unbreakable Linux Network (ULN), you can install Oracle Database via a single `yum` command.

    `# yum -y install oracle-database-ee-19c`

    This command downloads and installs the Oracle Database Preinstallation RPM and the Oracle Database RPM packages.

    The installation of Oracle Database software is now complete, continue to the "Creating and Configuring an Oracle Database" section.

### Installing Oracle Database RPM Manually

1.  Log in as `root`.

2.  Download and install the Oracle Database Preinstallation RPM:

    1.  On Oracle Linux

            # yum -y install oracle-database-preinstall-19c

    2.  On Red Hat Enterprise Linux

            # curl -o oracle-database-preinstall-19c-1.0-1.el7.x86_64.rpm https://yum.oracle.com/repo/OracleLinux/OL7/latest/x86_64/getPackage/oracle-database-preinstall-19c-1.0-1.el7.x86_64.rpm
            # yum -y localinstall oracle-database-preinstall-19c-1.0-1.el7.x86_64.rpm

        After successful installation, you can delete the downloaded RPM file:

            # rm oracle-database-preinstall-19c-1.0-1.el7.x86_64.rpm

3.  Access the software download page for Oracle Database RPM-based installation from Oracle Technology Network:

    <https://www.oracle.com/database/technologies/oracle-database-software-downloads.html>

4.  Download the `.rpm` file required for performing an RPM-based installation to a directory of your choice. For example, download the `oracle-database-ee-19c-1.0-1.x86_64.rpm` file to the `/tmp` directory.

5.  Install the database software using the `yum localinstall` command.

        # cd /tmp
        # yum -y localinstall oracle-database-ee-19c-1.0-1.x86_64.rpm

    Where, `oracle-database-ee-19c-1.0-1.x86_64.rpm` is the fully qualified name of the Oracle Database RPM.

The installation of Oracle Database software is now complete.

### Creating and Configuring an Oracle Database

To create a sample database with the default settings, perform the following steps:

1.  Log in as `root.`

2.  To configure a sample Oracle Database instance, run the following service configuration script:

        # /etc/init.d/oracledb_ORCLCDB-19c configure

    **Note:**

    You can modify the configuration parameters by editing the `/etc/sysconfig/oracledb_ORCLCDB-19c.conf` file.
    This script creates a container database (`ORCLCDB`) with one pluggable database (`ORCLPDB1`) and configures the listener at the default port (1521).

    Review the status information that is displayed on your screen.

**Related Topics**

- [Automatically Configuring Oracle Linux with Oracle Database Preinstallation RPM](automatically-configuring-oracle-linux-with-oracle-preinstallation-rpm.md)
- [Downloading Oracle Software](downloading-oracle-software.md)
- [Removing an RPM-based Oracle Database Installation](removing-rpm-based-database-installation.md)

**Parent topic:** [Installing Oracle Database Using RPM Packages](installing-oracle-database-using-rpm-packages.md)
