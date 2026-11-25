## Installing Oracle Oracle Database Preinstallation RPM Using the Oracle Linux yum Server

Install Oracle Linux and configure your Oracle Linux installation for security errata or bug fix updates using the Oracle Linux yum server.

1.  Refer to the official Oracle Linux documentation to install Oracle Linux:
    - Oracle Linux 7

      [Oracle Linux 7 Installation Guide](https://docs.oracle.com/en/operating-systems/oracle-linux/7/install/)

      [Oracle Linux 7: Managing Software](https://docs.oracle.com/en/operating-systems/oracle-linux/7/yum/)

    - Oracle Linux 8 and Oracle Linux 9

      [Oracle Linux 8 Installation Guide](https://docs.oracle.com/en/operating-systems/oracle-linux/8/install/)

      [Oracle Linux 9 Installation Guide](https://docs.oracle.com/en/operating-systems/oracle-linux/9/install/)

      [Managing Software in Oracle Linux](https://docs.oracle.com/en/operating-systems/oracle-linux/software-management/)
2.  After you have completed your Oracle Linux installation, run the command `yum update` as needed to obtain the most current security errata and bug fixes for your Oracle Linux installation.
3.  Restart your system.
4.  Start a terminal session and enter the following command as `root`:
    - Oracle Linux 7

          # yum install oracle-database-preinstall-19c

      **Note:**

      Use the `-y` option if you want `yum` to skip the package confirmation prompt.

    - Oracle Linux 8 and Oracle Linux 9

          # dnf install oracle-database-preinstall-19c

      **Note:**

      Use the `-y` option if you want `yum` to skip the package confirmation prompt.
      You should see output indicating that you have subscribed to the Oracle Linux channel, and that packages are being installed.

      The Oracle Database Preinstallation RPM automatically creates a standard (not role-allocated) Oracle installation owner and groups and sets up other kernel configuration settings as required for Oracle installations. If you plan to use job-role separation, then create the extended set of database users and groups depending on your requirements.

**Parent topic:** [Automatically Configuring Oracle Linux with Oracle Database Preinstallation RPM](automatically-configuring-oracle-linux-with-oracle-preinstallation-rpm.md)
