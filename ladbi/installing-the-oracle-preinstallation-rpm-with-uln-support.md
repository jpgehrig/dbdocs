## Installing the Oracle Database Preinstallation RPM Using ULN

Use this procedure to subscribe to Unbreakable Linux Network (ULN) Oracle Linux channels for your Oracle software.

To obtain Unbreakable Linux Network (ULN) support, subscribe to Oracle Linux channels, and to add the Oracle Linux channel that distributes the Oracle Database Preinstallation RPM:

1.  Download the Oracle Linux ISO from one of the following websites:
    - Oracle yum

          https://yum.oracle.com/oracle-linux-isos.html

    - Oracle Software Delivery Cloud website:

          https://edelivery.oracle.com/linux

    **Note:**

    Ensure that you use the latest available update release for Oracle Linux.
2.  Register your server with Unbreakable Linux Network (ULN). By default, you are registered for the Oracle Linux Latest channel for your operating system and hardware.
    - Oracle Linux 7

      <https://docs.oracle.com/en/operating-systems/oracle-linux/uln-user/>

    - Oracle Linux 8 and Oracle Linux 9

      <https://docs.oracle.com/en/operating-systems/oracle-linux/software-management/>
3.  Log in to Unbreakable Linux Network:
        https://linux.oracle.com
4.  Start a terminal session and enter the following command as `root`, depending on your platform. For example:
    - Oracle Linux 7

          # yum install oracle-database-preinstall-19c

      **Note:**

      Use the `-y` option if you want `yum` to skip the package confirmation prompt.

    - Oracle Linux 8 and Oracle Linux 9

          # dnf install oracle-database-preinstall-19c

    You should see output indicating that you have subscribed to the Oracle Linux channel, and that packages are being installed.

    The Oracle Database Preinstallation RPM automatically creates a standard (not role-allocated) Oracle installation owner and groups, and sets up other kernel configuration settings as required for Oracle installations.
5.  Check the RPM log file to review the system configuration changes. For example:
        /var/log/oracle-database-preinstall-19c/backup/timestamp/orakernel.log
6.  Repeat steps 1 through 4 on all other servers in your cluster.

If you have a premier support subscription, you can enable Ksplice to provide zero downtime patching. Refer to the Ksplice User's Guide for installation instructions:

<https://docs.oracle.com/en/operating-systems/oracle-linux/ksplice-user/>

**Parent topic:** [Automatically Configuring Oracle Linux with Oracle Database Preinstallation RPM](automatically-configuring-oracle-linux-with-oracle-preinstallation-rpm.md)
